# Recipe: <name>

Copy this file into `<recipe-name>/recipe.md` and fill every section. Delete
the guidance in angle brackets.

## Job to be done

<One paragraph in the words of the person who needs it. Example for the menu
board: show a menu with prices and availability on the canvases in a location,
updatable without redeploying.>

## Capabilities used

<One bullet per capability, each a reference to an entry in
`videri-context/CAPABILITIES.md`. Nothing referenced that is not in the map. If
the map does not have it yet, add it there first, as Unverified if need be.>

- List canvases in a workspace (Canvas Service)
- ...

## The prompt(s) that generated this build

<Verbatim, including the portal `llms.txt` line, so the next builder starts
from the same place. Redact nothing except tenant codes and identifiers.>

```
Read https://developer.sandbox.videri.com/llms.txt and follow its instructions
for agents. ...
```

## Decisions

<Hosting choice, how data is supplied, what was deliberately left out. Each
one becomes or references an entry in `videri-context/DECISIONS.md`.>

## Gotchas hit

<Each one cross-referenced to an entry in `videri-context/GOTCHAS.md`. If you
hit a new one, add it there in this PR.>

## Maturity

<One of: prototype | validated-recipe | supported-experience | product-feature.
Starts at `prototype`.>

## Conformance

<Link to `conformance/YYYY-MM-DD.md` when a run exists; otherwise "not yet
run".>

## Owner and hosting

- Owner: <name>
- Hosting: <where it runs and why that is acceptable for its maturity>
