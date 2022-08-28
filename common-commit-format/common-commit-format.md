# 1-) Semantic Commit Messages

See how a minor change to your commit message style can make you a better programmer.

Format: `<type>(<scope>): <subject>`

`<scope>` is optional

## Example

```
feat: add hat wobble
^--^  ^------------^
|     |
|     +-> Summary in present tense.
|
+-------> Type: chore, docs, feat, fix, refactor, style, or test.
```

More Examples:

- `feat`: (new feature for the user, not a new feature for build script)
- `fix`: (bug fix for the user, not a fix to a build script)
- `docs`: (changes to the documentation)
- `style`: (formatting, missing semi colons, etc; no production code change)
- `refactor`: (refactoring production code, eg. renaming a variable)
- `test`: (adding missing tests, refactoring tests; no production code change)
- `chore`: (updating grunt tasks etc; no production code change)

Original Version:

- https://gist.github.com/joshbuchea/6f47e86d2510bce28f8e7f42ae84c716

References:

- https://www.conventionalcommits.org/
- https://seesparkbox.com/foundry/semantic_commit_messages
- http://karma-runner.github.io/1.0/dev/git-commit-msg.html

# 2-) If you are using Jira (or similar tools)

Every task has an Id and summary
You need to use these Id and summary to add a commit message

## Example

EXAMPLE TASK URL: https://your-jira-name.atlassian.net/browse/HAGS-86
EXAMPLE SUMMARY: Fix General Modal's Css

HAGS-86 is task's ID now.

### Commit message can be like this

HAGS-86 | Fix General Modal's Css
