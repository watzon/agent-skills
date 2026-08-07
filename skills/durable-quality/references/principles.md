# Principles

## Economic shift

Writing cost approaches zero under capable agents. The scarce costs remain:

- understanding requirements and edge cases
- verifying behavior (especially semantic stability of tests)
- preserving architectural integrity across many small lands
- human attention for high blast-radius paths
- long-horizon ownership

Optimize the system of work for those scarce costs.

## Five loops

1. **Intent** — what must be true (acceptance criteria, invariants, threat notes)
2. **Generation** — produce candidate code
3. **Proof** — deterministic evidence intent holds
4. **Structure** — boundaries, deps, complexity, duplication limits
5. **Ownership** — named human liable across time

Agents amplify generation. Without proof, structure, and ownership, they amplify entropy.

## Code health direction

From Google's eng-practices standard of code review:

- Prefer landing a change that **improves** overall code health even if imperfect
- Never land a change that **degrades** code health except emergencies
- Perfect is not the bar; continuous improvement is
- Small complexity additions compound into unmaintainable systems

Operationalize as: every PR should leave the system easier to change, or at least not worse.

## Craft vs tools

Martin ("Tools are not the Answer", 2017): shiny tools do not replace discipline.

Updated for agents:

- Tools and gates **encode** discipline so it survives volume
- Tools without ownership and design gates become rubber stamps
- Instruction files without CI twins are wishes

## Clean code, steelmanned

Keep:

- reveal intent with names
- small change sets; Boy Scout Rule on touched code
- tests as first-class code
- dependency rule / inward-facing policy modules where the domain warrants it
- semantic stability of tests (mutation mindset)

Drop as religion:

- ceremonial micro-functions that harm navigation
- speculative abstractions for imagined futures
- "never read agent code" without complete fitness functions

## Design before code

Substantial user-visible or API change needs a short design gate before implementation PRs:

- problem statement
- non-goals
- proposed interface
- failure modes
- proof plan
- rollout / compatibility

Implementation review is for the code, not first principles.

## Small, bisectable change

From kernel culture:

- one logical change per patch
- series builds and passes at every step
- no mixed reformat + feature
- easy revert

Agents can produce huge diffs. The harness should still prefer small lands.

## Accountability

Someone with a name owns:

- merge decision
- production consequences
- follow-up debt on that module

Generation source (human, agent, mixed) does not transfer liability.
