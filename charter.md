# Secure Patterns for Internet CrEdentials (SPICE) at IETF - Proposed Charter

## Introduction

Digital credentials are essential to identity, access control, and digitization use cases that are part of modernization efforts, such as digital licenses or certificates of origin.
COSE and JOSE provide building blocks, such as identifiers and public and private claim structures, which enable interoperability and cryptographic agility, but which require profiling to render digitization easy, unambiguous and consistent.
There are various ways to combine identifiers, key material, signatures, and attributes to create credentials, which often prevents interoperabtility from spanning across data silos or cross use cases.
This lack of interoperabilty leads to increased implementation costs, attack surface, and harms adoption, which prevents digitzation from being deployed successfully.
SPICE aligns the capabilities of JOSE and COSE to support modern cryptographic capabilities, such as selective disclosure or unlinkablilty, consistent identity attribute semantics across representations, and Internet-scale discoverability of identifiers and cryptography capabilities.

## Background

Foundational building blocks have been developed with BBS Signatures, RSA Blind Signatures, Verifiable Random Functions, or other Selective-Disclosure and data minimization techniques.
While these techniques are being incorporated into JOSE and OAuth-based protocols, the integration into protocols using CBOR/COSE is, however, missing. 
The SPICE WG aims to close this gap by enabling the secure and privacy-friendly use of CBOR-based credentials for use cases that go beyond constrained Internet of Things devices. Envisioned use cases where these credentials will be used include education, digital wallets, business-to-business supply chain interactions, and digital media.

### A note on terminology (Note: context to be removed from charter upon adoption)

The term "digital credential" is a generic industry term, which does not imply a specific serialization. 

The term "verifiable credential" is a term which can imply, for example, JSON, JSON-LD or mDoc serialization.

In the W3C, "verifiable credential" implies specific JSON-LD based media types.

A "digital credential" is a "W3C Verifiable Credential" when it secures a JSON claimset that conforms to the W3C Technical Recommendation.

A "digital credential" is an "OAUTH Verifiable Credential" when it secures a JSON claimset that conforms to the requirements of documents developed by the OAUTH WG. 

A "digital credential" might be a "mDoc verifiable credential", in other specifications.

As a result, the SPICE WG avoids use the term "verifiable credential" in this charter text, as it is not intended to draw exclusive association to these existing serializations.

## Key Design Properties of Digital Credentials

- Unlinkability (preventing tracking while proving attributes / capabilities)
- Selective Disclosure (supporting user agency, data minimization, redaction)
- Authenticity (ensuring information is trustworthy and can be authenticated)
- Integrity (ensuring tampering with information is always evident)
- Confidentiality (ensuring information is protected from unauthorized access)
- Availability (efficiently information processing, minimizing data in flight, reducing carbon cost for storage and transmission, and supporting offline / paper credential use cases)
- Semantic interchangeability (ensuring terms are understood and used consistently, in a global or local context)
- Usability and Feasibility (the core operations must be easy to understand and use, and possible to integrate with existing platforms)
- Accountability (what format and protocol considerations can help mitigate abusive or excessive requests for credential presentation?  What mitigates abuse by issuers?)

## Goals

Coordination with CFRG, RATS, OAuth, JOSE, COSE, and SCITT are important to ensure that the latest work at IETF is leveraged. Feedback from experts in other IETF working groups is gathered in the SPICE WG without creating fragments of credential work spread across several existing places in the IETF. Additionally, the SPICE WG will coordinate with other SDOs, such as ISO or W3C, on data model elements needed to support existing credential use cases.

### In-Scope

The work of the SPICE WG aligns JWT and CWT registered claim names for use with the 'Three Role Model' as introduced by W3C's 'Verifiable Credentials Data Model v2.0' specification (https://w3c.github.io/vc-data-model/#roles).

The SPICE WG will develop a framework in support of the 'Three Role Model', selective disclosure, and unlinkability.
The framework will provide an architecture that enables consistent application of JOSE and COSE, similar to the work done in https://datatracker.ietf.org/doc/html/draft-ietf-rats-eat-21#name-eat-as-a-framework and https://datatracker.ietf.org/doc/draft-ietf-jose-json-web-proof.
The intent is also to apply lessons learned from the development of W3C's 'Securing Verifiable Credentials using JOSE and COSE' specification (https://www.w3.org/TR/vc-jose-cose), and extend them to non JSON-LD based payloads, specifically CWT Claim Sets, or other CBOR data structures.

A short list of lessons learned:
1. Expressive data models, such as RDF, are not necessarily suitable for
   all use-cases outside W3C
2. Reusing existing semantics that fit the domain well, such as provided by
   the JWT/CWT Claims registry, provide can improve interoperability,
   significantly
3. Focussing on crisp technical specifications and producing separate
   informative guidance documents helps to keep technical interested parties
   involved
4. Compact encoding matters and aligning JSON and CBOR provides
   the basis for simpler interoperability and smaller specification

### Out-of-Scope

The working group will NOT address transport protocols, such as those developed at OAUTH, OIDF, W3C or ISO in the scope of its initial charter.
The working group will NOT address specific credential use cases, such as "personal credentials" or "software supply chain".
The SPICE WG's work items will not require nor forbid the use of JSON-LD. Retaining semantic interchangeability is not in-scope. Newly registered claims will have broader applicability, to both JWT and CWT use cases.

## Deliverables

Documents produced by the working group will include the following:

- An architecture document that defines the terminology (e.g., Issuer, Holder, and Verifier), the communication patterns between these parties, and the security/privacy properties.

- A meta-data discovery document enabling issuers, holders and verifiers to discover supported protocols and formats for keys, claims, credentials and proofs.

- A document specifying the disclosure of claims in a secure and privacy-friendly manner.

## Milestones

- 10 2024 - Submit an informational Architecture document to the IESG for publication
- 02 2025 - Submit a document as a proposed standard covering Metadata Discovery to the IESG for publication
- 02 2025 - Submit a document as a proposed standard covering Claims Disclosure to the IESG for publication
