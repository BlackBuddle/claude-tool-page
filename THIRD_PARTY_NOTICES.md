# 제3자 소프트웨어 고지 (Third-Party Notices)

> 이 문서는 법률 자문이 아니고, 변호사의 검토를 받은 문서도 아니에요. 회사 업무·영리 목적 등으로 쓰거나 배포하기 전에는 전문가의 검토를 받으세요.
>
> *This document is not legal advice and has not been reviewed by a lawyer. Get professional advice before any business or commercial use or distribution.*

ClaudeTool 0.4.4(2026-10-07 기준) 설치 파일에는 아래의 제3자 소프트웨어가 들어 있어요(이 문서는 설치 파일을 만들 때 들어가는 구성요소를 기준으로 해요). 이 소프트웨어들은 **각자의 라이선스를 따르고**, ClaudeTool의 라이선스([LICENSE](LICENSE))는 그 라이선스를 바꾸지 않아요(LICENSE 제5조). 목록은 설치 파일에 들어가는 구성요소의 `package.json`과 라이선스 파일에서 가져왔고, 새 판에서 바뀔 수 있어요. 설치·제거 프로그램 쪽(3절)은 확인하지 못한 부분이 있어요. 한국어본과 영어본이 함께 있고, 뜻이 다르면 한국어본이 우선해요. 라이선스 전문은 맨 아래 "라이선스 전문" 절에 원문 그대로(영어) 있어요. 함께 읽으면 좋은 문서: [DISCLAIMER.md](DISCLAIMER.md), [PRIVACY.md](PRIVACY.md), [SECURITY.md](SECURITY.md).

*The ClaudeTool 0.4.4 installer (as of 2026-10-07) contains the third-party software listed below (this document is based on the components that go into the installer when it is built). Each item **follows its own license**, and the ClaudeTool license ([LICENSE](LICENSE)) does not change those licenses (LICENSE Section 5). The list was taken from the `package.json` and license files of the components that go into the installer and may change in new versions. Part of the installer/uninstaller side (Section 3) could not be confirmed. A Korean and an English version are provided; if they differ, the Korean version prevails. The license texts are in the "License texts" section at the very bottom, in their original English. See also: [DISCLAIMER.md](DISCLAIMER.md), [PRIVACY.md](PRIVACY.md), [SECURITY.md](SECURITY.md).*

---

## 한국어

### 1. 실행 환경: Electron, Chromium, Node.js

- 설치 폴더에는 **Electron 44.4.3**(MIT 라이선스, Copyright (c) Electron contributors, Copyright (c) 2013-2020 GitHub Inc.)이 들어 있어요. Electron은 Chromium(브라우저 엔진)과 Node.js를 품고 있어요.
- 설치 폴더 바로 아래에 다음 파일이 **함께 설치돼요.**
  - `LICENSE.electron.txt`: Electron의 라이선스와 저작권 고지
  - `LICENSES.chromium.html`: Chromium과 그 안에 든 구성요소(V8, Node.js, FFmpeg, ICU, ANGLE, SwiftShader, Skia, zlib 등)의 라이선스와 저작권 고지
- 설치 폴더의 `resources\node`에는 Claude Code 연결 스크립트를 돌리는 **Node.js**(MIT 라이선스, Copyright Node.js contributors)의 `node.exe`가 **함께 설치돼요.** 버전은 설치 파일을 만들 때 쓴 판이라 `resources\node\VERSION.txt`를 참고하세요. 라이선스는 같은 폴더의 `LICENSE`에 있어요.
- 해당 구성요소들은 위 파일에 적힌 라이선스(BSD, MIT, Apache-2.0, LGPL-2.1 등)를 따라요. 예를 들어 FFmpeg는 LGPL 2.1을 따르고 `ffmpeg.dll`이라는 별도 파일로 설치돼요.
- 그 밖에 Electron과 함께 들어 있는 그래픽·시스템 관련 파일(`d3dcompiler_47.dll`, `dxcompiler.dll`, `dxil.dll`, `vulkan-1.dll`, `vk_swiftshader.dll`, `icudtl.dat` 등)도 각각의 제공자가 정한 라이선스를 따라요.

### 2. 앱에 들어 있는 npm 패키지

설치 폴더의 `node_modules`와 화면 코드에 들어가는 패키지예요. Anthropic SDK와 새 판 확인(`electron-updater`)이 끌고 들어오는 하위 패키지도 모두 적었어요. 각 패키지의 라이선스 파일(`LICENSE`)은 설치 폴더의 `resources\app\node_modules\<패키지 이름>` 안에도 들어 있어요(`standardwebhooks`와 `lazy-val`은 라이선스 파일이 없어요).

