# Type system discipline

Apply when designing types, reviewing a function signature, or writing code in any statically-typed language. Make illegal states unrepresentable, brand semantic primitives, parse external data at boundaries, refuse to lie to the compiler, exhaust variants, derive from authoritative schemas.

The type checker is a proof assistant. A case the types let you ignore becomes a runtime failure the compiler could have stopped. Define errors and special cases out of existence rather than adding handlers.

- **Illegal states unrepresentable.** Model variants as sum types (discriminated unions, enums with payloads, sealed classes, ADTs), not a bag of optional fields. `{ completed: boolean; completedAt?: Date }` admits `completed: true` with no date. Use `{ kind: 'open' } | { kind: 'done'; at: Date }`, or derive the boolean from one source.
- **Construct, don't restrict.** Build the type from the values you want. A non-empty list is a head plus a rest; a valid range is a start plus a duration, not two timestamps you must keep ordered.
- **Brand semantic primitives.** `UserId` and `OrderId` are both strings but must not be interchangeable. Validate once at creation; trust downstream.
- **External data is untyped until parsed:** payloads, JSON, IPC, CLI args, config, env vars, database rows. One parse function per boundary ([boundary-discipline](boundary-discipline.md)).
- **Don't lie to the compiler.** Casts, unsafe coercions, and assertion helpers that bypass checks are deferred crashes. Prove the fact (validate, narrow, refine the model) or treat the cast as a hazard.
- **Exhaustive matching.** Adding a variant must break compilation where it is unhandled. Use the language's idiom (a never-typed default, an exhaustive match, an incomplete-pattern warning as error).
- **Derive from authoritative schemas** (protobuf, OpenAPI, GraphQL, migrations, design tokens). Hand-written parallel types drift.
- **Strengthen a type only where partiality shows up.** A runtime assertion or "should never happen" throw marks a type too weak; push that check into the type, then stop. Prefer total functions. Extra precision with no safety gain costs reuse.

**Checks:**
- Can you write a comment saying when this field combination is valid? Split it into a sum type.
- Do two arguments share a primitive but mean different things? Brand them.
- Where did this cast or non-null assertion come from? Validate at the boundary instead.
- If a variant is added next month, will the compiler point to every place that needs a case?
- Does this type duplicate a shape another file owns? Derive it.
- Am I strengthening this type to keep an operation total, or only to be precise? If nothing would otherwise fail, keep it plain.
