# Copy

Read when writing or reviewing UI text, docs, or reports. The cause of padded copy is repetition and explanation, not punctuation. Fix the cause.

## Rules

1. **Say a fact once.** A fact shown by a label, value, or badge is not restated in a sentence on the same view.
2. **Label plus value over prose.** Status is a label and a value, or a badge. Use a sentence only when the user must act.
3. **Do not explain obvious state.** If the interface needs a sentence to explain itself, fix the interface instead.
4. **Short labels.** UI labels are 4 words or fewer, without articles, and name the result of the action ("Save draft", not "Click here to save your draft").
5. **No courtesy filler.** No "please" or "thank you" in UI text. Say "sorry" only for a real failure.
6. **Keep full content where it matters.** Error messages, security warnings, and destructive confirmations state what happened, what it affects, and what to do. Never cut them for brevity.
7. **Reports and docs lead with the answer.** Length follows the decisions the reader must make, not the work you did. End with one specific next step, not a list of offers.
8. **Dashes (house preference).** No em or en dashes in copy and docs; use a period, comma, colon, or parentheses. This is a style choice enforced by grep, not a sign of quality. Do not swap in "--" to dodge the check; rewrite the sentence.
9. **Watch-list words are a review aid.** Inflated words ("delve", "tapestry", "pivotal", "showcase", "testament") and patterns ("not X, but Y", lists of three) are common in human text too. Rewrite only when several cluster in one paragraph.
10. **Never frame copy review as detecting AI authorship.** Name the defect: repeated, padded, vague, unclear.

Rules 1 to 7 come from public UI-writing guides, not measurement. Cutting too far yields fragments and arrow chains; when a short version is unclear, keep the words.

## Worked example

A billing page for an account on a free plan stated one fact, that nothing is charged on the free plan, four times across badges, labels, and sentences, then added two sentences explaining it. The page had no dashes, so a punctuation rule would have passed it.

Fix: one row per fact.

```
Plan      Free
Charges   None
```

Delete the sentences. If the page also shows two counters that look alike but disagree (for example, messages sent and free messages used), that is a labeling question, not a wording one: name exactly what each counts.

## Checks

- Mechanical: courtesy words, chat closers, dashes, label word counts ([index.md](index.md)).
- Repeated facts: collect the strings of each changed view and look for the same fact twice. This needs the source strings; a screenshot cannot be grepped.
- Judgment: read each changed view top to bottom and ask what each sentence adds that no label gives.

## Done when

- [ ] No fact appears twice on one view.
- [ ] Status uses label plus value; every remaining sentence asks the user to act or adds a fact.
- [ ] Labels are 4 words or fewer; no courtesy filler.
- [ ] Errors and destructive confirmations are complete.
- [ ] The dash grep is clean, or the project has opted out of the preference.