| 패키지 | 버전 | 라이선스 | 저작권 | 쓰임 |
|---|---|---|---|---|
| `@anthropic-ai/sdk` | 0.127.0 | MIT (일부 코드는 BSD-3-Clause, 아래 "라이선스 전문") | Copyright 2023 Anthropic, PBC. | 질문하기의 API 키 방식 |
| `@babel/runtime` | 7.29.7 | MIT | Copyright (c) 2014-present Sebastian McKenzie and other contributors | `json-schema-to-ts`의 하위 패키지 |
| `@stablelib/base64` | 1.0.1 | MIT | Copyright (C) 2016 Dmitry Chestnykh | `standardwebhooks`의 하위 패키지 |
| `argparse` | 2.0.1 | Python-2.0 | PSF 라이선스 전문 아래 "라이선스 전문"에 있어요(전문 안에 "Copyright (c) 2001, 2002, 2003, 2004, 2005, 2006 Python Software Foundation" 표기가 있어요) | `js-yaml`의 하위 패키지 |
| `builder-util-runtime` | 9.7.0 | MIT | Copyright (c) 2015 Loopline Systems | `electron-updater`의 하위 패키지 |
| `debug` | 4.4.3 | MIT | Copyright (c) 2014-2017 TJ Holowaychuk, (c) 2018-2021 Josh Junon | `builder-util-runtime`의 하위 패키지 |
| `electron-updater` | 6.8.10 | MIT | Copyright (c) 2015 Loopline Systems | 새 판 확인과 업데이트 |
| `fast-sha256` | 1.3.0 | Unlicense(퍼블릭 도메인) | 저작권을 주장하지 않아요(퍼블릭 도메인으로 공개됨) | `standardwebhooks`의 하위 패키지 |
| `fflate` | 0.8.3 | MIT | Copyright (c) 2026 Arjun Barrett | zip 가져오기·내보내기 |
| `fs-extra` | 10.1.0 | MIT | Copyright (c) 2011-2017 JP Richardson | `electron-updater`의 하위 패키지 |
| `graceful-fs` | 4.2.11 | ISC | Copyright (c) 2011-2022 Isaac Z. Schlueter, Ben Noordhuis, and Contributors | `fs-extra`의 하위 패키지 |
| `js-yaml` | 4.3.2 | MIT | Copyright (C) 2011-2015 by Vitaly Puzrin | `electron-updater`의 하위 패키지(업데이트 정보 `latest.yml` 읽기) |
| `json-schema-to-ts` | 3.1.1 | MIT | Copyright (c) 2020 Thomas Aribart | Anthropic SDK의 하위 패키지 |
| `jsonfile` | 6.2.1 | MIT | Copyright (c) 2012-2015, JP Richardson | `fs-extra`의 하위 패키지 |
| `lazy-val` | 1.0.5 | MIT(패키지 정보에 적힌 값) | 패키지에 라이선스 파일이 들어 있지 않아 저작권 줄을 확인하지 못했어요 | `electron-updater`의 하위 패키지 |
| `lodash.escaperegexp` | 4.1.2 | MIT | Copyright jQuery Foundation and other contributors | `electron-updater`의 하위 패키지 |
| `lodash.isequal` | 4.5.0 | MIT | Copyright JS Foundation and other contributors | `electron-updater`의 하위 패키지 |
| `ms` | 2.1.3 | MIT | Copyright (c) 2020 Vercel, Inc. | `debug`의 하위 패키지 |
| `preact` | 10.29.8 | MIT | Copyright (c) 2015-present Jason Miller | 화면(펫·말풍선·설정 창) |
| `sax` | 1.6.1 | BlueOak-1.0.0 | 라이선스 전문(아래 "라이선스 전문")에 저작권 줄이 없어요. 만든 사람: Isaac Z. Schlueter(패키지 정보) | `builder-util-runtime`의 하위 패키지 |
| `semver` | 7.7.4 | ISC | Copyright (c) Isaac Z. Schlueter and Contributors | `electron-updater`의 하위 패키지(판 번호 비교) |
| `standardwebhooks` | 1.1.1 | MIT(패키지 정보에 적힌 값) | 패키지에 라이선스 파일이 들어 있지 않아 저작권 줄을 확인하지 못했어요. 만든 곳: Standard Webhooks | Anthropic SDK의 하위 패키지 |
| `tiny-typed-emitter` | 2.1.0 | MIT | Copyright (c) 2020 Zurab Benashvili (binier) | `electron-updater`의 하위 패키지 |
| `ts-algebra` | 2.0.0 | MIT | Copyright (c) 2020 Thomas Aribart | `json-schema-to-ts`의 하위 패키지 |
| `universalify` | 2.0.1 | MIT | Copyright (c) 2017, Ryan Zimmerman | `fs-extra`·`jsonfile`의 하위 패키지 |
| `zod` | 4.6.5 | MIT | Copyright (c) 2025 Colin McDonnell | 설정·입력값 검사 |

### 3. 설치 프로그램(NSIS)

