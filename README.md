# NuxtNxBug

This is a bug reproduction repository for Nuxt and Nx with pnpm workspaces.

We have a Nuxt app that is part of a Nx workspace. There is a `.env` and a `.env.staging` file in the root of the `apps/backend` Nuxt app.  The `.env.staging` file should be used when running the `dev:staging` task.

The problem is that when the `dev:staging` task is run, the `.env` file is used instead of the `.env.staging` file, even though the appropriate command is run in the correct directory (or it appears to be).

When the `nuxi dev --dotenv .env.staging` command is run manually in the `apps/backend` directory, it works as expected.

Not sure if this is a bug in Nx, Nuxt, or something else.

## Steps to reproduce

1. Clone this repository
2. Run `pnpm install`

### Regular dev mode (works)
1. Run `pnpx nx run backend:dev`
2. Check the console output, `nuxt dev` is run
3. Check the app in the browser, it shows `.env / default` as expected

### Staging dev mode (doesn't work)
1. Run `pnpx nx run backend:dev:staging`
2. Check the console output, `nuxi dev --dotenv .env.staging` is run
3. Check the app in the browser, it shows `.env / default` instead of `.env.staging / staging`

### Manually running the staging command (works)
1. Run `cd apps/backend`
2. Run `nuxi dev --dotenv .env.staging`
3. Check the app in the browser, it shows `.env.staging / staging` as expected
