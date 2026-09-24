# locAIlize

Localization intelligence for Visual Studio Code.

locAIlize helps developers understand localization coverage, inspect source references, review translations, and test internationalized interfaces without leaving VS Code.

> This repository is the public support and feedback hub for the locAIlize VS Code extension. The extension source code is not hosted here.
>
> **Proprietary software:** All rights reserved. This repository provides documentation, release information, and issue tracking only.

## Features

- Discover JSON locale resources and flatten nested keys.
- Index static localization references in JavaScript, TypeScript, JSX, TSX, and supported framework files.
- Navigate between locale resources and source references.
- Review translations in the Resource Grid.
- Search, filter, and edit translations inline.
- Detect missing locale values and empty translations.
- Detect placeholder mismatches and invalid message-format braces.
- Detect unused resource keys and source references without matching resources.
- Validate plural categories using locale-aware CLDR rules.
- Detect invalid or invisible Unicode characters.
- Inspect comments, variables, source locations, and issue details.
- Use VS Code language models for context enrichment and translation assistance.
- Import and export XLIFF 2.0 files.
- Lock source strings that must not be localized.
- Run deterministic pseudo-localization against an existing locale file.
- Test accented Latin, long text, RTL, CJK, Cyrillic, Greek, Devanagari, Thai, combining-mark, and bidi scenarios.

## Getting Started

1. Install locAIlize from the Visual Studio Code Marketplace.
2. Open a project containing locale JSON files.
3. Open the locAIlize view from the Activity Bar.
4. Enable indexing if it is disabled.
5. Expand `Workspace resources` to inspect locale files and keys.
6. Open a locale file or key to launch the Resource Grid.

The included source reference analysis is strongest with i18next-style calls such as:

```ts
 t('account.welcome');
 i18n.t('account.welcome');
```

## Resource Grid

The Resource Grid provides:

- Locale selection.
- Source and translation comparison.
- Missing and updated filters.
- Issue and unused-key filters.
- Inline multiline editing.
- Source-file navigation.
- Locale-aware LTR and RTL translation display.
- Localization and XLIFF synchronization statuses.

Clicking a string highlights it within the complete locale-file scope rather than filtering the grid to one row.

## AI Features

AI actions are explicitly user initiated. Depending on the command, locAIlize can:

- Enrich one key with contextual information.
- Enrich a locale file.
- Enrich the project.
- Translate one key.
- Translate a locale file.
- Translate a project.

AI features use language model providers exposed by VS Code. Availability and output quality depend on the configured provider and model.

Translation requests preserve localization keys, placeholders, tags, and source context. Locked strings are excluded from translation actions.

## Pseudo-Localization

Pseudo-translation writes deterministic test values into an existing locale file. It does not create a separate pseudo-locale by default.

Available profiles include:

- Accented Latin.
- Long text.
- Cyrillic.
- Greek.
- Arabic RTL.
- CJK.
- Devanagari.
- Thai.
- Vietnamese combining marks.
- Mixed bidirectional text.

Use pseudo-localization to test text expansion, script coverage, RTL behavior, combining marks, placeholders, and layout resilience.

## XLIFF

locAIlize supports XLIFF 2.0 export and import workflows.

Generated XLIFF files are written under the workspace `.locailize/export` directory. The extension tracks synchronization state for exported and imported translation records and reports source changes and conflicts.

## Locking Source Strings

Some source strings should be visible to localization tooling but must not be translated, such as product names, technical identifiers, or intentionally universal text.

Use **Lock string** on a source key to:

- Persist the lock in `.locailize/locks.json`.
- Restore the source value in target locale files.
- Prevent AI translation.
- Prevent XLIFF imports.
- Prevent inline grid edits.

Use **Unlock string** to restore normal localization behavior.

## Diagnostics

Current diagnostics include:

- Malformed locale JSON.
- Missing locale values.
- Empty translations.
- Placeholder mismatches.
- Invalid message-format braces.
- Missing ICU `other` branches for detected plural/select expressions.
- Missing plural categories based on locale rules.
- Unused resource keys.
- Source references without matching resources.
- Invalid or invisible Unicode characters.

Diagnostics appear in the VS Code Problems panel and in the locAIlize tree.

## Privacy

locAIlize performs indexing and diagnostics locally. AI actions are explicit and send only the records required for the selected operation to the chosen VS Code language model provider.

Do not include secrets, credentials, or sensitive customer data in localization resources or issue reports.

## Feedback and Issues

Please use [GitHub Issues](https://github.com/adafieno/locAIlize/issues) for:

- Bug reports.
- Feature requests.
- Framework support requests.
- Diagnostic false positives.
- Translation workflow feedback.
- Pseudo-localization results.

When reporting a bug, include:

- Visual Studio Code version.
- locAIlize version.
- Operating system.
- Locale file shape and source-call pattern.
- Steps to reproduce.
- Expected behavior.
- Actual behavior.
- Relevant diagnostic output.

Please remove proprietary strings and sensitive project content before sharing examples.

## Support Repository

This repository contains public documentation, release information, and issue tracking for locAIlize. The extension is distributed through the Visual Studio Code Marketplace.

- [Report an issue](https://github.com/adafieno/locAIlize/issues)
- [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/)

## License

locAIlize is proprietary software. All rights are reserved by the copyright holder.

The extension is distributed through the Visual Studio Code Marketplace under its Marketplace terms. This repository contains public documentation and support materials only; no source-code license is granted.
