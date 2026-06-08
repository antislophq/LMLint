# LMLint

LMLint is a linter that uses rules defined in markdown.

<!--LMLint is designed to work with cheap models and is Git-aware, so it only runs on changed files.-->

### Motivation

What if every single PR comment could be converted into a rule? Take this comment for example:

<!-- comment_image.png -->

Converting this into an ESLint rule isn't trivial since it requires defining an AST-based rule.

With LMLint, the above comment can be turned into a rule with a simple GitHub comment (`@lmlint make this a rule`). LMLint then opens a PR with the rule added.

### Isn't this expensive?

LLM-based rules are more expensive to run that traditional lint rules that are defined in code. However, LMLint is intentionally designed to reduced costs. (a) it works well with cheap models and (b) is Git-aware, so it only runs on changed files.

### Isn't this slow?

Not really. Rules can be evaluated in parallel, so running time doesn't significantly vary with the number of rules or files.
