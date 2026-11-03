# Verifying a CineDock release

## Current status

**There is no approved public ZIP, signature, release manifest, or source archive
to verify yet.** These are verification requirements and a download-check
procedure, not evidence that a release has been signed.

The signing contract is now committed in the private source, but is not yet
integrated into the final release source. Parser/tests, cryptographic checks,
and an actual signing-workflow run remain unvalidated. No Sigstore verification
command has been executed successfully. The owner must confirm the integrated
implementation and tested commands before executable Sigstore instructions are
published here. No sample signatures or example digests are release proof.

## Committed signing contract (not validated)

The committed private-source path is `.github/workflows/release-signing.yml`
with a Python standard-library helper and **Cosign v3.1.4**. That is the
committed version pin, not a claim that a verifier was installed or tested here.
The final tested contract and official verifier-download checksum must be
confirmed before use.

- Each final ZIP is signed directly with `sign-blob`; its matching new-format
  Sigstore bundle appends `.sigstore.json` to the complete ZIP filename.
  An older local-key in-toto digest attestation is not a substitute.
- Signed `ReleaseSigning.input.json` binds the immutable source revision,
  full source version, candidate/prerelease status, approved four-edition matrix,
  review record, every ZIP's hash, size, and complete member hashes, and
  digest-bound approval for the exact public signing metadata.
- `ReleaseSigning.result.json` and its `.sigstore.json` bundle bind the input
  plan digest, producer run/artifact ID and transport digest, signing run and
  attempt, signer/issuer/source, and retained plan, review, ZIP, and bundle
  hashes. The result manifest and its own bundle are explicit self-reference
  exceptions to their own inventory, not exemptions from signature verification.

The planned verifier checks the signed result first, then its full referenced
inventory and individual ZIP signatures. Result retention is initially in
private Actions artifacts; that is **not** a public download or recipient-access
solution. Public release verification materials still need approved publication.
This contract is not independently authenticated build provenance. A signing
worker commit is not the final signer/release commit: the application owner
must integrate the edition/version source and signing changes, then provide the
final immutable source revision and digests. Existing pending private staging
ZIPs cannot become approved candidates merely by signing them.

All four public IDs, `Free`, `FreewithAds`, `Supporter`, and `Pro`, are required
by the candidate signing contract; `OwnerTest` is excluded. Each ZIP must contain
complete `EditionInfo.json` captured from that actual candidate executable's
`--edition-info` output, matching the reviewed full version, edition ID,
`buildLabel`, and boolean entitlements. The packaging owner must execute and
cross-check the candidate binary and bind that capture to its hashes. The
signer does not execute downloaded applications.

## Approved certificate identity

Only the following exact workflow identity and issuer have been approved for
this release lane:

```text
Certificate identity:
https://github.com/QuasarLI/CineDock/.github/workflows/release-signing.yml@refs/heads/main

OIDC issuer:
https://token.actions.githubusercontent.com
```

Use exact identity and issuer matching, not a wildcard, substring, arbitrary
GitHub workflow, or a different branch. The approval allows the signing
metadata for that private-source workflow to be public; it is not itself a
signature, endorsement of arbitrary future bytes, or proof of acceptance.

The `main` workflow identity does not identify a unique source commit. The
reviewed release metadata must also bind the concrete source revision/ref,
artifact digests, and corresponding-source materials. Do not infer a source
snapshot from a branch name alone.

In addition to the exact identity and issuer, the committed verifier constrains
the GitHub workflow repository to `QuasarLI/CineDock`, ref to `refs/heads/main`,
trigger to `workflow_dispatch`, and workflow SHA to the final reviewed
40-character commit. It also requires signed-timestamp verification and does
not bypass transparency-log or signed-certificate-timestamp checks. These are
requirements of the unvalidated path, not a tested command recipe.

## Required verification sequence

Once an approved release exists:

1. Start from the release linked in the [catalog](releases.md), not a private
   preview, forwarded archive, or guessed URL. Obtain the exact edition ZIP,
   reviewed manifest/checksum file, its matching signature material, and public
   corresponding-source materials. Use the actual asset names and formats
   recorded for that release.
2. Before extracting or running the ZIP, use the release owner's confirmed
   verifier and tested command to authenticate the signed result manifest first,
   with the exact certificate identity, issuer, source commit, and additional
   workflow constraints above. Then verify the signed input plan and the full
   referenced inventory against that result. A checksum copied alongside an
   untrusted file is not independent proof of authenticity.
3. Calculate the ZIP's SHA-256 digest and compare it with its exact asset entry
   in the authenticated, reviewed inventory. Check edition, version, platform,
   filename, size, and required member inventory. Verify the **downloaded final
   ZIP bytes** with its matching signature bundle, the same exact certificate
   identity and issuer, and required workflow constraints. Require all
   cryptographic, certificate, signed-timestamp, and applicable transparency-log
   checks. Verifying an executable inside the ZIP, an unsigned checksum text, or
   a different archive does not verify the ZIP.
4. Validate any claimed build provenance/attestation separately using the
   implemented path.
   Match its artifact subject digest to the downloaded ZIP and the reviewed
   manifest; match its source repository, concrete revision/ref, and
   corresponding-source/dependency digests to the release approval. A direct
   ZIP signature alone does not establish those source bindings. If a binding
   is missing or unverified, or required source materials are accessible only
   through a private repository rather than the public release snapshot,
   source verification is incomplete.
5. Confirm the public corresponding-source links actually work and cover the
   exact distributed binaries under the [source-access gate](licensing-and-source.md).
   Source availability and license compliance are separate from signature
   verification.

If required material is missing or any check fails, stop: do not run the
package or treat it as an approved release. Report the mismatch through
[CineDock support](https://quasarli.github.io/cinedock/support/) without sending
credentials, private previews, personal media, or unredacted logs.

### SHA-256 on Windows

This PowerShell command computes a local digest only. Select the actual
downloaded ZIP when prompted; it does not download, extract, run, or authenticate
the package.

```powershell
$zipPath = (Resolve-Path -LiteralPath (Read-Host 'Full path to downloaded release ZIP')).Path
Get-FileHash -LiteralPath $zipPath -Algorithm SHA256 |
    Format-List Path, Algorithm, Hash
```

Compare the displayed digest with the exact manifest entry, ignoring letter
case only. No expected digest exists until a concrete release is reviewed.

## What signatures do not establish

Sigstore verification can bind bytes to a certificate identity and provide
verifiable signing evidence according to the implemented scheme. It is not a
malware audit, feature/device acceptance, privacy approval, licensing clearance,
or a guarantee that a build is reproducible.

**Sigstore is not Windows Authenticode.** A verified ZIP does not imply its
executables have an Authenticode signature or a trusted Windows publisher
reputation, and does not guarantee SmartScreen acceptance. Do not disable
SmartScreen, antivirus, or other system protections to bypass a warning.
