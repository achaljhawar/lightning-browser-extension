# ⭐ Contribution guide for new developers

We welcome and appreciate new contributions.

- We expect contributors to abide by our underlying [Code of Conduct](./CODE_OF_CONDUCT.md) . All discussions about this project must be respectful and harassment-free.
- Remember that communication is the lifeblood of any Open Source project. We are all working on this together, and we are all benefiting from this software.
- It's very easy to misunderstand one another in asynchronous, text-based conversations. When in doubt, assume everyone has the best intentions.

### Creating an Issue

- Check if the issue you are going to propose is not duplicate of another issue.
- Open a new issue according to type i.e., if issue is a bug open a new issue by clicking on Bug Report.
- Give a precise and meaningful name of the issue.
- Describe your issue as good as possible that may ease the process of issue-reviewing by a community member.

### How to contribute

- Fork the project and clone it to your local machine. Follow the [setup](./SETUP.md) guideline.
- Always take a pull from the remote repository to your master branch to keep it at sync with the main project(updated repository).

  ```
  git pull upstream master
  ```

* Create a branch. For details on how to name your branches, see [Branch names](#branch-names).

  ```
  git checkout -b feat/feature-name
  ```

  This both creates and checks out that branch in one command.
  The feature name should provide a (short) description of the issue.

- Follow the [translation](#translations) rules while translating UI strings

- Commit your changes and push it to your fork of the repository. For details on how to name your commit, see [Commit Message Format](#commit-message-format).

- Create Pull Request (PR). Make sure to comment the issue that your PR is supposed to solve.

### Creating a Pull Request

When creating a PR please take this points as a reminder:

- If there's not yet an issue for your PR please first [create an issue](https://github.com/bumi/lightning-browser-extension/issues/new) with a proposal what you would like to do. This allows us to give feedback and helps you no wasting time and motivation
- Think in iterations (babysteps)\
  You can always start a PR and if you feel like adding on more things to it, better branch off and [create a new i.e. _draft_-PR](https://github.blog/2019-02-14-introducing-draft-pull-requests/)
- Newly added components should have a unit-test
- If you work on a more complex PR please [join our community chat](https://bitcoindesign.slack.com/archives/C02591ADXM2) (Invite link at https://bitcoin.design/) to get feedback, discuss the best way to tackle the challenge, and to ensure that there's no duplication of work. It's often faster and nicer to chat or call about questions than to do ping-pong comments in PRs

### Code format & preferences

- [ESLint](https://eslint.org/) for code linting
- [Prettier](https://prettier.io/) for code (and more) formatting
- We prefer [Axios](https://axios-http.com/) over [fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)

#### Code Editors

##### [VS Code](https://code.visualstudio.com/)

For better support we recommend these extensions:

- [vscode-eslint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [prettier-vscode](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [vscode-tailwindcss](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss)
- [vscode-html-css](https://marketplace.visualstudio.com/items?itemName=ecmel.vscode-html-css)

### Branch names

Please prefix your branch names with `feat/`, `fix/`, `chore/`, `refactor/`, `docs/` based on the intent of the branch or issue being addressed (see commit message format below).

### Commit message format

Alby enforces [Conventional Commits Specification](https://www.conventionalcommits.org/en/)

> A specification for adding human and machine-readable meaning to commit messages

### Translations

Alby uses [Weblate](https://weblate.org/en/) to manage translations for different locales. If you'd like to contribute, you can [add translations here](https://hosted.weblate.org/projects/getalby-lightning-browser-extension/getalby-lightning-browser-extension/).

### Rules for developers adding new i18n translation strings:

[Not to be confused with language translations]

#### We categorize strings into:

1. **Translations**\
   Here we again divide strings as per screens (Welcome, Home...)
1. **Common**\
   All the common words and actions (Confirm, Delete, Edit...)
1. **Components**\
   The i18n strings which exist within the components (SitePreferences, QRCodeScanner, PublisherCard...)

#### Use underscores instead of camelCase

✅ Correct

```json
"pay_now": "Pay Now"
```

❌ Wrong

```json
"payNow": "Pay Now"
```

#### To avoid confusion, we prefer indentation over underscores, i.e.

✅ Correct

```json
{
  "blue": {
    "label": "Blue"
  }
}
```

❌ Wrong

```json
{
  "blue_label": "Blue"
}
```

#### Only indent strings when it is an input or has different attributes:

✅ Correct

```json
{
  "edit": {
    "title": "Edit Account",
    "label": "Name",
    "screen_reader": "Edit account name"
  }
}
```

❌ Wrong

```json
{
  "edit": {
    "title": "Edit Account"
  }
}
```

Correct way for this would be:

```json
{
  "edit": "Edit Account"
}
```

#### Use title for heading tags and label for label tags

##### When the content is copy-text and you wish to divide it in parts, you can use numbers:

```json
{
  "enable": {
    "request1": "Request approval for transactions",
    "request2": "Request invoices and lightning information"
  }
}
```

##### For button text, you can use common translations:

```json
{
  "common": {}
}
```

#### You can add a new string if you don't find the suitable text in common. In that case, indent them within "actions":

```json
{
  "actions": {
    "add_account": "Add account"
  }
}
```

_Usually, we prefer single words in `common`, phrases like "Get Started", "Enable Now" can be indented in the above way._

#### Similarly, the error messages go within "errors":

```json
{
  "errors": {
    "enter_password": "Please enter a new unlock password.",
    "confirm_password": "Please confirm your password.",
    "mismatched_password": "Passwords don't match."
  }
}
```
