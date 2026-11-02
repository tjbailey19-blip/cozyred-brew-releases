# Brew releases

What Brew.app reads from the internet, and nothing else. No code lives here.

- `appcast.xml`: the update feed Brew checks once a day (Sparkle). Each version's notarized zip is an asset of its GitHub release, signed with Brew's update key.
- `notes/`: each version's release notes.
- `revoked.json`: the invite codes that are turned off, signed with Brew's invite key. Brew downloads it with a plain request that sends nothing about you or your projects.

## Getting started

**What Brew needs.** A Mac with Apple silicon, macOS 14 or later, Adobe Premiere Pro 25.6 or later, and 10 GB free. An internet connection the first time it opens (it downloads the transcription model, about 1.6 GB, once) and whenever it reads a recording with Claude. Your recordings never leave your Mac; only the words of the transcript go to Anthropic, under your own key.

**Two things to have ready.**
- A Claude key. Sign in at https://console.anthropic.com, open API keys, make a key (it starts with `sk-ant-`) and put credit on the account there. Brew keeps the key in your Mac's Keychain and uses it only for your own requests.
- Your invite code, the one you were sent with this link. Paste the whole code.

**Install.** Download the newest `Brew-<version>.zip` from this repository's Releases page, double-click it to unzip, drag Brew into your Applications folder, and open it from there (opened from Downloads, Brew asks to be moved first). macOS asks once whether to open an app downloaded from the internet. Brew has no window: a cup appears in the menu bar at the top right of the screen. Its first screen checks your Mac, downloads the model, and asks for your Claude key and your invite code; press Keep.

**Where the panel is.** Brew puts its own panel into Premiere Pro. Open Premiere and a project, then open the panel from Window → UXP Plugins → Brew and press Choose your episode folder. After your first episode, with Premiere closed, Brew docks the panel beside the timeline for the next time. In the panel: Choose your episode folder, wait for the ready shorts, and click one to put it in your timeline; or pick a beat and press Make the cut.

**Uninstall.** Click the cup in the menu bar and choose Uninstall Brew…: Brew moves itself to the Trash, takes its panel out of Premiere and forgets your Claude key. Uninstall and Remove Projects deletes its data folder too.

## Brew 0.6.2: notices

Brew's own code is Cozyred's. These other programs and libraries ship inside Brew.app, each under its own licence and each with its licence text beside it in the app (paths from Brew.app/Contents). None of them is under the GPL.

### FFmpeg 9.0.2, LGPL 2.1 or later

Resources/bin/ffmpeg and ffprobe, which Brew runs as separate programs. Built from FFmpeg's own source with no GPL part (no --enable-gpl, no x264) and only macOS's own frameworks. The source is the tarball Brew's build pins: ffmpeg-9.0.2.tar.xz from https://ffmpeg.org/releases/ffmpeg-9.0.2.tar.xz (SHA-256 8c3850283eb25fa026482078a04051e0be17347b09ef81a0849bec15a96e002e), configured with --disable-autodetect --enable-videotoolbox --enable-audiotoolbox --enable-zlib --enable-bzlib --disable-doc --disable-ffplay --disable-network --disable-debug. If you want that source and cannot download it there, open an issue at https://github.com/tjbailey19-blip/cozyred-brew-releases/issues and it will be sent to you, for three years from this release. Its licence texts are in Resources/licenses/FFmpeg (COPYING.LGPLv2.1, LICENSE.md).

### soxr 1.1.0, LGPL 2.1 or later

The python-soxr package, with the libsoxr resampler inside it, in Resources/python/lib/python3.11/site-packages/soxr; its licence texts are in Resources/python/lib/python3.11/site-packages/soxr-1.1.0.dist-info/licenses (COPYING.LGPL, LICENSE-libsoxr.txt, LICENSE-PFFFT.txt). Its source is at https://github.com/dofuuz/python-soxr (the same version), libsoxr's with it; the same offer as FFmpeg's applies.