- 설치·제거 프로그램은 NSIS(Nullsoft Scriptable Install System) 3.0.4.1로 만들었어요(빌드 도구 electron-builder 26.15.3이 내려받아 쓰는 판). 설치·제거 프로그램 실행 파일에 NSIS의 실행 코드가 들어 있어요. NSIS는 zlib/libpng 라이선스를 따르고, 압축 모듈은 각각 zlib/libpng·bzip2·LZMA(Common Public License 1.0) 라이선스를 따라요(NSIS 배포본의 `COPYING` 기준). NSIS와 함께 오는 기본 플러그인·헤더(`System`, `nsExec`, `nsDialogs` 등)도, 따로 표시된 것을 뺀 나머지는 `COPYING`에 따라 같은 zlib/libpng 라이선스예요.
- LZMA 압축 모듈의 소스 코드는 NSIS 프로젝트에서 구할 수 있어요.
- 설치 화면과 설치 순서를 정하는 스크립트는 electron-builder의 NSIS 템플릿에서 왔어요. electron-builder는 MIT 라이선스(Copyright (c) 2015 Loopline Systems)예요.
- **확인하지 못한 것:** 설치·제거 프로그램 안에 실제로 든 NSIS 플러그인(설치 프로그램용 DLL)과 보조 프로그램의 전체 목록, 그리고 아래 표에서 "확인하지 못한 것"으로 적은 라이선스를 확인하지 못했어요. 설치 파일의 압축된 안은 열어 보지 않았고, electron-builder의 NSIS 템플릿(이 설치 프로그램의 설정에서 쓰이는 부분)과 빌드 도구가 내려받아 둔 NSIS 플러그인 묶음에서 이름이 확인되는 것만 적었어요(0.3.0 빌드의 설치 스크립트 기록에서 이 묶음의 `x86-unicode` 폴더가 플러그인 경로로 지정된 것까지는 확인했어요). 아래 표는 설치 파일에 든 것의 전부라는 보증도, 표에 있는 것이 모두 들어 있다는 보증도 아니에요.

| 구성요소 | 확인된 것 | 확인하지 못한 것 |
|---|---|---|
| `StdUtils`(NSIS 플러그인, 템플릿이 호출) | Copyright (C) 2004-2018 LoRd_MuldeR. 템플릿에 든 헤더 파일 머리에 GNU LGPL 2.1 이상으로 적혀 있어요 | LGPL 전문, 소스 코드를 구할 곳 |
| `nsis7z`(7-Zip NSIS 플러그인, 앱 압축 풀기) | 파일 정보에 Copyright (c) 1999-2016 Igor Pavlov, Nik Medved, Marek Mizanin, Stuart Welch | 라이선스 |
| `nsProcess`, `UAC`, `WinShell`, `SpiderBanner`(NSIS 플러그인, 템플릿이 호출) | 이름만 확인했어요(파일에서 저작권 표시를 찾지 못했어요) | 저작자, 라이선스 |
| `elevate.exe`(NSIS 도구 묶음에 들어 있던 것을 electron-builder가 설치 폴더의 `resources\elevate.exe`로 넣어요) | 파일 정보에 (c) 2007 Johannes Passing | 라이선스 |
| 템플릿에 든 보조 스크립트(`NsisMultiUser` 계열, `StrContains` 등) | 템플릿 설명에 NsisMultiUser를 쓴다고 적혀 있어요. `StrContains`는 kenglish_hi가 쓰고 dandaman32의 `StrReplace`를 바탕으로 했다고만 적혀 있어요 | 라이선스 |

- 같은 플러그인 묶음에는 `INetC`·`nsisunz`·`EmbedHTML`도 들어 있지만, 템플릿은 `INetC`를 웹 설치 프로그램에서만, `nsisunz`를 zip 압축 방식에서만 부르고 `EmbedHTML`은 부르지 않아요. 이 설치 프로그램은 그런 방식이 아니라서 쓰이지 않는 것으로 보지만, 확인하지 못했어요.
- ClaudeTool의 라이선스와 면책조항 가운데 위 구성요소의 라이선스와 다른 조항은 **저작권자가 단독으로 제공하는 것**이고, 구성요소 제공자가 제공하는 것이 아니에요. 구성요소 제공자는 어떤 보증도 하지 않고 손해에 대해 책임지지 않아요.

### 4. 상표

이 문서에 나온 제품·회사 이름은 각 소유자의 상표예요. ClaudeTool은 이들과 제휴·후원·승인 관계가 없어요. "Claude", "Anthropic"에 관한 내용은 [DISCLAIMER.md](DISCLAIMER.md)의 4절을 보세요.

---

## English

*A courtesy translation. If it differs from the Korean version, the Korean version prevails.*

### 1. Runtime: Electron, Chromium, Node.js

- The install folder contains **Electron 44.4.3** (MIT License, Copyright (c) Electron contributors, Copyright (c) 2013-2020 GitHub Inc.). Electron includes Chromium (the browser engine) and Node.js.
- The following files are **installed together** directly under the install folder:
  - `LICENSE.electron.txt`: Electron's license and copyright notice
  - `LICENSES.chromium.html`: licenses and copyright notices of Chromium and the components inside it (V8, Node.js, FFmpeg, ICU, ANGLE, SwiftShader, Skia, zlib, etc.)
