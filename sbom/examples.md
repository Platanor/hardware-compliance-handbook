**Worked examples — the same device, two SBOM formats**

**Everything below is invented for illustration.** The device name, component names and versions, hashes, checksums, and the CVE ID in the VEX example are all fictional placeholders — none of it describes a real product, and the CVE ID is not a real advisory. The structure of each document was checked against the official CycloneDX 1.6/1.7 JSON schema and standard SPDX 2.3 JSON usage, but these are hand-built teaching examples, not output from running an SBOM tool against real firmware. For real, complete, tool-generated examples, use the format projects' own repositories: [CycloneDX/bom-examples](https://github.com/CycloneDX/bom-examples) and the [SPDX examples page](https://spdx.dev/use/examples/).

The hypothetical device is a small connected gateway ("example-iot-gateway", v2.4.0) with three third-party components: **mbedTLS** 3.6.0 (a TLS/crypto library, Apache-2.0), **FreeRTOS** 10.6.2 (a real-time OS kernel, MIT), and **lwIP** 2.2.0 (a lightweight TCP/IP stack, BSD-3-Clause). Both examples describe exactly the same four things (the device plus its three components) so the two formats can be compared directly.

**CycloneDX 1.7 (JSON)**

```json
{
  "bomFormat": "CycloneDX",
  "specVersion": "1.7",
  "serialNumber": "urn:uuid:3e671687-395b-41f5-a30f-a58921a69b79",
  "version": 1,
  "metadata": {
    "timestamp": "2026-09-15T00:00:00Z",
    "tools": {
      "components": [
        { "type": "application", "name": "cdxgen" }
      ]
    },
    "manufacturer": { "name": "Example IoT Co" },
    "component": {
      "type": "device",
      "bom-ref": "example-iot-gateway@2.4.0",
      "name": "example-iot-gateway",
      "version": "2.4.0"
    }
  },
  "components": [
    {
      "type": "library",
      "bom-ref": "mbedtls@3.6.0",
      "name": "mbedtls",
      "version": "3.6.0",
      "purl": "pkg:generic/mbedtls@3.6.0",
      "licenses": [{ "license": { "id": "Apache-2.0" } }],
      "hashes": [{ "alg": "SHA-256", "content": "4022437811b7b98f9dee6030fcfa7161c463d597a891aee87e1780ef3fed144f" }]
    },
    {
      "type": "library",
      "bom-ref": "freertos@10.6.2",
      "name": "FreeRTOS",
      "version": "10.6.2",
      "purl": "pkg:generic/freertos@10.6.2",
      "licenses": [{ "license": { "id": "MIT" } }]
    },
    {
      "type": "library",
      "bom-ref": "lwip@2.2.0",
      "name": "lwIP",
      "version": "2.2.0",
      "purl": "pkg:generic/lwip@2.2.0",
      "licenses": [{ "license": { "id": "BSD-3-Clause" } }]
    }
  ],
  "dependencies": [
    {
      "ref": "example-iot-gateway@2.4.0",
      "dependsOn": ["mbedtls@3.6.0", "freertos@10.6.2", "lwip@2.2.0"]
    }
  ]
}
```

**The same file, with a CycloneDX VEX statement added**

This extends the document above with a `vulnerabilities` array — the CycloneDX VEX flavor described in [`vex.md`](vex.md), traveling as part of the same SBOM file rather than as a separate document. Shown here as its own self-contained JSON object (so the block below is valid JSON on its own if you copy just it) rather than as a bare fragment — in the actual file, `vulnerabilities` is a sibling key of `metadata`, `components`, and `dependencies` above, not a nested object.

```json
{
  "vulnerabilities": [
    {
      "bom-ref": "vuln-1",
      "id": "CVE-2024-99999",
      "source": {
        "name": "NVD",
        "url": "https://nvd.nist.gov/vuln/detail/CVE-2024-99999"
      },
      "ratings": [
        {
          "source": { "name": "NVD" },
          "score": 5.3,
          "severity": "medium",
          "method": "CVSSv31",
          "vector": "CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N"
        }
      ],
      "affects": [
        { "ref": "mbedtls@3.6.0" }
      ],
      "analysis": {
        "state": "not_affected",
        "justification": "code_not_reachable",
        "detail": "The vulnerable code path is in mbedTLS's RSA-PSS padding routine, which this firmware does not call - only AES-CBC and ECDHE are used for the TLS connection to the cloud backend."
      }
    }
  ]
}
```

Note the vocabulary: `state: "not_affected"` and `justification: "code_not_reachable"` are CycloneDX's own values (`analysis.state` and `analysis.justification`), not the CISA VEX vocabulary (`not_affected` / `affected` / `fixed` / `under_investigation`) used by OpenVEX and CSAF VEX — see the vocabulary mismatch note in [`vex.md`](vex.md). But the *justification* concept isn't CycloneDX-specific - it exists under different label names in the other two as well: OpenVEX requires either a `justification` label or a free-form `impact_statement` for any `not_affected` status, and strongly recommends the label (five fixed values) over the free-form text, which it says breaks automation, and its `vulnerable_code_not_in_execute_path` label is close to CycloneDX's `code_not_reachable` used here; CSAF VEX carries the same idea through its `flags` mechanism, using the same underlying label catalog as OpenVEX (both trace back to CISA's 2022 *VEX Status Justifications* document). What differs across the three is the label spelling, not whether the concept of "why not affected" exists at all.

**SPDX 2.3 (JSON)**

