# slsa-provenance-demo

[![Main](https://github.com/shenxianpeng/slsa-provenance-demo/actions/workflows/main.yml/badge.svg)](https://github.com/shenxianpeng/slsa-provenance-demo/actions/workflows/main.yml)
[![SLSA 3](https://slsa.dev/images/gh-badge-level3.svg)](https://slsa.dev)

Generate Level 3 provenance with https://github.com/shenxianpeng/slsa-provenance-demo/blob/main/.github/workflows/main.yml

# Verify artifact

Then user can verify artifact with the following command. (need to install [slsa-verifier](https://github.com/slsa-framework/slsa-verifier) first)

```bash
bash-4.4$ slsa-verifier verify-artifact test-1.0.0-py3-none-any.whl --provenance-path test-1.0.0-py3-none-any.whl.intoto.jsonl --source-uri github.com/shenxianpeng/slsa-provenance-demo
Verified signature against tlog entry index 49728014 at URL: https://rekor.sigstore.dev/api/v1/log/entries/24296fb24b8ad77af7063689e8760fd7134f37e17251ec1d5adc16af64cb5cb579493278f7686e77
Verified build using builder "https://github.com/slsa-framework/slsa-github-generator/.github/workflows/generator_generic_slsa3.yml@refs/tags/v1.9.0" at commit fb7f6df9f8565ed6fa01591df2af0c41e5573798
Verifying artifact test-1.0.0-py3-none-any.whl: PASSED

PASSED: Verified SLSA provenance
```

If user used a malicious package test-1.0.0-py3-none-any.whl, SLSA verification will failed.

```bash
slsa-verifier verify-artifact test-1.0.0-py3-none-any.whl --provenance-path test-1.0.0-py3-none-any.whl.intoto.jsonl --source-uri github.com/shenxianpeng/slsa-provenance-demo
Verified signature against tlog entry index 49728014 at URL: https://rekor.sigstore.dev/api/v1/log/entries/24296fb24b8ad77af7063689e8760fd7134f37e17251ec1d5adc16af64cb5cb579493278f7686e77
Verifying artifact test-1.0.0-py3-none-any.whl: FAILED: expected hash 'e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855' not found: artifact hash does not match provenance subject

FAILED: SLSA verification failed: expected hash 'e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855' not found: artifact hash does not match provenance subject
```

Or if the provenance file is not match the artifact, SLSA verification will also failed.

```bash
slsa-verifier verify-artifact test-1.0.0-py3-none-any.whl --provenance-path fake-test-1.0.0-py3-none-any.whl.intoto.js
onl --source-uri github.com/shenxianpeng/slsa-provenance-demo
Verified signature against tlog entry index 49730828 at URL: https://rekor.sigstore.dev/api/v1/log/entries/24296fb24b8ad77a4d3065ac8be37137dc304fae44b8c7368249a15785fc018e342b6394d387147d
Verifying artifact test-1.0.0-py3-none-any.whl: FAILED: expected hash 'd3e6957b0e434641ba2da134635fc25d3b555e55be4a1f04549627e30f26f118' not found: artifact hash does not match provenance subject

FAILED: SLSA verification failed: expected hash 'd3e6957b0e434641ba2da134635fc25d3b555e55be4a1f04549627e30f26f118' not found: artifact hash does not match provenance subject
```
