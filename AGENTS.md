# Agent Instructions

## Commits

- Follow [Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/).
- Use this message format:

  ```text
  <type>[optional scope][optional !]: <description>

  [optional body]

  [optional footer(s)]
  ```

- Use `feat` for new features and `fix` for bug fixes. Use other appropriate types, such as `docs`, `refactor`, `test`, `build`, `ci`, or `chore`, for other changes.
- Indicate breaking changes with `!` before the colon or a `BREAKING CHANGE:` footer explaining the change.
- Keep commits atomic: each commit must represent one coherent change. Do not combine unrelated features, fixes, refactors, or formatting changes.
- Include the tests and documentation needed for the same change in that commit. Keep each commit independently understandable and avoid leaving it in a broken state.
- Review the staged diff and run relevant checks before committing. Stage only files or hunks belonging to the intended change.
