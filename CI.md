# CI runner contract

The Tests workflow uses Boat for its Linux lane and keeps Windows on
`windows-latest`. The logical `matrix.os` values stay unchanged so check names
remain `test (ubuntu-latest)` and `test (windows-latest)`.

Both lanes still use Node 24, `npm ci --ignore-scripts`, and all unit,
integration and E2E commands. Type stripping is not a TypeScript diagnostic check.

The manual Release workflow stays on `ubuntu-latest`. npm trusted publishing
supports GitHub-hosted runners, not self-hosted runners such as Boat. This is an
explicit compatibility exception, not a billing workaround. The existing
permissions, registry setup, full-suite prerequisite and
`npm publish --provenance` remain unchanged. No long-lived token is added.
See [npm trusted publishing](https://docs.npmjs.com/trusted-publishers/).

Public Boat execution policy is account-level and separate from workflow source.
No settings, credentials, billing or workflow dispatch are changed here. Provider
billing failures are not fixed by changing a runner label.

The npm-cache proposal remains gated on fork/upstream policy and measured restore
behavior. No dependency versions, lifecycle policy or cache behavior changed.
