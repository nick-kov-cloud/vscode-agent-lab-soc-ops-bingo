---
name: copilot
description: Core instructions for working with the Soc Ops bingo game project. Follow these guidelines for all code changes, features, and improvements.
---

## Project Overview

**Soc Ops** is a social bingo game for in-person mixers. Players find people matching bingo card questions and mark them off. Get 5 in a row (horizontally, vertically, or diagonally) to win.

### Tech Stack
- **Frontend**: React 19 + TypeScript
- **Styling**: Tailwind CSS 4 with vite plugin
- **Build**: Vite 7
- **Testing**: Vitest
- **Linting**: ESLint with TypeScript support
- **Deployment**: GitHub Pages (automatic on push to main)

### Project Structure
```
src/
├── components/          # React UI components
│   ├── BingoBoard.tsx  # Main board display
│   ├── BingoSquare.tsx # Individual square component
│   ├── BingoModal.tsx  # Modal dialogs
│   ├── GameScreen.tsx  # Active game view
│   └── StartScreen.tsx # Welcome/setup screen
├── utils/
│   ├── bingoLogic.ts   # Core game mechanics
│   └── bingoLogic.test.ts
├── hooks/
│   └── useBingoGame.ts # Game state management
├── data/
│   └── questions.ts    # Bingo question database
└── types/
    └── index.ts        # TypeScript type definitions
```

## Code Quality Standards

### Testing Requirements
- Write unit tests for utility functions (especially game logic)
- Use Vitest for all tests
- Aim for >80% coverage on game mechanics
- Test edge cases: empty boards, invalid marks, winning conditions

### Linting & Formatting
- All code must pass ESLint without warnings
- Run `npm run lint` before submitting changes
- Use TypeScript strict mode (enforced in tsconfig.json)
- No unused imports or variables

### Type Safety
- Always use TypeScript types, avoid `any`
- Define proper interfaces in `src/types/index.ts`
- Use discriminated unions for variant types (e.g., game states)

## React & Component Guidelines

### Component Structure
- Use functional components with hooks
- Keep components focused and single-responsibility
- Extract reusable logic into custom hooks
- Use React 19+ features (no legacy patterns)

### State Management
- Use `useBingoGame` hook for game state
- Prefer React hooks over external state libraries
- Keep component state local when possible

### Performance
- Memoize expensive components with `React.memo` if needed
- Use efficient key strategies in lists
- Avoid unnecessary re-renders

## Styling with Tailwind CSS 4

### Best Practices
- Use Tailwind utility classes exclusively (no custom CSS unless unavoidable)
- Leverage CSS variables for theming
- Use Tailwind's `@apply` directive sparingly
- Follow Tailwind v4 plugin patterns (vite integration)

### Design Philosophy
- Keep the UI clean and engaging
- Ensure accessibility (WCAG 2.1 AA)
- Mobile-first responsive design
- Consistent spacing and typography

## Game Logic Standards

### Core Rules (Immutable)
- Board is 5x5 with 25 squares (0-24 IDs)
- Center square (index 12) is always free
- Win conditions: 5 in a row (horizontal, vertical, diagonal)
- Questions should be diverse and encourage mingling

### Question Guidelines
- Icebreaker-style prompts that spark conversations
- Inclusive and appropriate for professional/social settings
- Mix of quick/easy and observation-based questions
- Avoid controversial or exclusionary topics

## Git & Commit Practices

### Commit Messages
- Use clear, descriptive commit messages
- Format: `[feature|fix|refactor|docs]: Description`
- Example: `[feature]: Add animations to winning board state`

### Branch Naming
- Feature branches: `feature/description`
- Bug fixes: `fix/description`
- Docs: `docs/description`

## Development Workflow

### Before Submitting Work
1. Run `npm run lint` and fix any issues
2. Run `npm run test` and ensure all tests pass
3. Run `npm run build` to verify production build
4. Test in browser at http://localhost:5173
5. Commit with clear messages

### Pull Request Checklist
- [ ] Tests pass and cover new functionality
- [ ] Linting passes without warnings
- [ ] Build succeeds without errors
- [ ] Code follows TypeScript/React best practices
- [ ] Commit messages are descriptive
- [ ] No console errors or warnings

## Common Tasks

### Adding a New Feature
1. Create a feature branch: `git checkout -b feature/your-feature`
2. Write tests first (TDD approach)
3. Implement the feature
4. Update types if needed
5. Verify ESLint and tests pass
6. Commit and push

### Modifying Game Questions
- Edit `src/data/questions.ts`
- Keep questions diverse and engaging
- No need for additional tests unless logic changes
- Re-run dev server to see changes immediately

### Updating Game Logic
- Modify `src/utils/bingoLogic.ts`
- Update corresponding tests in `bingoLogic.test.ts`
- Ensure 100% test coverage for logic functions
- Verify with `npm run test`

## Performance & Accessibility

### Accessibility Requirements
- Semantic HTML structure
- Proper ARIA labels where needed
- Keyboard navigation support
- Color contrast ratios (WCAG AA minimum)
- Test with screen readers

### Performance Targets
- Page load < 2s on 4G
- Smooth 60fps animations
- Minimal bundle size (current: ~200KB gzipped)

## Debugging Tips

- Use React DevTools browser extension for component inspection
- Check Vite dev server logs for build issues
- Browser DevTools console for runtime errors
- Vitest watch mode for iterative testing: `vitest`

## Questions or Clarifications?

When in doubt:
- Check existing tests for patterns
- Review similar components for structure
- Run tests to validate behavior
- Ask clarifying questions about requirements
