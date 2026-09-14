# CONFORMANCE.md: the checklist between a prototype and a validated recipe

Version 1, 14 Sep 2026 (CORE-10270). A person runs this; automated checks are
added over time. Passing it moves a recipe from `prototype` to
`validated-recipe`. It does not make something a supported experience; that
needs QA, hosting, a named owner and a service level on top.

## How to run it

1. Copy the checklist below into `<recipe>/conformance/YYYY-MM-DD.md`.
2. Mark each item `PASS`, `FAIL` or `N/A` with one line of evidence (a request,
   a file, a screenshot name).
3. Sign it with your name and the environment you tested on.
4. Open a pull request that updates the recipe's `recipe.md` maturity and links
   the run. The reviewer re-checks any `FAIL` that was fixed in the same PR.

A recipe with any `FAIL` stays `prototype`.

## Checklist

### API usage

- [ ] Uses only endpoints present in a spec listed in `/openapi/index.json`;
      no undocumented or internal paths.
- [ ] Auth flow is correct: key to token, `id_token` as Bearer, refresh before
      expiry, refresh token never client-side.
- [ ] `x-tenant` on every call after the token call; `x-group` (or Canvas
      Service's `group_id`) used deliberately, not by accident or omission.
- [ ] Pagination handled through the starter's adapters; counts read from
      totals; page sizes within what the spec allows.
- [ ] Retries and error handling: `401` with an expiry message refreshes once;
      `403` is surfaced to the user; no unbounded retry loop.

### Security and tenancy

- [ ] No API key, password, refresh token or third-party secret in a client
      bundle, in the repository or in logs. (`grep` for `sk_test_`, `sk_prod_`,
      `password`, `api_key` before signing.)
- [ ] Cannot read or write outside the caller's tenant; tenant code comes from
      configuration or the signed-in user, never hard-coded.
- [ ] Destructive actions (create event, delete playlist or event, remove asset
      from playlist) are confirmed with the user; device commands have an
      explicit decision on confirmation.
- [ ] Hosting matches the guidance: public-API-only with a test key may live on
      a static host; anything touching internal data or production tenants
      goes through Videri's own hosting path.

### Platform capability

- [ ] Every capability the experience relies on is `Supported` or
      `Constrained` in `videri-context/CAPABILITIES.md`. Nothing `Unverified`
      or `Unsupported` is promised in the UI. (Until `CAPABILITIES.md` exists:
      every capability is exercised by a working request in the recipe.)

### Quality

- [ ] Functional pass on a sandbox tenant from a clean clone of the starter
      plus the recipe folder.
- [ ] Renders correctly on at least one representative canvas resolution and
      orientation, as the recipe's `README.md` states.
- [ ] `recipe.md` is complete: job, capabilities, prompt(s), decisions, gotchas
      hit, maturity, conformance link.

### Ownership

- [ ] Named owner in `recipe.md`.
- [ ] Hosting model stated.
- [ ] Maturity label set and consistent with this run.

## Record

```
Conformance run: <recipe> on <date>
Environment: sandbox / production
Reviewer: <name>
Result: PASS / FAIL (n items)
Notes:
```
