# Subtract before you add

Apply when sequencing an addition, refactor, or rewrite. Remove dead weight, redundant validators, and stub references first, then build on the simpler base.

Adding to a complex system compounds complexity. Removing first shrinks the surface, shows the essential structure, and usually makes the next design obvious.

- **Removal before construction.** Land deletions first, in their own commit.
- **Cut before you polish.** Get to the minimum before investing in quality.
- **Design for observed use,** not speculative edge cases.
- **No speculative validators, parsers, or guards** beyond what the spec demands. Out-of-spec features drag guards behind them: persistence, retry-on-startup, and schema migration each need their inputs defended.
- **Simplify instructions and prompts too:** remove redundant rules and oversized templates.
- **Delete a reference with no new content** rather than leaving a stub.
- Leave the design slightly simpler and more capable, behind the same or a smaller surface, than you found it.

**Check:** before adding, did you look for something to remove first?
