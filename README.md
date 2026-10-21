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
constraints block the PHP 8.4 graph: WKT 2.2 uses Doctrine Lexer 3 token objects;
FCM 1.0.1 admits Guzzle 7 without changing SDK source. Their original open PHP
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
