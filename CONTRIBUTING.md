# Contributing to Storyboard AI

Thank you for considering contributing to Storyboard AI! We welcome individuals who want to help us improve the platform, whether it's by fixing bugs, improving documentation, or adding new features.

The following is a set of guidelines for contributing to Storyboard AI. These are guidelines, not rigid rules. Use your best judgment, and feel free to propose changes to this document in a pull request.

## 🚀 How to Contribute

### Reporting Bugs

This section guides you through submitting a bug report. Following these guidelines helps maintainers and the community understand your report, reproduce the behavior, and find related reports.

- **Use the GitHub Issues search** — check if the issue has already been reported.
- **Check if the issue has been fixed** — try to reproduce it using the latest `main` branch.
- **Isolate the problem** — ideally create a reduced test case.

**If you find a closed issue that seems like it is the same thing that you're experiencing, open a new issue and include a link to the original issue in the body of your new one.**

### Suggesting Enhancements

This section guides you through submitting an enhancement suggestion, including completely new features and minor improvements to existing functionality.

- **Use a clear and descriptive title** for the issue to identify the suggestion.
- **Provide a step-by-step description of the suggested enhancement** in as much detail as possible.
- **Explain why this enhancement would be useful** to most Storyboard AI users.

### Pull Requests

1. **Fork the repo** and create your branch from `main`.
2. **Clone the project** to your own machine.
3. **Create a new branch**:
   ```bash
   git checkout -b feature/my-new-feature
   ```
4. **Make your changes** and commit them:
   - We use conventional commits (e.g., `feat: add new feature`, `fix: resolve crash`).
5. **Push to your fork** and submit a **Pull Request**:
   ```bash
   git push origin feature/my-new-feature
   ```
6. **Open a PR** on GitHub against our `main` branch.

### Code Style Standards

- **TypeScript**: We use TypeScript with strict typing. Please ensure there are no unnecessary `any` types.
- **Styling**: We use Tailwind CSS v4. Avoid writing custom CSS in global files unless it's a reusable utility.
- **Linting & Formatting**: Run `pnpm run lint` and `pnpm run typecheck` before committing to ensure your code follows our standards.

## 🛠 Development Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/shakibzcv/storyboard-ai.git
   cd storyboard-ai
   ```
2. Install dependencies:
   ```bash
   pnpm install
   ```
3. Set up your `.env` file (see [README.md](README.md)).
4. Set up the database and run migrations:
   ```bash
   pnpm run db:migrate
   ```
5. Run the development server:
   ```bash
   pnpm run dev
   ```

## 🧪 Code Verification

We enforce code quality through automated verification checks before merging:

- **Run Linter**: `pnpm run lint`
- **Run Type Checks**: `pnpm run typecheck`
- **Verify Build**: `pnpm run build`

## 💬 Community & Contact

If you have any questions, suggestions, or need assistance contributing:

- **GitHub Issues & Discussions**: Start a discussion or open an issue on our [GitHub Issues](https://github.com/shakibzcv/storyboard-ai/issues) page.
- **Maintainer Contact**: Reach out directly to Shakib Khan via email at [shakibzcv@gmail.com](mailto:shakibzcv@gmail.com) or on GitHub [@shakibzcv](https://github.com/shakibzcv).

Thank you for contributing!
