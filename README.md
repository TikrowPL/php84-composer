# Tikrow PHP 8.4 compatibility repository

Pinned Composer metadata for Tikrow's PHP 8.4 migration. Each entry in
`forks.json` identifies its original revision and the reviewed corporate fork
commit. Package names and existing release versions are preserved; source and
dist references identify the compatibility changes unambiguously.

Use this repository at an immutable Git commit URL. Commit `composer.lock` in
the consuming application. Do not track this repository's moving default branch
in a release build.

Maintained packages with a usable official PHP 8.4 release remain upstream.
Abandoned status alone does not justify a fork. Legacy Zend requirements in
retained forks are mapped to Laminas; runtime namespace aliases remain provided
by the bridge. TwbBundle retains Serializer 2.x and admits Form 3. Humus supports
the verified Symfony Console 6/7 command-registration paths.

Two explicitly approved exceptions preserve application APIs where dependency
constraints block the PHP 8.4 graph: WKT 2.2 accepts Doctrine Lexer 2.1/3 token
objects; FCM 1.0.1 admits Guzzle 7 without changing SDK source. The application
selects official Lexer 2.1 to preserve unmodified GeoParser 2.2.1 conversion. Their original open PHP
minimums already admit PHP 8.4. Mocked FCM transport tests do not establish live
Google endpoint delivery.

Two entries are unchanged upstream pins, **not corporate forks**:
`phpoffice/phpspreadsheet` and `creof/doctrine2-spatial`. Their existing dev
revisions are preserved to avoid an unrelated migration of moving branches.

Verification includes PHP 8.4 and PHP 8.0 comparison checks, class loading and
focused behavior tests. ProxyManager 2.14.1 is tested with official Laminas Code
4.17 on PHP 8.4. Original suites with obsolete test harnesses, missing backend
extensions or OpenSSL differences are not represented as fully passing suites.
Nine obsolete cache adapters are retained for provenance but are not selected by
the application's Cache 3 dependency graph. Their optional backends are not
certified by lint or reflection checks.

This repository establishes dependency provenance, not production acceptance or
proof that a PHP runtime contains a particular security fix. Application tests,
deployment validation and the final patched PHP image must be checked separately.

## Office version lines

The `php84-office-20261021` branch extends the immutable Tikrow registry base
`ea114c7b928beb946fae093ac80e1c904771f9e1` with exactly 20 Office package
versions. Original package entries and `forks.json` remain unchanged.
`office-forks.json` records each exact Office upstream source base, corporate
version-line branch and compatibility commit. Existing Office release versions
and dependency metadata are preserved; their PHP constraints additionally admit
PHP 8.4. Source and dist references identify real published corporate commits.

Seventeen forks change PHP metadata only. RPC resolves `self` and `parent`
parameter types; Crypt normalizes a null Hybrid key ID to the historical empty
ID; Log retains priority 2048 without evaluating deprecated `E_STRICT`.
Native PHP 8.4.26 source lint, class loading and focused behavior probes pass
in an isolated dependency harness. The three original source behaviors were
reproduced before their fixes. This is dependency evidence; the consuming
Office root graph and application still require independent acceptance.

## Office runtime deprecation repair

Two additional Office version lines retain the exact stable upstream bases:
`laminas/laminas-mvc` 3.8.0 and `php-ai/php-ml` 0.10.0. Their existing PHP and
dependency constraints already admit PHP 8.4 and remain unchanged. MVC makes
the middleware route-match parameter explicitly nullable. PHP-ML replaces
deprecated string interpolation, including property interpolation that formerly
recursed when rendering terminal leaves or trained stumps. PHP-ML's corporate
repository imports its public GitLab upstream history; MVC is a GitHub fork.

All 65 previously registered version objects remain byte-identical. Both new
source/dist references identify published compatibility commits, recorded in
`office-forks.json`. Native PHP 8.4.27 lint covers all 223 source files with no
diagnostics, compared with 13 deprecations at the original stable bases. Focused
and adjacent behavior checks pass: 22 tests and 57 assertions, also executed
against downloaded corporate archives. This remains isolated dependency proof;
the consuming Office application needs its own integration acceptance.
