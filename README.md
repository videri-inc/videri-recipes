# videri-recipes

Job-shaped, validated builds on the Videri REST API. Each recipe is a complete
experience you can run from the starter kit and adapt, with a `recipe.md` that
records what it does, what it relies on, the prompt that produced it, and how
far it has been validated.

**Status: public preview.** The first recipe (menu board) is in progress.
Licensed under Apache-2.0; recipe documents may be reused with attribution.

## Layout

```
CONFORMANCE.md          the checklist that moves a recipe from prototype to validated
TEMPLATE/recipe.md      copy this to start a new recipe
<recipe-name>/
  README.md             what it does, how to run it from the starter, screenshots
  recipe.md             job, capabilities used, prompt, decisions, gotchas, maturity, conformance
  conformance/          one dated file per checklist run
  ...source...
```

## Maturity labels

Every recipe carries exactly one, as a GitHub topic and in its `recipe.md`:

| Label | Meaning | Sales language |
|---|---|---|
| `prototype` | Runs; not reviewed | Can be shown |
| `validated-recipe` | Passed `CONFORMANCE.md`; reviewed API, UX and security | Can be offered as a starting point |
| `supported-experience` | QA, hosting, named owner, service level | Can be sold |
| `product-feature` | Promoted into the core platform | Part of the product |

A prototype is shown, a validated recipe is offered, only a supported
experience is sold.

## Planned recipes

1. Menu board (CORE-10268), from the existing menu-board build with
   customer-estate specifics removed.
2. Canvas discovery and device health.
3. Then, as opportunities land: content actions, scheduling, dynamic data,
   multi-screen.

## Adding a recipe

1. Copy `TEMPLATE/recipe.md` into a new folder and fill every section.
2. Reference only capabilities that exist in `videri-context/CAPABILITIES.md`
   and gotchas that exist in `videri-context/GOTCHAS.md`; add missing ones
   there first.
3. Include the prompt(s) that generated the build, verbatim.
4. Open a pull request; the template asks for the conformance status.

## Related

- Context pack: https://github.com/videri-inc/videri-context
- Starter kit: https://github.com/videri-inc/videri-starter
