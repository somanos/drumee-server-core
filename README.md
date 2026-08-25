# @drumee/server-core

The foundational middleware library for [Drumee](https://drumee.com) back-end
services.

[![npm](https://img.shields.io/npm/v/@drumee/server-core)](https://www.npmjs.com/package/@drumee/server-core)

```console
npm i @drumee/server-core
```

---

## What it is

`server-core` owns the parts every Drumee back-end service needs:

- the HTTP request and response lifecycle
- session management
- authentication and authorisation — the bitwise **ACL** model
- the **meta filesystem** (MFS)
- media conversion

It is a **library only**. It has no server entry point of its own: consuming
services instantiate the pipeline and supply the business logic. The main
consumer is [server-team](https://github.com/drumee/server-team); others include
`onboarding-server` and `sandbox-server`.

## Documentation

**`docs/ARCHITECTURE.md` in this repository is the authoritative reference.** It
covers hub multi-tenancy, the full request pipeline, session states, the bitwise
ACL model, the MFS node layout, the output envelope and the exception-to-HTTP
mapping. Read it before making non-trivial changes, and keep it updated
alongside the code.

Platform documentation: [docs.drumee.com](https://docs.drumee.com/introduction/).

## Layout

| Path | What it holds |
|---|---|
| `lib/` | The library itself; `lib/index.js` is the entry point |
| `schemas/` | Schema helpers used by the core |
| `bin/` | Maintenance scripts |
| `docs/` | Architecture reference |

## Tests

```console
npm test               # runs test:modules, test:acl and test:db in sequence
npm run test:modules   # instantiates MariaDB, cache, redis store, logger, offline
npm run test:db        # SELECT 1 and SHOW TABLES against the yp database
```

These are **smoke tests against a live environment**, not a unit-test harness —
there is no test runner, no linter and no build step. A failure usually means
the environment is not up rather than that the code is broken, so check the
environment before chasing a code change.

## Built on

[`@drumee/server-essentials`](https://github.com/drumee/server-essentials) —
database, cache, logging, mail and template primitives.

## Contributing

See the org [CONTRIBUTING guide](https://github.com/drumee/.github/blob/main/CONTRIBUTING.md).
Questions: [Discussions](https://github.com/orgs/drumee/discussions).

## License

AGPL-3.0 — see [LICENSE](LICENSE).
