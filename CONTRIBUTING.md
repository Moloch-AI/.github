# Contributing to Moloch-AI projects

Thanks for helping. This guide applies to every repository in the organization. Each repository also has its own `CONTRIBUTING.md` with the exact setup, test and lint commands, so read that one before you start.

## Ways to contribute

- **Report a bug.** Open an issue in the repository where it happens. Include the version or commit, your OS and runtime version, what you ran, what you expected, and what happened. Redact API keys, and prompts you do not want public.
- **Fix a bug or improve the docs.** Small fixes can go straight to a pull request.
- **Propose a feature.** Open an issue first, so we can agree on the approach before you write code.
- **Correct a fact.** If a README, guide or example disagrees with the [API documentation](https://molochai.dev/docs?utm_source=github&utm_medium=oss&utm_campaign=org-profile) or with a model's own card, an issue or pull request that links the source is very welcome.

Questions about your account, billing or the hosted API are not repository issues. Use [molochai.dev/contact](https://molochai.dev/contact?utm_source=github&utm_medium=oss&utm_campaign=org-profile).

## Ground rules

1. **Match the real API.** Code and docs must follow the public [API documentation](https://molochai.dev/docs?utm_source=github&utm_medium=oss&utm_campaign=org-profile). Do not add parameters, endpoints or behavior the API does not have. If the API does not support something, say so instead of working around it silently.
2. **Source every model fact.** Context length, license, input types and similar facts come from the base model's own card, linked. Do not add benchmark claims, rankings or "best model" wording.
3. **Never commit secrets.** No API keys, tokens or private URLs, not even expired ones. Tests and examples run against the mock server from [uncensored-ai-api](https://github.com/Moloch-AI/uncensored-ai-api) or in-process mocks, with placeholder keys such as `mock-key`.
4. **Keep changes focused.** One logical change per pull request. Update tests and docs in the same pull request as the code they describe.
5. **Keep dependencies lean.** Add a dependency only when it clearly earns its place, and explain why in the pull request.

## Pull request checklist

- [ ] Tests pass and lint is clean with the commands in the repository's `CONTRIBUTING.md`.
- [ ] New behavior has tests. Bug fixes include a test that fails without the fix.
- [ ] README, examples and changelog are updated where behavior changed.
- [ ] No secrets, personal data or internal infrastructure details in code, tests, fixtures or commit messages.

Write commit messages in the imperative mood (`Add retry cap for Retry-After`) and say why in the body when it is not obvious.

## Writing style

Plain, specific and honest about limits: an engineer explaining a system to another engineer. State numbers, and say what a thing does not do. Avoid marketing words such as "revolutionary", "seamless" or "unleash", and avoid absolute claims such as "no refusals" or "unlimited". When describing the models, say "reduced refusal behavior" or "less-restricted", and use "uncensored" where people search for it, explained.

## License

By contributing, you agree that your contributions are licensed under the license of the repository you contribute to (MIT for every repository in this organization).

## Code of Conduct

Everyone taking part is expected to follow the [Code of Conduct](CODE_OF_CONDUCT.md).
