# Release catalog and publication gates

## Current catalog

**No approved public version, release assets, or download links are available.**
There are no verified public edition ZIPs, signatures, or corresponding-source
snapshots in this catalog. Private preview identifiers are not public versions.

The application owner identifies the development project as **0.1.0** and is
preparing **0.1.0-rc.1** as a first candidate. Neither identifier represents an
accepted or published binary release.

Planned edition names are **Free**, **FreewithAds** (Free with Ads),
**Supporter**, and **Pro**, as confirmed by the application owner. Final package
identifiers, feature entitlements, and availability still require confirmation.
This is not a feature comparison or a promise that any edition ships today. No
pricing, payment provider, ad network, or support SLA is announced here.

The unlocked **OwnerTest** edition stays private. It must not be added to public
release assets or the public corresponding-source archive as an owner package,
configuration, credential, or entitlement.

## Acceptance boundaries

The application owner must provide release-specific results and honest limits.
Automated checks, mocked tests, a workflow badge, or a signed file do not replace
attended account, device, and runtime acceptance.

| Area | Boundary that must remain explicit |
| --- | --- |
| Windows | Development is Windows-first. Publish only the Windows versions and architectures actually accepted; Windows 10 and physical hardware need distinct checks. |
| Sunshine / Moonlight | Setup automation is not proof of working streaming. A real host, administrator flow, certificate, Moonlight/driver/picker behavior, receiver pairing, remote hosts, and the full attended owned-browser return flow require acceptance. |
| Controllers | Opt-in Xbox navigation is not universal controller support. A reported two-button navigation trap remains unreproduced; automated QML checks are not physical acceptance. Physical controller and remote compatibility require separate checks; browser authorization currently needs keyboard and mouse. |
| Live60 / high-frame-rate media | Ongoing-film Live60 interpolation is unaccepted and is not a shipped Pro promise. Saved-HFR conversion through a separately installed and licensed SVPcode companion is a distinct optional path, not verified in-app SVP automation. Exact release availability and device acceptance are pending. |
| Google Drive | External credentials, live streaming/download acceptance, and OAuth verification remain unfinished. A browser authorization callback is not complete account, library, playback, or revocation acceptance, and is not Google approval. Restricted-scope review, production configuration, privacy, retention, and deletion decisions remain separate gates. |
| Decoding and display hardware | Codec acceleration, HDR, and 4K depend on actual decoder, GPU, and rendering support. There is no universal old-PC compatibility guarantee. |
| Source and dependencies | A working player or passed build does not verify redistribution rights, exact corresponding source, or recipients' access. See [licensing and source](licensing-and-source.md). |

If an integration is not accepted, the final release must accurately describe
its restrictions or exclude/disable it, rather than advertise it as complete.
See the [canonical owner checklist](https://quasarli.github.io/cinedock/support/#release-steps)
and [development data-use notes](https://quasarli.github.io/cinedock/privacy/).

## Before any public release

1. The application owner confirms the concrete version, edition matrix,
   platform/architecture, acceptance results, and remaining documented limits.
   The coordinating owner explicitly approves that concrete release.
2. The release owner reviews an exact artifact inventory: filenames, byte sizes,
   SHA-256 digests, edition mapping, source revision/ref, dependency revisions,
   and corresponding-source archive digests. Nothing private or unrelated is
   included.
3. The [licensing and source-access gate](licensing-and-source.md) is resolved for
   those exact binaries, with complete source, dependency, build, patch, and
   applicable relink materials accessible to recipients.
4. Final ZIP bytes are signed by the approved private-source workflow.
   [Verification](verification.md) checks those bytes, certificate identity and
   issuer, source/ref/digest bindings, and the reviewed manifest. A workflow run
   alone is insufficient.
5. The application coordinator is the sole final asset publisher and publishes
   only the explicitly approved assets after these gates pass. This
   documentation repository does not dispatch signing or introduce a second
   signing pipeline. Do not create a tag, GitHub Release, or upload source/binaries
   before the concrete release is approved.
6. This catalog and the website are updated from the actual published asset
   inventory. Use genuine release and corresponding-source links; do not
   fabricate versioned URLs or advertise OwnerTest.

## Catalog update handoff

Keep the landing page at `README.md`, the release catalog in this file,
verification instructions at `docs/verification.md`, and source/license
instructions at `docs/licensing-and-source.md`.

For each approved release, record the exact version, release URL, supported
platforms, edition-to-asset mapping, sizes and SHA-256 digests, actual signature
bundle and verification-file links, public corresponding-source links, and
acceptance limitations. Obtain final names and verification commands from the
release owner; this document does not prescribe an unimplemented manifest or
bundle format.
