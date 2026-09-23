# Security Policy

CYC (ClaimYourConnection) runs as a Windows Service with administrative
privileges and serves a local web dashboard, so a bug in it is worth
reporting properly rather than in a public issue.

## Supported versions

Only the most recent release is supported. There are no maintenance branches
and no backports: fixes go into the next version, which the in-app updater
offers to every installation. The current version is the newest release in
this repository.

| Version         | Supported |
| --------------- | --------- |
| Latest release  | yes       |
| Anything older  | no        |

## Reporting a vulnerability

Report privately through GitHub's private vulnerability reporting on this
repository: **Security → Advisories → Report a vulnerability**, or directly at
<https://github.com/BAEM1337/netwatch-releases/security/advisories/new>.
That opens a thread only you and the maintainer can read. You need a GitHub
account for it. English or German are both fine.

Please do not open a public issue or a pull request for a vulnerability
before it is fixed, and please do not post it anywhere public in the
meantime.

Useful to include:

- the version (About page in the dashboard, or the MSI's `ProductVersion`),
- Windows version and whether the dashboard was reachable on the LAN
  (LAN Access on or off),
- what an attacker would have to be able to do to reach the bug: another
  program on the same machine, another machine on the same network, a
  website the user happens to have open,
- how to reproduce it.

If a report turns out to be valid, the fix ships in the next release and the
advisory is published once that release is out.

## Out of scope

- Anything that requires administrator rights on the machine already: the
  service runs as `LocalSystem` by design, and an administrator can replace
  it outright.
- The dashboard being reachable from the local network while LAN Access is
  deliberately switched on. That is the feature; the pairing and rights model
  around it is not.

## Release integrity

Released MSIs are published with a SHA-256 in `update-manifest.json` next to
them, and the in-app updater refuses a download whose hash does not match.
The MSI itself is **not Authenticode-signed**, so Windows SmartScreen warns on
a manual install. Until it is, the SHA-256 on the release is the thing to
check.
