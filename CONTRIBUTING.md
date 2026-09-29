# Contributing

Contributions are welcome for skill instructions, installation guidance, and client configuration examples.

Keep changes focused on discovery through the hosted TadaPay Marketplace MCP. This repository does not host the server, merchant catalog, review records, or payment execution code. Do not add scraped catalogs, deployment files, or wallet credentials.

## Propose a change

Open an issue describing the user-facing problem, or submit a pull request with:

- The behavior or documentation being changed.
- The application and version used to check it.
- The commands or prompts used, expected results, and observed results.

Use synthetic examples for reproduction. Remove credentials and personal information from logs. Do not run paid requests or make purchases as part of testing this skill.

## Check your change

- Keep the skill name and directory name aligned: `tadapay-marketplace`.
- Preserve valid YAML frontmatter in `SKILL.md` and valid client configuration examples.
- Check relative documentation links and installation paths.
- Exercise ordinary discovery, missing metadata, and unavailable-service cases.
- Check that unsupported filters are not sent, review scope is not overstated, and discovery never initiates payment.

Prefer the live MCP tool schemas over copied parameter lists. Do not hardcode catalog counts or merchant records into the skill.

Merchant onboarding and catalog maintenance are handled separately by TadaPay. Keep pull requests focused on the skill and its documentation.

Contributions are made under the repository's [MIT license](LICENSE).
