# PIPE-10061 canary

Harmless stand-ins for the URL orb SSRF: public files with a marker,
`PIPE-10061-CANARY-bca7c6ad`, that must never appear in a compile error.

* `scalar.yml`: plain text. Legacy quoted the whole body as schema `INPUT:`.
* `not-yaml.yml`: not YAML. Legacy quoted snakeyaml's excerpt of the line.
* `../.circleci/config.yml`: uses both. Pushing it triggers a pipeline.
* `redirect-config.yml`: same body reached through an httpbin redirect (PR 2).

URL orb allow-list entry for the org:
`https://raw.githubusercontent.com/parkuman/learning-circleci/main/canary/`
(plus `https://httpbin.org/` for the redirect check)

Check: `circleci config validate --org <org-uuid> --json .circleci/config.yml`
