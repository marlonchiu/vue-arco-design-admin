 git commit -m "feat: 修复代码文件格式问题"

> vue-arco-design-admin@1.0.0 lint-staged
> npx lint-staged

✔ Preparing lint-staged...
⚠ Running tasks for staged files...
  ❯ package.json — 6 files
    ❯ *.{js,ts,jsx,tsx} — 1 file
      ✔ prettier --write
      ✖ eslint --fix
    ❯ *.vue — 2 files
      ✖ stylelint --fix [FAILED]
      ◼ prettier --write
      ◼ eslint --fix
    ↓ *.{less,css} — no files
↓ Skipped because of errors from tasks.
✔ Reverting to original state because of errors...
✔ Cleaning up temporary files...

✖ stylelint --fix:
TypeError: opts.node.rangeBy is not a function
    at new Warning (D:\github_projects\vue-arco-design-admin\node_modules\.pnpm\postcss@8.5.6\node_modules\postcss\lib\warning.js:9:29)
    at Result.warn (D:\github_projects\vue-arco-design-admin\node_modules\.pnpm\postcss@8.5.6\node_modules\postcss\lib\result.js:30:19)
    at reportUnknownRuleNames (D:\github_projects\vue-arco-design-admin\node_modules\.pnpm\stylelint@14.13.0\node_modules\stylelint\lib\reportUnknownRuleNames.js:70:16)
    at D:\github_projects\vue-arco-design-admin\node_modules\.pnpm\stylelint@14.13.0\node_modules\stylelint\lib\lintPostcssResult.js:71:7
    at Array.map (<anonymous>)
    at lintPostcssResult (D:\github_projects\vue-arco-design-admin\node_modules\.pnpm\stylelint@14.13.0\node_modules\stylelint\lib\lintPostcssResult.js:70:19)
    at lintSource (D:\github_projects\vue-arco-design-admin\node_modules\.pnpm\stylelint@14.13.0\node_modules\stylelint\lib\lintSource.js:103:8)
    at async D:\github_projects\vue-arco-design-admin\node_modules\.pnpm\stylelint@14.13.0\node_modules\stylelint\lib\standalone.js:214:27
    at async Promise.all (index 0)
    at async standalone (D:\github_projects\vue-arco-design-admin\node_modules\.pnpm\stylelint@14.13.0\node_modules\stylelint\lib\standalone.js:254:22)
✔ Preparing lint-staged...
⚠ Running tasks for staged files...
  ❯ package.json — 6 files
    ❯ *.{js,ts,jsx,tsx} — 1 file
      ✔ prettier --write
      ✖ eslint --fix [KILLED]
    ❯ *.vue — 2 files
      ✖ stylelint --fix [FAILED]
      ◼ prettier --write
      ◼ eslint --fix
    ↓ *.{less,css} — no files
↓ Skipped because of errors from tasks.
✔ Reverting to original state because of errors...
✔ Cleaning up temporary files...
husky - pre-commit hook exited with code 1 (error)
