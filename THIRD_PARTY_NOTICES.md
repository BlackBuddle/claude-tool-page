# 제3자 소프트웨어 고지 (Third-Party Notices)

> 이 문서는 법률 자문이 아니고, 변호사의 검토를 받은 문서도 아니에요. 회사 업무·영리 목적 등으로 쓰거나 배포하기 전에는 전문가의 검토를 받으세요.
>
> *This document is not legal advice and has not been reviewed by a lawyer. Get professional advice before any business or commercial use or distribution.*

ClaudeTool 0.4.1(2026-10-02 기준) 설치 파일에는 아래의 제3자 소프트웨어가 들어 있어요(이 문서는 설치 파일을 만들 때 들어가는 구성요소를 기준으로 해요). 이 소프트웨어들은 **각자의 라이선스를 따르고**, ClaudeTool의 라이선스([LICENSE](LICENSE))는 그 라이선스를 바꾸지 않아요(LICENSE 제5조). 목록은 설치 파일에 들어가는 구성요소의 `package.json`과 라이선스 파일에서 가져왔고, 새 판에서 바뀔 수 있어요. 설치·제거 프로그램 쪽(3절)은 확인하지 못한 부분이 있어요. 한국어본과 영어본이 함께 있고, 뜻이 다르면 한국어본이 우선해요. 라이선스 전문은 맨 아래 "라이선스 전문" 절에 원문 그대로(영어) 있어요. 함께 읽으면 좋은 문서: [DISCLAIMER.md](DISCLAIMER.md), [PRIVACY.md](PRIVACY.md), [SECURITY.md](SECURITY.md).

*The ClaudeTool 0.4.1 installer (as of 2026-10-02) contains the third-party software listed below (this document is based on the components that go into the installer when it is built). Each item **follows its own license**, and the ClaudeTool license ([LICENSE](LICENSE)) does not change those licenses (LICENSE Section 5). The list was taken from the `package.json` and license files of the components that go into the installer and may change in new versions. Part of the installer/uninstaller side (Section 3) could not be confirmed. A Korean and an English version are provided; if they differ, the Korean version prevails. The license texts are in the "License texts" section at the very bottom, in their original English. See also: [DISCLAIMER.md](DISCLAIMER.md), [PRIVACY.md](PRIVACY.md), [SECURITY.md](SECURITY.md).*

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

설치 폴더의 `node_modules`와 화면 코드에 들어가는 패키지예요. Anthropic SDK가 끌고 들어오는 하위 패키지도 모두 적었어요. 각 패키지의 라이선스 파일(`LICENSE`)은 설치 폴더의 `resources\app\node_modules\<패키지 이름>` 안에도 들어 있어요(`standardwebhooks`는 라이선스 파일이 없어요).

| 패키지 | 버전 | 라이선스 | 저작권 | 쓰임 |
|---|---|---|---|---|
| `@anthropic-ai/sdk` | 0.127.0 | MIT (일부 코드는 BSD-3-Clause, 아래 "라이선스 전문") | Copyright 2023 Anthropic, PBC. | 질문하기의 API 키 방식 |
| `@babel/runtime` | 7.29.7 | MIT | Copyright (c) 2014-present Sebastian McKenzie and other contributors | `json-schema-to-ts`의 하위 패키지 |
| `@stablelib/base64` | 1.0.1 | MIT | Copyright (C) 2016 Dmitry Chestnykh | `standardwebhooks`의 하위 패키지 |
| `fast-sha256` | 1.3.0 | Unlicense(퍼블릭 도메인) | 저작권을 주장하지 않아요(퍼블릭 도메인으로 공개됨) | `standardwebhooks`의 하위 패키지 |
| `fflate` | 0.8.3 | MIT | Copyright (c) 2026 Arjun Barrett | zip 가져오기·내보내기 |
| `json-schema-to-ts` | 3.1.1 | MIT | Copyright (c) 2020 Thomas Aribart | Anthropic SDK의 하위 패키지 |
| `preact` | 10.29.8 | MIT | Copyright (c) 2015-present Jason Miller | 화면(펫·말풍선·설정 창) |
| `standardwebhooks` | 1.1.1 | MIT(패키지 정보에 적힌 값) | 패키지에 라이선스 파일이 들어 있지 않아 저작권 줄을 확인하지 못했어요. 만든 곳: Standard Webhooks | Anthropic SDK의 하위 패키지 |
| `ts-algebra` | 2.0.0 | MIT | Copyright (c) 2020 Thomas Aribart | `json-schema-to-ts`의 하위 패키지 |
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

These are the packages in the install folder's `node_modules` and in the screen code, including every sub-package the Anthropic SDK pulls in. Each package's license file (`LICENSE`) is also included in the install folder under `resources\app\node_modules\<package name>` (`standardwebhooks` ships none).

| Package | Version | License | Copyright | Used for |
|---|---|---|---|---|
| `@anthropic-ai/sdk` | 0.127.0 | MIT (some code is BSD-3-Clause, see "License texts" below) | Copyright 2023 Anthropic, PBC. | The API-key method of asking questions |
| `@babel/runtime` | 7.29.7 | MIT | Copyright (c) 2014-present Sebastian McKenzie and other contributors | Sub-package of `json-schema-to-ts` |
| `@stablelib/base64` | 1.0.1 | MIT | Copyright (C) 2016 Dmitry Chestnykh | Sub-package of `standardwebhooks` |
| `fast-sha256` | 1.3.0 | Unlicense (public domain) | No copyright is claimed (released into the public domain) | Sub-package of `standardwebhooks` |
| `fflate` | 0.8.3 | MIT | Copyright (c) 2026 Arjun Barrett | Importing/exporting zip files |
| `json-schema-to-ts` | 3.1.1 | MIT | Copyright (c) 2020 Thomas Aribart | Sub-package of the Anthropic SDK |
| `preact` | 10.29.8 | MIT | Copyright (c) 2015-present Jason Miller | The screens (pet, speech bubbles, settings window) |
| `standardwebhooks` | 1.1.1 | MIT (as stated in the package metadata) | The package ships no license file, so the copyright line could not be confirmed. Made by: Standard Webhooks | Sub-package of the Anthropic SDK |
| `ts-algebra` | 2.0.0 | MIT | Copyright (c) 2020 Thomas Aribart | Sub-package of `json-schema-to-ts` |
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

**MIT License:** `@anthropic-ai/sdk`, `@babel/runtime`, `@stablelib/base64`, `fflate`, `json-schema-to-ts`, `preact`, `standardwebhooks`, `ts-algebra`, `zod`, Electron, electron-builder의 NSIS 템플릿. 저작권 표시는 위 표의 "저작권" 칸(Electron은 `LICENSE.electron.txt`, electron-builder의 NSIS 템플릿은 3절)을 보세요. *Copyright notices: see the "Copyright" column of the table above (for Electron, `LICENSE.electron.txt`; for electron-builder's NSIS templates, Section 3).*

**The Unlicense:** `fast-sha256`. **BSD 3-Clause:** `@anthropic-ai/sdk` 안의 쿼리 문자열 처리 코드 *(query-string code inside `@anthropic-ai/sdk`)*.

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
