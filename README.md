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
