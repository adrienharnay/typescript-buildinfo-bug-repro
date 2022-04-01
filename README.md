# typescript-buildinfo-bug-repro

This repository is a reproduction for a cache error regarding `tsconfig.tsbuildinfo` when a TS file imported by a .d.ts is changed.

## Steps

- Run `yarn lint` or `npm run lint`.
- The command succeeds.
- Change the value returned by `constants.ts` to `2`.
- Run `yarn lint` or `npm run lint` again.
- The command succeeds (it should not, and VSCode picks up the error).

Workaround:

- Run `yarn lint:clean` or `npm run lint:clean` (to delete the `tsconfig.tsbuildinfo`).
- Run `yarn lint` or `npm run lint` again.
- The command fails, as it should.
