# LMLint

LMLint is a linter that uses rules defined in markdown.

<!--LMLint is designed to work with cheap models and is Git-aware, so it only runs on changed files.-->

### Motivation

What if every single PR comment could be converted into a rule? Take this comment for example:

<!-- comment_image.png -->

Converting this into an ESLint rule isn't trivial since it requires defining an AST-based rule.

With LMLint, creating a rule is as simple as commenting `@lmlint make this a rule`. LMLint then opens a PR with the rule added as a markdown file.

### Install

```bash
curl -sSL https://raw.githubusercontent.com/antislophq/lmlint/main/install.sh | bash
```

### Usage

Run the `init` command to create a sample rule:

```bash
# Creates a .rules/ directory with a sample rule
lmlint init
```

Then run the `check` command to run the rule:

```bash
lmlint check
```

### FAQs

#### Is this slow?

Not really. Rules are evaluated in parallel, so a run completes within a few seconds irrespective of the number of rules or files.

#### Is this expensive?

LMLint is intentionally designed to reduced costs:

- LMLint works well with cheap models (like Claude Haiku, or the GPT mini series) as long as your rules are concise
- LMLint is Git-aware, so it only runs on changed files by default

#### Is this unreliable?

If your rules are small & specific, LMLint is fairly reliable. When rules are large or ambiguous, LMLint may produce false positives or negatives. Such failures are fixed by updating rules over time. To make this easier, LMLint also provides a `preview` command that looks at previous PRs and shows what a rule would've flagged.
