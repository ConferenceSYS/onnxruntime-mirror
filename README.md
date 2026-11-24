# onnxruntime-mirror

Unmodified copies of the ONNX Runtime 1.26.0 native Linux libraries, kept so that
ConferenceSYS can build its embeddings service without depending on a single
third-party download host.

The upstream GitHub repository `microsoft/onnxruntime` and its release downloads
became unavailable in November 2026. These files are the official release build,
copied from the official NuGet package, and are served here as release assets.

This is a mirror, not a fork. It contains no source code and is not affiliated
with or endorsed by Microsoft.

## Files

Release `v1.26.0`:

| File | What it is |
|---|---|
| `libonnxruntime-linux-x64-1.26.0.so` | `runtimes/linux-x64/native/libonnxruntime.so` from the package |
| `libonnxruntime-linux-arm64-1.26.0.so` | `runtimes/linux-arm64/native/libonnxruntime.so` from the package |
| `SHA256SUMS` | SHA-256 of both files |

## Where the files come from

* Package: `Microsoft.ML.OnnxRuntime` 1.26.0 on nuget.org, published 2026-05-08.
* Package SHA-512 (as published by nuget.org):
  `zE9c8ZTS90qnEdr3SXN+x02wH6GqAilkiHbSgY7iEDPik3Q1J8cFYEE7s7jzhuowSa8rHZ/gS2bkgJePU53M7Q==`
* Upstream commit recorded in the package: `8c546c37b43caaca1fa25db430dab94b901cf277`.
* The x64 file is byte-for-byte identical to the `libonnxruntime.so` that was baked into
  ConferenceSYS's production image before the upstream repository was removed
  (SHA-256 `5bd5bedf736fc501692435d0ec4f6e8b2bdf48cd30af8e6d00d61b3ddc9a7ab8`).
* The files are not modified in any way.

## Use

```sh
curl -fSL -o libonnxruntime.so \
  https://github.com/ConferenceSYS/onnxruntime-mirror/releases/download/v1.26.0/libonnxruntime-linux-x64-1.26.0.so
echo "5bd5bedf736fc501692435d0ec4f6e8b2bdf48cd30af8e6d00d61b3ddc9a7ab8  libonnxruntime.so" | sha256sum -c -
```

Always verify the checksum. A build that downloads from here should fail if it does not match.

## Licence

ONNX Runtime is released under the MIT licence; the licence text and the third-party
notices shipped with the package are in `LICENSE` and `ThirdPartyNotices.txt`.
Copyright (c) Microsoft Corporation.
