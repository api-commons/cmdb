# ITSM Change and CMDB

The common ITSM vocabulary beyond the ticket -- the configuration items a CMDB tracks, the change requests that alter them and the problems that explain recurring incidents -- distilled from the APIs that already exist. Incidents and service requests belong to the help-desk context. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged ITSM, IT Service Management, CMDB, Change Management, Problem Management, ITIL, Service Management, IT Operations in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
| Concept | Expose it | Readable schema | Core properties (share) | Collection named |
| --- | ---: | ---: | --- | --- |
| change_request | 4 | 3 | description 100%, name 100% | changes 3, change 1 |

Cohort: 32 providers with harvested OpenAPI, 4 crosswalks. Of the providers exposing a change_request: 75% create, 75% list, 75% fetch, 75% update, 25% delete. Generated 2026-11-11 by build.py.
<!-- /commons:summary -->

Shares are of the providers with a readable resource schema for that concept. The
extended tier and the long tail of every concept are in [profile.yml](profile.yml).

## What the measurement shows

- ITSM beyond the ticket is nearly invisible as OpenAPI (32 providers, 4 mapped). The market's largest platform exposes every ITSM record through a generic table API (`/table/{tableName}`), so configuration items, changes and problems have no resource paths to measure.
- A change request agrees on its title and description where it is a resource (3 providers): too few to say more.

## Artifacts

- [openapi.yml](openapi.yml) -- OpenAPI 3.1 of the shared operations. No one serves it; it
  is the shape to map to. Lints clean against the
  [naming ruleset](https://github.com/api-commons/schema-commons/blob/main/ruleset/schema-commons-naming.yaml).
- [schema/](schema) -- JSON Schema 2020-12 per concept; each property carries
  `x-commons-tier`, `x-commons-share`, `x-commons-providers` and the spellings seen.
- [crosswalk/](crosswalk) -- one per provider, common name -> their name, with the harvested
  spec and operations each mapping was read from.
- [adopters.yml](adopters.yml) -- who exposes which concept, linked to their APIs.io page.
- [concepts.yml](concepts.yml) -- the only hand-written input: concepts, path segments and
  their qualifiers, aliases, reviewed exclusions, merged duplicates, and the decisions below.
- [census/](census) -- the cohort and the raw census the profile is built from.

## Decisions

These are calls, not measurements, recorded so they can be revisited as the method matures.

- Incidents and service requests stay in help desk; this context keeps changes, problems and the CMDB.
- Configuration items and problems were measured and dropped. A table-API reader -- one that reads a provider's table schemas as resources -- would recover them; it is recorded for the tooling backlog.

## Rebuild

```bash
../schema-commons/scripts/run.sh .
```

## License

Artifacts CC BY-NC-SA 4.0 ([LICENSE](LICENSE)); code Apache 2.0 ([LICENSE-CODE](LICENSE-CODE)).
