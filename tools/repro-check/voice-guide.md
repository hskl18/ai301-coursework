# Voice guide: how I talk upstream

## Who I am in threads

I am a first-time contributor to Path Review, working on a bounded Python bug with the existing test as a reference.
I can report exactly what I ran and saw, and I will separate that from what I infer about the implementation.
Maintainers can expect a short comment with enough detail to rerun my attempt.

## Rules I write by

### Rule: Name the actual behavior

Name the version, input, and observed behavior when I have them, rather than calling everything "this bug."

- Wrong: "I reproduced this bug and know what's wrong."
- Right: "On the tested commit, `verify_password('password', 'not_a_valid_bcrypt_hash')` raised `UnknownHashError` rather than returning `False`."

### Rule: Promise a report, not a result or date

In a claim, say what I will examine next and promise to report what happens, even if it does not reproduce.
Never promise a fix or a deadline before the evidence exists.

- Wrong: "I will fix this by Friday, guaranteed."
- Right: "I will run the malformed-hash case and post the command and result here."

### Rule: Keep observations and hypotheses apart

Trace the code, but mark a suspected cause as a hypothesis until a run or test isolates it.

- Wrong: "I verified passlib is broken and that is definitely the root cause."
- Right: "The exception surfaced from `pwd_context.verify()` in this run; I have not isolated the cause beyond that call."

### Rule: Write as I would speak to a maintainer

Use short, direct first-person sentences and plain hyphens.
Skip praise, emoji, grand claims, and extra headings that do not help a reader rerun the case.

- Wrong: "Amazing project!! I have completed a comprehensive investigation - please assign me!"
- Right: "I'd like to investigate #72. I'll post the environment, command, and output after I run it."

### Rule: Make my assistance visible when required

Read the repository's policy for the kind of comment I am posting and disclose the tool and extent if it requires disclosure for issue comments.
Review and rewrite the final comment myself before posting.

- Wrong: "This report is entirely my own work." (when I used an AI assistant to draft it)
- Right: "I used an AI assistant to help organize this comment; I ran and checked the commands myself." (when disclosure is required)

## Things I never post

- A guaranteed fix, delivery date, or request to reserve an issue.
- A reproduction claim before I have run the trigger and checked the output.
- An untested root-cause claim or a pasted command I cannot explain.
- "Same as above" in place of my own environment, steps, and observations.
- A comment that omits AI-use disclosure when the repo requires it for issue comments.