- The `resources\node` folder of the install folder also contains **Node.js** (MIT License, Copyright Node.js contributors) as `node.exe`, which runs the Claude Code connection script. The version is the one used when the installer was built; see `resources\node\VERSION.txt`. Its license is in `LICENSE` in the same folder.
- Those components follow the licenses written in the files above (BSD, MIT, Apache-2.0, LGPL-2.1, etc.). For example, FFmpeg follows LGPL 2.1 and is installed as a separate file, `ffmpeg.dll`.
- Other graphics- and system-related files that come with Electron (`d3dcompiler_47.dll`, `dxcompiler.dll`, `dxil.dll`, `vulkan-1.dll`, `vk_swiftshader.dll`, `icudtl.dat`, etc.) follow the licenses set by their respective providers.

### 2. npm packages in the app

These are the packages in the install folder's `node_modules` and in the screen code, including every sub-package that the Anthropic SDK and the new-version check (`electron-updater`) pull in. Each package's license file (`LICENSE`) is also included in the install folder under `resources\app\node_modules\<package name>` (`standardwebhooks` and `lazy-val` ship none).

| Package | Version | License | Copyright | Used for |
|---|---|---|---|---|
| `@anthropic-ai/sdk` | 0.127.0 | MIT (some code is BSD-3-Clause, see "License texts" below) | Copyright 2023 Anthropic, PBC. | The API-key method of asking questions |
| `@babel/runtime` | 7.29.7 | MIT | Copyright (c) 2014-present Sebastian McKenzie and other contributors | Sub-package of `json-schema-to-ts` |
| `@stablelib/base64` | 1.0.1 | MIT | Copyright (C) 2016 Dmitry Chestnykh | Sub-package of `standardwebhooks` |
| `argparse` | 2.0.1 | Python-2.0 | The PSF license text is under "License texts" below (it carries "Copyright (c) 2001, 2002, 2003, 2004, 2005, 2006 Python Software Foundation") | Sub-package of `js-yaml` |
| `builder-util-runtime` | 9.7.0 | MIT | Copyright (c) 2015 Loopline Systems | Sub-package of `electron-updater` |
| `debug` | 4.4.3 | MIT | Copyright (c) 2014-2017 TJ Holowaychuk, (c) 2018-2021 Josh Junon | Sub-package of `builder-util-runtime` |
| `electron-updater` | 6.8.10 | MIT | Copyright (c) 2015 Loopline Systems | Checking for new versions and updating |
| `fast-sha256` | 1.3.0 | Unlicense (public domain) | No copyright is claimed (released into the public domain) | Sub-package of `standardwebhooks` |
| `fflate` | 0.8.3 | MIT | Copyright (c) 2026 Arjun Barrett | Importing/exporting zip files |
| `fs-extra` | 10.1.0 | MIT | Copyright (c) 2011-2017 JP Richardson | Sub-package of `electron-updater` |
| `graceful-fs` | 4.2.11 | ISC | Copyright (c) 2011-2022 Isaac Z. Schlueter, Ben Noordhuis, and Contributors | Sub-package of `fs-extra` |
| `js-yaml` | 4.3.2 | MIT | Copyright (C) 2011-2015 by Vitaly Puzrin | Sub-package of `electron-updater` (reading the update information `latest.yml`) |
| `json-schema-to-ts` | 3.1.1 | MIT | Copyright (c) 2020 Thomas Aribart | Sub-package of the Anthropic SDK |
| `jsonfile` | 6.2.1 | MIT | Copyright (c) 2012-2015, JP Richardson | Sub-package of `fs-extra` |
| `lazy-val` | 1.0.5 | MIT (as stated in the package metadata) | The package ships no license file, so the copyright line could not be confirmed | Sub-package of `electron-updater` |
| `lodash.escaperegexp` | 4.1.2 | MIT | Copyright jQuery Foundation and other contributors | Sub-package of `electron-updater` |
| `lodash.isequal` | 4.5.0 | MIT | Copyright JS Foundation and other contributors | Sub-package of `electron-updater` |
| `ms` | 2.1.3 | MIT | Copyright (c) 2020 Vercel, Inc. | Sub-package of `debug` |
| `preact` | 10.29.8 | MIT | Copyright (c) 2015-present Jason Miller | The screens (pet, speech bubbles, settings window) |
| `sax` | 1.6.1 | BlueOak-1.0.0 | The license text (under "License texts" below) has no copyright line. Author: Isaac Z. Schlueter (per the package metadata) | Sub-package of `builder-util-runtime` |
| `semver` | 7.7.4 | ISC | Copyright (c) Isaac Z. Schlueter and Contributors | Sub-package of `electron-updater` (comparing version numbers) |
| `standardwebhooks` | 1.1.1 | MIT (as stated in the package metadata) | The package ships no license file, so the copyright line could not be confirmed. Made by: Standard Webhooks | Sub-package of the Anthropic SDK |
| `tiny-typed-emitter` | 2.1.0 | MIT | Copyright (c) 2020 Zurab Benashvili (binier) | Sub-package of `electron-updater` |
| `ts-algebra` | 2.0.0 | MIT | Copyright (c) 2020 Thomas Aribart | Sub-package of `json-schema-to-ts` |
| `universalify` | 2.0.1 | MIT | Copyright (c) 2017, Ryan Zimmerman | Sub-package of `fs-extra` and `jsonfile` |
| `zod` | 4.6.5 | MIT | Copyright (c) 2025 Colin McDonnell | Validating settings and inputs |

