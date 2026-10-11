# Download Sources Registry

Record download experience. After each successful datasheet or footprint download, record the exact device/package, source, URL, and verification date. Recheck that a prior record still matches the required revision, package, and EDA format before reusing it.

## Usage Rules

1. Before downloading, consult this file. A prior record is a useful starting point, not proof that the current file is valid; verify the exact model, package, revision, and format.
2. After a successful download, append the new record under the corresponding category.
3. If a previously recorded source becomes invalid, annotate the failure date and add a new usable source.
4. For datasheets, use the manufacturer's current document first; use an authorized-distributor attachment to cross-check. Aggregators are discovery leads only and must be checked against an authoritative copy. For footprints, prefer manufacturer CAD or a verified official/authorized library; cross-check third-party library dimensions against the package drawing.
5. Record format: `| Device model / package | Source site | URL | Document revision / format | Verification date |`

## Datasheet Download Records

| Device model / package | Source site | URL | Document revision | Verification date |
|------------------------|-------------|-----|-------------------|-------------------|
| (Append after successful download) | | | | |

## Footprint Download Records

| Device model / package | Source site | Format | URL | Verification date |
|------------------------|-------------|--------|-----|-------------------|
| (Append after successful download) | | | | |

## Known Failed Sources (avoid repeated attempts)

| Device / Manufacturer | Failed source | Failure reason | Record date |
|-----------------------|---------------|----------------|-------------|
| (Recorded after download failure) | | | |