### OpenCV 4.14.0.94, Apache License 2.0

The opencv-python-headless package, built by Brew from the package's own source (opencv_python_headless-4.14.0.94.tar.gz, SHA-256 4afa2ea1214453648be88259f035712454faa9039b686de7753569ba8eec1577) with only the modules Brew uses (core, imgproc, imgcodecs, objdetect, the Python bindings) and none of the video libraries PyPI's wheels carry (which include GPL ones). Its licence texts are in Resources/python/lib/python3.11/site-packages/opencv_python_headless-4.14.0.94.dist-info (LICENSE.txt, LICENSE-3RD-PARTY.txt).

### Sparkle 2.10.0, MIT

Frameworks/Sparkle.framework, the updater; its licence text is in Resources/licenses/Sparkle/LICENSE.

### Python 3.11.17, PSF License 2.0

Resources/python, python-build-standalone's build (release 20261013); its licence text, with those of the libraries it bundles, is Resources/python/lib/python3.11/LICENSE.txt.

### Every Python package in Brew

From backend/requirements.lock, each at the version named, each with its own licence text in its .dist-info folder under Resources/python/lib/python3.11/site-packages:

| package | version | licence |
|---|---|---|
| aiohappyeyeballs | 2.7.1 | PSF-2.0 |
| aiohttp | 3.14.5 | Apache-2.0 AND MIT |
| aiosignal | 1.4.0 | Apache-2.0 |
| annotated-doc | 0.0.5 | MIT |
| annotated-types | 0.8.0 | MIT |
| anthropic | 2.3.0 | Apache-2.0 |
| anyio | 4.15.1 | MIT |
| attrs | 26.1.0 | MIT |
| audioread | 3.1.0 | MIT |
| cbor2 | 6.1.5 | MIT |
| certifi | 2026.7.22 | MPL-2.0 |
| cffi | 2.1.1 | MIT-0 |
| charset-normalizer | 3.5.2 | MIT |
| click | 8.5.0 | BSD-3-Clause |
| cloudpickle | 3.1.2 | BSD-3-Clause |
| cryptography | 50.0.2 | Apache-2.0 OR BSD-3-Clause |
| decorator | 5.3.1 | BSD-2-Clause |
| docstring_parser | 0.18.0 | MIT |
| fastapi | 0.143.0 | MIT |
| filelock | 4.1.1 | MIT |
| frozenlist | 1.8.0 | Apache-2.0 |
| fsspec | 2026.9.0 | BSD-3-Clause |
| grpclib | 0.4.9 | BSD-3-Clause |
| h11 | 0.16.0 | MIT |
| h2 | 4.4.1 | MIT |
| hf-xet | 1.7.0 | Apache-2.0 |
| hpack | 4.2.0 | MIT |
| httpcore2 | 2.13.1 | BSD-3-Clause |
| httptools | 0.9.0 | MIT |
| httpx2 | 2.13.1 | BSD-3-Clause |
| huggingface_hub | 2.2.0 | Apache-2.0 |
| hyperframe | 6.1.0 | MIT |
| idna | 3.20 | BSD-3-Clause |
| Jinja2 | 3.1.6 | BSD |
| jiter | 0.18.0 | MIT |
| joblib | 1.6.0 | BSD-3-Clause |
| lazy-loader | 0.6 | BSD-3-Clause |
| librosa | 0.11.0 | ISC |
| llvmlite | 0.50.0 | BSD-2-Clause AND Apache-2.0 WITH LLVM-exception |
| markdown-it-py | 4.2.0 | MIT |
| MarkupSafe | 3.0.4 | BSD-3-Clause |
| mdurl | 0.1.2 | MIT |
| mlx | 0.32.3 | MIT |
| mlx-metal | 0.32.3 | MIT |
| mlx-whisper | 0.4.3 | MIT |
| modal | 1.6.1 | Apache-2.0 |
| more-itertools | 11.1.0 | MIT |
| mpmath | 1.3.0 | BSD |
| msgpack | 1.2.3 | Apache-2.0 |
| multidict | 7.1.0 | Apache-2.0 |
| mypy | 1.18.2 | MIT |
| mypy_extensions | 1.1.0 | MIT |
| narwhals | 2.27.1 | MIT |
| networkx | 3.6.1 | BSD-3-Clause |
| numba | 0.68.0 | BSD |
| numpy | 2.4.6 | BSD-3-Clause AND 0BSD AND MIT AND Zlib AND CC0-1.0 |
| opencv-python-headless | 4.14.0.94 | Apache-2.0 |
| opentelemetry-api | 1.45.1 | Apache-2.0 |
| OpenTimelineIO | 0.18.1 | Apache-2.0 |
| otio-cmx3600-adapter | 1.0.0 | Apache-2.0 |
| otio-fcp-adapter | 1.0.0 | Apache-2.0 |
| otio-fcpx-xml-adapter | 1.0.0 | Apache-2.0 |
| packaging | 26.3 | Apache-2.0 OR BSD-2-Clause |
| pathspec | 1.1.1 | MPL-2.0 |
| platformdirs | 4.13.0 | MIT |
| pooch | 1.9.0 | BSD-3-Clause |
| propcache | 0.5.4 | Apache-2.0 |
| protobuf | 7.36.2 | BSD-3-Clause |
| pyaaf2 | 1.7.1 | MIT |
| pycparser | 3.11 | BSD-3-Clause |
| pydantic | 2.14.1 | MIT |
| pydantic_core | 2.50.1 | MIT |
| Pygments | 2.21.0 | BSD-2-Clause |
| pyloudnorm | 0.2.0 | MIT |
| python-dotenv | 1.2.4 | BSD-3-Clause |
| PyYAML | 6.0.3 | MIT |
| regex | 2026.9.29 | Apache-2.0 AND CNRI-Python |
| requests | 2.34.2 | Apache-2.0 |
| rich | 15.0.0 | MIT |
| ruff | 0.13.3 | MIT |
| scenedetect | 0.7.2 | BSD-3-Clause |
| scikit-learn | 1.9.1 | BSD-3-Clause |
| scipy | 1.17.1 | BSD |
| sherpa-onnx | 1.13.8 | Apache-2.0 |
| sherpa-onnx-core | 1.13.8 | Apache-2.0 |
| silero-vad | 6.2.3 | MIT |
| sniffio | 1.3.1 | MIT OR Apache-2.0 |
| soundfile | 0.14.0 | BSD-3-Clause |
| soxr | 1.1.0 | LGPL-2.1-or-later |
| starlette | 1.8.0 | BSD-3-Clause |
| sympy | 1.14.0 | BSD |
| synchronicity | 0.12.6 | Apache-2.0 |
| threadpoolctl | 3.7.0 | BSD-3-Clause |
| tiktoken | 0.14.0 | MIT |
| toml | 0.10.2 | MIT |
| torch | 2.14.1 | Apache-2.0 AND Apache-2.0 WITH LLVM-exception AND BSD-2-Clause AND BSD-3-Clause AND BSL-1.0 AND MIT |
| tqdm | 4.70.1 | MPL-2.0 AND MIT |
| truststore | 0.10.5 | MIT |
| types-certifi | 2021.10.8.3 | Apache-2.0 |
| types-toml | 0.10.8.20260518 | Apache-2.0 |
| typing-inspection | 0.4.4 | MIT |
| typing_extensions | 4.16.0 | PSF-2.0 |
| urllib3 | 2.8.0 | MIT |
| uvicorn | 0.54.0 | BSD-3-Clause |
| uvloop | 0.23.0 | MIT |
| watchfiles | 1.3.0 | MIT |
| websockets | 17.2 | BSD-3-Clause |
| yarl | 1.25.1 | Apache-2.0 |
| yt-dlp | 2026.10.21 | Unlicense |
