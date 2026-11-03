# Licensing and corresponding source

## Current distribution gate

**Public binaries remain blocked.** The selected libmpv/FFmpeg build has
GPLv3-path components; it has not been verified as LGPL-only. Exact complete
corresponding source, dependency/build/patch materials, applicable relink
requirements, and recipients' source access must be resolved for the actual
combined binary before publication.

Notices alone, an upstream homepage, a private repository link, a successful
build, or a signature do not close this gate. This documentation is not a claim
that legal review or redistribution clearance is complete.

## License scope

CineDock-owned source retains its MIT notice, `Copyright(c)2026QuasarLabs`.
The original notice and license text must accompany the relevant source.
Third-party components retain their own licenses, copyright notices, and
distribution obligations.

The CineDock-owned source notice is **not** an MIT-only designation for the
combined application, libmpv/FFmpeg, every bundled binary, or all repository
content. Determine the obligations of the exact selected components and their
combination; do not relabel GPL-path components as MIT or assume LGPL relinking
alone resolves a GPL-path distribution.

Separately installed optional integrations and companions also have their own
licenses and redistribution rules. Referencing Sunshine, Moonlight, or SVPcode
does not grant permission to bundle them or remove their license requirements.
The release owner must confirm the final notices and distribution scope.

## Required public source materials

The approved publication plan is to keep ongoing development private while
publishing complete required corresponding-source snapshots, including
**CineDock code**, dependencies, and build scripts. A release must give its
recipients real access to the exact required materials, not merely promise
private access or direct them to the private development repository.

Before publication, the release owner must establish and review:

1. The source revision and release/ref binding for every distributed binary,
   including the matching CineDock source and the actual libmpv/FFmpeg sources,
   enabled components, dependency versions, modifications, and patches.
2. Complete required build/configuration scripts, dependency acquisition and
   version information, relevant toolchain details, and instructions sufficient
   to build the covered software. Resolve applicable relink materials and
   installation information rather than assuming a source tree alone suffices.
3. The exact license texts, copyright notices, third-party inventory, and
   source-distribution obligations for the selected binary combination.
4. Sanitized source archives/materials and a reviewed inventory of their
   filenames and SHA-256 digests, tied to the binary release manifest.
5. Working public recipient-access links and any required delivery terms or
   continued source availability. A maintainer's authenticated access to a
   private repository does not test recipient access.

When approved materials exist, the [release catalog](releases.md) will link them
alongside the exact binaries, notices, and verification files. **No approved
corresponding-source snapshot or final source-archive link is available yet.**

## Public-source sanitization boundary

Publish the required code and build materials, not a copy of the owner's
working directory. Exclude secrets, credentials, signing tokens, account/client
configuration containing private data, owner profiles, entitlement material,
browser profiles, personal media, private diagnostics, and unrelated projects.
OwnerTest packages and owner-specific configuration remain private.

Sanitization must not silently omit code, dependency materials, patches, or
build scripts required for the distributed software. If something required
cannot safely or lawfully be supplied, resolve it before releasing the binary;
do not use sanitization as a substitute for corresponding-source completeness.

For current product, support, and data-use boundaries, see the
[official product page](https://quasarli.github.io/cinedock/),
[support checklist](https://quasarli.github.io/cinedock/support/#release-steps),
and [development data-use notes](https://quasarli.github.io/cinedock/privacy/).
