# .github

Organization-wide files for [Moloch-AI](https://github.com/Moloch-AI).

| Path | Purpose |
| --- | --- |
| [`profile/README.md`](profile/README.md) | The profile shown on the organization page |
| [`profile/assets/`](profile/assets) | Logo files used by the profile, from the MolochAI brand kit |
| [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md) | Contributor Covenant 2.1 |
| [`CONTRIBUTING.md`](CONTRIBUTING.md) | Ground rules that apply to every repository |
| [`SECURITY.md`](SECURITY.md) | How to report vulnerabilities |
| [`SUPPORT.md`](SUPPORT.md) | Where to get help |
| [`.github/ISSUE_TEMPLATE/`](.github/ISSUE_TEMPLATE) | Default issue forms |
| [`.github/pull_request_template.md`](.github/pull_request_template.md) | Default pull request template |

GitHub uses these community health files for any repository in the organization that does not have its own. Repositories keep their own `CONTRIBUTING.md` and `SECURITY.md` for project-specific commands and details.

## Checks

CI lints the Markdown with [markdownlint-cli2](https://github.com/DavidAnson/markdownlint-cli2) and checks links with [lychee](https://github.com/lycheeverse/lychee). To run the lint locally:

```bash
npx markdownlint-cli2 "**/*.md"
```

## License

The text in this repository is available under the [MIT License](LICENSE). The MolochAI name and logo are trademarks of MolochAI and are not covered by that license. Use them only to refer to MolochAI.