### 3. The installer (NSIS)

- The installer and uninstaller were built with NSIS (Nullsoft Scriptable Install System) 3.0.4.1 (the version the build tool electron-builder 26.15.3 downloads and uses), and the installer and uninstaller executables contain NSIS's runtime code. NSIS follows the zlib/libpng license, and its compression modules follow the zlib/libpng, bzip2 and LZMA (Common Public License 1.0) licenses respectively (according to the `COPYING` of the NSIS distribution). The default plugins and headers that come with NSIS (`System`, `nsExec`, `nsDialogs`, etc.) are, except where noted otherwise, under the same zlib/libpng license according to `COPYING`.
- The source code of the LZMA compression module is available from the NSIS project.
- The scripts that define the installer's screens and steps come from electron-builder's NSIS templates. electron-builder is under the MIT License (Copyright (c) 2015 Loopline Systems).
- **What could not be confirmed:** the complete list of NSIS plugins (DLLs for installers) and helper programs that actually went into the installer and uninstaller, and the licenses marked "What could not be confirmed" in the table below. The compressed inside of the installer was not opened; only names that can be found in electron-builder's NSIS templates (the parts used by this installer's settings) and in the NSIS plugin pack the build tool downloaded are listed (it was confirmed from the installer-script record of the 0.3.0 build that this pack's `x86-unicode` folder was set as the plugin path). The table is not a guarantee that it is everything that went into the installer, nor that everything in it did.

| Component | What was confirmed | What could not be confirmed |
|---|---|---|
| `StdUtils` (NSIS plugin, called by the templates) | Copyright (C) 2004-2018 LoRd_MuldeR. The header file in the templates states GNU LGPL 2.1 or later | The LGPL text, where to get the source code |
| `nsis7z` (7-Zip NSIS plugin, extracts the app) | The file information says Copyright (c) 1999-2016 Igor Pavlov, Nik Medved, Marek Mizanin, Stuart Welch | The license |
| `nsProcess`, `UAC`, `WinShell`, `SpiderBanner` (NSIS plugins, called by the templates) | Only the names were confirmed (no copyright notice could be found in the files) | The authors, the licenses |
| `elevate.exe` (taken from the NSIS tool bundle and placed by electron-builder at `resources\elevate.exe` in the install folder) | The file information says (c) 2007 Johannes Passing | The license |
| Helper scripts in the templates (derived from `NsisMultiUser`, `StrContains`, etc.) | The template notes say NsisMultiUser is used. `StrContains` is only noted as written by kenglish_hi, adapted from `StrReplace` by dandaman32 | The licenses |

- The same plugin pack also contains `INetC`, `nsisunz` and `EmbedHTML`, but the templates call `INetC` only for a web installer and `nsisunz` only for the zip compression mode, and do not call `EmbedHTML`. This installer uses neither mode, so they are presumed unused, but that could not be confirmed.
- Any provision of the ClaudeTool license and disclaimer that differs from the licenses of the components above is offered **by the Licensor alone**, not by the component providers. The component providers give no warranty and are not liable for damages.

### 4. Trademarks

Product and company names in this document are trademarks of their respective owners. ClaudeTool is not affiliated with, sponsored by or approved by them. For "Claude" and "Anthropic", see Section 4 of [DISCLAIMER.md](DISCLAIMER.md).

---

## 라이선스 전문 (License texts)

원문 그대로(영어)예요. 한국어본·영어본 모두에 적용돼요. *Original English texts; they apply to both the Korean and the English parts above.*

**MIT License:** `@anthropic-ai/sdk`, `@babel/runtime`, `@stablelib/base64`, `builder-util-runtime`, `debug`, `electron-updater`, `fflate`, `fs-extra`, `js-yaml`, `json-schema-to-ts`, `jsonfile`, `lazy-val`, `lodash.escaperegexp`, `lodash.isequal`, `ms`, `preact`, `standardwebhooks`, `tiny-typed-emitter`, `ts-algebra`, `universalify`, `zod`, Electron, electron-builder의 NSIS 템플릿. 저작권 표시는 위 표의 "저작권" 칸(Electron은 `LICENSE.electron.txt`, electron-builder의 NSIS 템플릿은 3절)을 보세요. *Copyright notices: see the "Copyright" column of the table above (for Electron, `LICENSE.electron.txt`; for electron-builder's NSIS templates, Section 3).*

**The Unlicense:** `fast-sha256`. **BSD 3-Clause:** `@anthropic-ai/sdk` 안의 쿼리 문자열 처리 코드 *(query-string code inside `@anthropic-ai/sdk`)*. **ISC License:** `graceful-fs`, `semver`. **Blue Oak Model License 1.0.0:** `sax`. **Python Software Foundation License(Python-2.0):** `argparse`.

### MIT License

```text
MIT License

Copyright (c) <copyright holder of each package; see the "Copyright" column of the table above>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

### The Unlicense (`fast-sha256`)

```text
This is free and unencumbered software released into the public domain.

Anyone is free to copy, modify, publish, use, compile, sell, or
distribute this software, either in source code form or as a compiled
binary, for any purpose, commercial or non-commercial, and by any
means.

In jurisdictions that recognize copyright laws, the author or authors
of this software dedicate any and all copyright interest in the
software to the public domain. We make this dedication for the benefit
of the public at large and to the detriment of our heirs and
successors. We intend this dedication to be an overt act of
relinquishment in perpetuity of all present and future rights to this
software under copyright law.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS BE LIABLE FOR ANY CLAIM, DAMAGES OR
OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE,
ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.

For more information, please refer to unlicense.org
```

### BSD 3-Clause License (`@anthropic-ai/sdk` 안의 쿼리 문자열 처리 코드 / query-string code inside `@anthropic-ai/sdk`)

```text
BSD 3-Clause License

Copyright (c) 2014, Nathan LaFreniere and other contributors. All rights reserved.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

3. Neither the name of the copyright holder nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```

### ISC License (`graceful-fs`, `semver`)

```text
ISC License

Copyright (c) <copyright holder of each package; see the "Copyright" column of the table above>

Permission to use, copy, modify, and/or distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR
IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
```

### Blue Oak Model License 1.0.0 (`sax`)

```text
# Blue Oak Model License

Version 1.0.0

## Purpose

This license gives everyone as much permission to work with
this software as possible, while protecting contributors
from liability.

## Acceptance

In order to receive this license, you must agree to its
rules.  The rules of this license are both obligations
under that agreement and conditions to your license.
You must not do anything with this software that triggers
a rule that you cannot or will not follow.

## Copyright

Each contributor licenses you to do everything with this
software that would otherwise infringe that contributor's
copyright in it.

## Notices

You must ensure that everyone who gets a copy of
any part of this software from you, with or without
changes, also gets the text of this license or a link to
<https://blueoakcouncil.org/license/1.0.0>.

## Excuse

If anyone notifies you in writing that you have not
complied with [Notices](#notices), you can keep your
license by taking all practical steps to comply within 30
days after the notice.  If you do not do so, your license
ends immediately.

## Patent

Each contributor licenses you to do everything with this
software that would otherwise infringe any patent claims
they can license or become able to license.

## Reliability

No contributor can revoke this license.

## No Liability

***As far as the law allows, this software comes as is,
without any warranty or condition, and no contributor
will be liable to anyone for any damages related to this
software or this license, under any kind of legal claim.***
```

### Python Software Foundation License (Python-2.0) (`argparse`)

```text
A. HISTORY OF THE SOFTWARE
==========================

Python was created in the early 1990s by Guido van Rossum at Stichting
Mathematisch Centrum (CWI, see http://www.cwi.nl) in the Netherlands
as a successor of a language called ABC.  Guido remains Python's
principal author, although it includes many contributions from others.

In 1995, Guido continued his work on Python at the Corporation for
National Research Initiatives (CNRI, see http://www.cnri.reston.va.us)
in Reston, Virginia where he released several versions of the
software.

In May 2000, Guido and the Python core development team moved to
BeOpen.com to form the BeOpen PythonLabs team.  In October of the same
year, the PythonLabs team moved to Digital Creations, which became
Zope Corporation.  In 2001, the Python Software Foundation (PSF, see
https://www.python.org/psf/) was formed, a non-profit organization
created specifically to own Python-related Intellectual Property.
Zope Corporation was a sponsoring member of the PSF.

All Python releases are Open Source (see http://www.opensource.org for
the Open Source Definition).  Historically, most, but not all, Python
releases have also been GPL-compatible; the table below summarizes
the various releases.

    Release         Derived     Year        Owner       GPL-
                    from                                compatible? (1)

    0.9.0 thru 1.2              1991-1995   CWI         yes
    1.3 thru 1.5.2  1.2         1995-1999   CNRI        yes
    1.6             1.5.2       2000        CNRI        no
    2.0             1.6         2000        BeOpen.com  no
    1.6.1           1.6         2001        CNRI        yes (2)
    2.1             2.0+1.6.1   2001        PSF         no
    2.0.1           2.0+1.6.1   2001        PSF         yes
    2.1.1           2.1+2.0.1   2001        PSF         yes
    2.1.2           2.1.1       2002        PSF         yes
    2.1.3           2.1.2       2002        PSF         yes
    2.2 and above   2.1.1       2001-now    PSF         yes

Footnotes:

(1) GPL-compatible doesn't mean that we're distributing Python under
    the GPL.  All Python licenses, unlike the GPL, let you distribute
    a modified version without making your changes open source.  The
    GPL-compatible licenses make it possible to combine Python with
    other software that is released under the GPL; the others don't.

(2) According to Richard Stallman, 1.6.1 is not GPL-compatible,
    because its license has a choice of law clause.  According to
    CNRI, however, Stallman's lawyer has told CNRI's lawyer that 1.6.1
    is "not incompatible" with the GPL.

Thanks to the many outside volunteers who have worked under Guido's
direction to make these releases possible.


B. TERMS AND CONDITIONS FOR ACCESSING OR OTHERWISE USING PYTHON
===============================================================

PYTHON SOFTWARE FOUNDATION LICENSE VERSION 2
--------------------------------------------

1. This LICENSE AGREEMENT is between the Python Software Foundation
("PSF"), and the Individual or Organization ("Licensee") accessing and
otherwise using this software ("Python") in source or binary form and
its associated documentation.

2. Subject to the terms and conditions of this License Agreement, PSF hereby
grants Licensee a nonexclusive, royalty-free, world-wide license to reproduce,
analyze, test, perform and/or display publicly, prepare derivative works,
distribute, and otherwise use Python alone or in any derivative version,
provided, however, that PSF's License Agreement and PSF's notice of copyright,
i.e., "Copyright (c) 2001, 2002, 2003, 2004, 2005, 2006, 2007, 2008, 2009, 2010,
2011, 2012, 2013, 2014, 2015, 2016, 2017, 2018, 2019, 2020 Python Software Foundation;
All Rights Reserved" are retained in Python alone or in any derivative version
prepared by Licensee.

3. In the event Licensee prepares a derivative work that is based on
or incorporates Python or any part thereof, and wants to make
the derivative work available to others as provided herein, then
Licensee hereby agrees to include in any such work a brief summary of
the changes made to Python.

4. PSF is making Python available to Licensee on an "AS IS"
basis.  PSF MAKES NO REPRESENTATIONS OR WARRANTIES, EXPRESS OR
IMPLIED.  BY WAY OF EXAMPLE, BUT NOT LIMITATION, PSF MAKES NO AND
DISCLAIMS ANY REPRESENTATION OR WARRANTY OF MERCHANTABILITY OR FITNESS
FOR ANY PARTICULAR PURPOSE OR THAT THE USE OF PYTHON WILL NOT
INFRINGE ANY THIRD PARTY RIGHTS.

5. PSF SHALL NOT BE LIABLE TO LICENSEE OR ANY OTHER USERS OF PYTHON
FOR ANY INCIDENTAL, SPECIAL, OR CONSEQUENTIAL DAMAGES OR LOSS AS
A RESULT OF MODIFYING, DISTRIBUTING, OR OTHERWISE USING PYTHON,
OR ANY DERIVATIVE THEREOF, EVEN IF ADVISED OF THE POSSIBILITY THEREOF.

6. This License Agreement will automatically terminate upon a material
breach of its terms and conditions.

7. Nothing in this License Agreement shall be deemed to create any
relationship of agency, partnership, or joint venture between PSF and
Licensee.  This License Agreement does not grant permission to use PSF
trademarks or trade name in a trademark sense to endorse or promote
products or services of Licensee, or any third party.

8. By copying, installing or otherwise using Python, Licensee
agrees to be bound by the terms and conditions of this License
Agreement.


BEOPEN.COM LICENSE AGREEMENT FOR PYTHON 2.0
-------------------------------------------

BEOPEN PYTHON OPEN SOURCE LICENSE AGREEMENT VERSION 1

1. This LICENSE AGREEMENT is between BeOpen.com ("BeOpen"), having an
office at 160 Saratoga Avenue, Santa Clara, CA 95051, and the
Individual or Organization ("Licensee") accessing and otherwise using
this software in source or binary form and its associated
documentation ("the Software").

2. Subject to the terms and conditions of this BeOpen Python License
Agreement, BeOpen hereby grants Licensee a non-exclusive,
royalty-free, world-wide license to reproduce, analyze, test, perform
and/or display publicly, prepare derivative works, distribute, and
otherwise use the Software alone or in any derivative version,
provided, however, that the BeOpen Python License is retained in the
Software, alone or in any derivative version prepared by Licensee.

3. BeOpen is making the Software available to Licensee on an "AS IS"
basis.  BEOPEN MAKES NO REPRESENTATIONS OR WARRANTIES, EXPRESS OR
IMPLIED.  BY WAY OF EXAMPLE, BUT NOT LIMITATION, BEOPEN MAKES NO AND
DISCLAIMS ANY REPRESENTATION OR WARRANTY OF MERCHANTABILITY OR FITNESS
FOR ANY PARTICULAR PURPOSE OR THAT THE USE OF THE SOFTWARE WILL NOT
INFRINGE ANY THIRD PARTY RIGHTS.

4. BEOPEN SHALL NOT BE LIABLE TO LICENSEE OR ANY OTHER USERS OF THE
SOFTWARE FOR ANY INCIDENTAL, SPECIAL, OR CONSEQUENTIAL DAMAGES OR LOSS
AS A RESULT OF USING, MODIFYING OR DISTRIBUTING THE SOFTWARE, OR ANY
DERIVATIVE THEREOF, EVEN IF ADVISED OF THE POSSIBILITY THEREOF.

5. This License Agreement will automatically terminate upon a material
breach of its terms and conditions.

6. This License Agreement shall be governed by and interpreted in all
respects by the law of the State of California, excluding conflict of
law provisions.  Nothing in this License Agreement shall be deemed to
create any relationship of agency, partnership, or joint venture
between BeOpen and Licensee.  This License Agreement does not grant
permission to use BeOpen trademarks or trade names in a trademark
sense to endorse or promote products or services of Licensee, or any
third party.  As an exception, the "BeOpen Python" logos available at
http://www.pythonlabs.com/logos.html may be used according to the
permissions granted on that web page.

7. By copying, installing or otherwise using the software, Licensee
agrees to be bound by the terms and conditions of this License
Agreement.


CNRI LICENSE AGREEMENT FOR PYTHON 1.6.1
---------------------------------------

1. This LICENSE AGREEMENT is between the Corporation for National
Research Initiatives, having an office at 1895 Preston White Drive,
Reston, VA 20191 ("CNRI"), and the Individual or Organization
("Licensee") accessing and otherwise using Python 1.6.1 software in
source or binary form and its associated documentation.

2. Subject to the terms and conditions of this License Agreement, CNRI
hereby grants Licensee a nonexclusive, royalty-free, world-wide
license to reproduce, analyze, test, perform and/or display publicly,
prepare derivative works, distribute, and otherwise use Python 1.6.1
alone or in any derivative version, provided, however, that CNRI's
License Agreement and CNRI's notice of copyright, i.e., "Copyright (c)
1995-2001 Corporation for National Research Initiatives; All Rights
Reserved" are retained in Python 1.6.1 alone or in any derivative
version prepared by Licensee.  Alternately, in lieu of CNRI's License
Agreement, Licensee may substitute the following text (omitting the
quotes): "Python 1.6.1 is made available subject to the terms and
conditions in CNRI's License Agreement.  This Agreement together with
Python 1.6.1 may be located on the Internet using the following
unique, persistent identifier (known as a handle): 1895.22/1013.  This
Agreement may also be obtained from a proxy server on the Internet
using the following URL: http://hdl.handle.net/1895.22/1013".

3. In the event Licensee prepares a derivative work that is based on
or incorporates Python 1.6.1 or any part thereof, and wants to make
the derivative work available to others as provided herein, then
Licensee hereby agrees to include in any such work a brief summary of
the changes made to Python 1.6.1.

4. CNRI is making Python 1.6.1 available to Licensee on an "AS IS"
basis.  CNRI MAKES NO REPRESENTATIONS OR WARRANTIES, EXPRESS OR
IMPLIED.  BY WAY OF EXAMPLE, BUT NOT LIMITATION, CNRI MAKES NO AND
DISCLAIMS ANY REPRESENTATION OR WARRANTY OF MERCHANTABILITY OR FITNESS
FOR ANY PARTICULAR PURPOSE OR THAT THE USE OF PYTHON 1.6.1 WILL NOT
INFRINGE ANY THIRD PARTY RIGHTS.

5. CNRI SHALL NOT BE LIABLE TO LICENSEE OR ANY OTHER USERS OF PYTHON
1.6.1 FOR ANY INCIDENTAL, SPECIAL, OR CONSEQUENTIAL DAMAGES OR LOSS AS
A RESULT OF MODIFYING, DISTRIBUTING, OR OTHERWISE USING PYTHON 1.6.1,
OR ANY DERIVATIVE THEREOF, EVEN IF ADVISED OF THE POSSIBILITY THEREOF.

6. This License Agreement will automatically terminate upon a material
breach of its terms and conditions.

7. This License Agreement shall be governed by the federal
intellectual property law of the United States, including without
limitation the federal copyright law, and, to the extent such
U.S. federal law does not apply, by the law of the Commonwealth of
Virginia, excluding Virginia's conflict of law provisions.
Notwithstanding the foregoing, with regard to derivative works based
on Python 1.6.1 that incorporate non-separable material that was
previously distributed under the GNU General Public License (GPL), the
law of the Commonwealth of Virginia shall govern this License
Agreement only as to issues arising under or with respect to
Paragraphs 4, 5, and 7 of this License Agreement.  Nothing in this
License Agreement shall be deemed to create any relationship of
agency, partnership, or joint venture between CNRI and Licensee.  This
License Agreement does not grant permission to use CNRI trademarks or
trade name in a trademark sense to endorse or promote products or
services of Licensee, or any third party.

8. By clicking on the "ACCEPT" button where indicated, or by copying,
installing or otherwise using Python 1.6.1, Licensee agrees to be
bound by the terms and conditions of this License Agreement.

        ACCEPT


CWI LICENSE AGREEMENT FOR PYTHON 0.9.0 THROUGH 1.2
--------------------------------------------------

Copyright (c) 1991 - 1995, Stichting Mathematisch Centrum Amsterdam,
The Netherlands.  All rights reserved.

Permission to use, copy, modify, and distribute this software and its
documentation for any purpose and without fee is hereby granted,
provided that the above copyright notice appear in all copies and that
both that copyright notice and this permission notice appear in
supporting documentation, and that the name of Stichting Mathematisch
Centrum or CWI not be used in advertising or publicity pertaining to
distribution of the software without specific, written prior
permission.

STICHTING MATHEMATISCH CENTRUM DISCLAIMS ALL WARRANTIES WITH REGARD TO
THIS SOFTWARE, INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND
FITNESS, IN NO EVENT SHALL STICHTING MATHEMATISCH CENTRUM BE LIABLE
FOR ANY SPECIAL, INDIRECT OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT
OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
```