The same device and components, in the format most current SBOM tooling (e.g. Syft's `spdx-json` output) actually emits by default.

```json
{
  "spdxVersion": "SPDX-2.3",
  "dataLicense": "CC0-1.0",
  "SPDXID": "SPDXRef-DOCUMENT",
  "name": "example-iot-gateway-2.4.0",
  "documentNamespace": "https://example.com/spdx/example-iot-gateway-2.4.0-3e671687",
  "creationInfo": {
    "created": "2026-09-15T00:00:00Z",
    "creators": ["Tool: syft-1.x", "Organization: Example IoT Co"]
  },
  "packages": [
    {
      "SPDXID": "SPDXRef-Package-example-iot-gateway",
      "name": "example-iot-gateway",
      "versionInfo": "2.4.0",
      "downloadLocation": "NOASSERTION",
      "supplier": "Organization: Example IoT Co",
      "licenseConcluded": "NOASSERTION",
      "licenseDeclared": "NOASSERTION",
      "filesAnalyzed": false
    },
    {
      "SPDXID": "SPDXRef-Package-mbedtls",
      "name": "mbedtls",
      "versionInfo": "3.6.0",
      "downloadLocation": "https://github.com/Mbed-TLS/mbedtls",
      "licenseConcluded": "Apache-2.0",
      "licenseDeclared": "Apache-2.0",
      "externalRefs": [
        { "referenceCategory": "PACKAGE-MANAGER", "referenceType": "purl", "referenceLocator": "pkg:generic/mbedtls@3.6.0" }
      ],
      "checksums": [
        { "algorithm": "SHA256", "checksumValue": "4022437811b7b98f9dee6030fcfa7161c463d597a891aee87e1780ef3fed144f" }
      ],
      "filesAnalyzed": false
    },
    {
      "SPDXID": "SPDXRef-Package-freertos",
      "name": "FreeRTOS",
      "versionInfo": "10.6.2",
      "downloadLocation": "https://github.com/FreeRTOS/FreeRTOS-Kernel",
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "externalRefs": [
        { "referenceCategory": "PACKAGE-MANAGER", "referenceType": "purl", "referenceLocator": "pkg:generic/freertos@10.6.2" }
      ],
      "filesAnalyzed": false
    },
    {
      "SPDXID": "SPDXRef-Package-lwip",
      "name": "lwIP",
      "versionInfo": "2.2.0",
      "downloadLocation": "https://savannah.nongnu.org/projects/lwip/",
      "licenseConcluded": "BSD-3-Clause",
      "licenseDeclared": "BSD-3-Clause",
      "externalRefs": [
        { "referenceCategory": "PACKAGE-MANAGER", "referenceType": "purl", "referenceLocator": "pkg:generic/lwip@2.2.0" }
      ],
      "filesAnalyzed": false
    }
  ],
  "relationships": [
    { "spdxElementId": "SPDXRef-DOCUMENT", "relationshipType": "DESCRIBES", "relatedSpdxElement": "SPDXRef-Package-example-iot-gateway" },
    { "spdxElementId": "SPDXRef-Package-example-iot-gateway", "relationshipType": "DEPENDS_ON", "relatedSpdxElement": "SPDXRef-Package-mbedtls" },
    { "spdxElementId": "SPDXRef-Package-example-iot-gateway", "relationshipType": "DEPENDS_ON", "relatedSpdxElement": "SPDXRef-Package-freertos" },
    { "spdxElementId": "SPDXRef-Package-example-iot-gateway", "relationshipType": "DEPENDS_ON", "relatedSpdxElement": "SPDXRef-Package-lwip" }
  ]
}
```

**Same data, different shape — what to notice**

- **How the product itself is represented.** CycloneDX gives the device its own slot in `metadata.component`, separate from the `components` array that lists everything *inside* it. SPDX has no separate slot for this — the device is just another entry in `packages`, and a `DESCRIBES` relationship from `SPDXRef-DOCUMENT` is what marks it as the thing the document is actually about.
- **How dependencies are expressed.** CycloneDX uses a single `dependencies` array of `{ref, dependsOn}` edges, keyed by `bom-ref`. SPDX has no dedicated dependency array at all — every relationship, including "depends on," is one more entry in the general-purpose `relationships` array, using `relationshipType: "DEPENDS_ON"`.
- **How external identifiers attach.** CycloneDX puts `purl` directly on the component object as a field. SPDX has no `purl` field on a package - it goes inside `externalRefs`, an array built for several kinds of reference, with `referenceType: "purl"` picking out this one.
- **Vulnerabilities and VEX.** CycloneDX has a native `vulnerabilities` array, shown above - a VEX statement and the SBOM it's about can be one file. SPDX 2.3 has no equivalent array; SPDX's security-focused fields live in the separate `security` profile introduced in SPDX 3.0 (see [`formats-and-specifications.md`](formats-and-specifications.md)), not in the 2.3 structure shown here.
- **Licensing.** CycloneDX nests license data one level down (`licenses: [{license: {id: ...}}]`, an array because a component can carry more than one). SPDX puts `licenseConcluded` and `licenseDeclared` directly on the package as plain strings - and deliberately distinguishes the two: `licenseDeclared` is what the component's own metadata claims, `licenseConcluded` is what the person or tool building the SBOM actually determined after checking, which is why `NOASSERTION` is a valid, honest answer for either field.

**Source:** structure checked against the [CycloneDX 1.6/1.7 JSON schema](https://cyclonedx.org/docs/1.6/json/) and standard SPDX 2.3 JSON usage as documented at [spdx.dev](https://spdx.dev/use/examples/); see [`formats-and-specifications.md`](formats-and-specifications.md) and [`vex.md`](vex.md) for the specifications themselves. CycloneDX and SPDX are independently governed, trademarked specifications - these examples are illustrative and hand-built, not reproduced from either project's own example repository.
