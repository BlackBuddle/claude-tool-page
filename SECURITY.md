# 보안 정책 (Security Policy)

> 이 문서는 법률 자문이 아니고 변호사의 검토를 받은 문서도 아니에요. 회사 업무·영리 목적 등으로 쓰거나 배포하기 전에는 전문가의 검토를 받으세요.
>
> *This document is not legal advice and has not been reviewed by a lawyer. Get professional advice before any business or commercial use or distribution.*

ClaudeTool은 한 사람이 만드는 개인 프로젝트예요. 취약점을 알려 주시면 고맙게 살펴볼게요. 다만 아래 "약속하지 않는 것"도 함께 읽어 주세요. 한국어본과 영어본이 함께 있고 뜻이 다르면 한국어본이 우선해요. 함께 읽으면 좋은 문서: [DISCLAIMER.md](DISCLAIMER.md)(면책과 알려진 한계), [PRIVACY.md](PRIVACY.md)(개인정보), [LICENSE](LICENSE), [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

*ClaudeTool is a personal project made by one person. I am grateful for vulnerability reports and will look into them, but please also read "What is not promised" below. A Korean and an English version are provided; if they differ, the Korean version prevails. See also: [DISCLAIMER.md](DISCLAIMER.md) (disclaimer and known limits), [PRIVACY.md](PRIVACY.md) (privacy), [LICENSE](LICENSE), [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).*

---

## 한국어

### 1. 지원하는 버전

- 보안 수정은 **가장 최근에 배포한 판**에만 해요. 이전 판은 지원하지 않아요. 새 설치 파일은 공개 저장소(`claude-tool-page`)의 릴리스에서 받아 덮어 설치해 최신으로 쓰세요.
- 쓰고 있는 판은 설정 창 › 일반의 "버전"이나 설치 파일 이름(`ClaudeTool-Setup-<버전>.exe`)에서 알 수 있어요.

### 2. 보안 문제를 알리는 방법

1. 이 저장소의 **Security 탭 → "Report a vulnerability"** 로 알려 주세요. 바로 가기: <https://github.com/BlackBuddle/claude-tool-page/security/advisories/new> (비공개로 접수돼요. 신고 양식을 열려면 GitHub 계정으로 로그인해야 해요.)
2. **공개 이슈·토론·SNS 등에는 취약점 내용을 올리지 마세요.** 고쳐지기 전에 공개되면 쓰는 사람들이 위험해져요.
3. 보안과 상관없는 버그나 질문은 이 저장소의 Issues에 올려 주세요.

**신고에 담으면 좋은 것**

- 쓰고 있는 ClaudeTool 버전과 Windows 버전
- 무엇이 문제인지 한두 문장
- 재현 순서(가능하면 아주 작은 예. 플러그인 문제라면 `plugin.json`과 문제가 되는 최소한의 코드)
- 영향: 이 문제로 무엇을 할 수 있게 되는지(어떤 정보가 새는지, 무엇에 닿는지)
- 알고 있다면 피하는 방법이나 고치는 방법

**보내지 마세요:** 실제 API 키·Admin 키·토큰·비밀번호나 개인 문서. 이미 노출된 키가 있다면 먼저 폐기하세요. 로그를 붙일 때는 경로·이름 같은 개인 정보를 지워 주세요.

### 3. 범위

**범위 안 — 알려 주세요**

- **앱 본체와 설치 프로그램:** 앱이 파일·설정·키를 다루는 방식(예: 허락 없이 다른 곳의 파일을 쓰거나 덮어쓰는 것, 경로 탈출), 설치·제거 프로그램이 일으키는 문제
- **플러그인 격리와 동의:** 플러그인이 동의하지 않은 권한·주소를 쓰거나, 자기 폴더 밖의 파일·다른 플러그인·앱 화면의 내용에 닿거나, 격리된 창 밖으로 나오는 것. 동의 창이 실제 권한·주소와 다르게 보이는 것(문구 속임), 가짜 로그인 창처럼 사용자를 속이는 표시. 플러그인이 앱 본체나 다른 플러그인을 멈추게 하는 것
- **들어오는 연결:** 토큰 없이, 또는 웹 페이지·다른 기기에서 통로에 보낼 수 있는 것, 토큰 검사·횟수 제한을 피하는 것, `127.0.0.1` 밖으로 열리는 것
- **비밀 저장:** `secrets.bin`의 키·토큰·비밀 값이 로그·화면·내보내기 파일·설정 파일로 새는 것
- **가져오기(zip):** 압축을 푸는 동안의 경로 탈출·압축 폭탄, 허용하지 않는 파일이 들어오는 것
- **Claude Code 연결:** 연결·해제 흐름이 Claude Code 설정 파일을 의도하지 않게 바꾸는 것

**범위 밖 — 받아 보지만 이 정책의 대상은 아니에요**

- Anthropic·Claude Code·GitHub 같은 **제3자 서비스**의 취약점 → 그 서비스에 신고해 주세요.
- **Electron·Chromium·Node.js·Windows** 자체의 취약점 → 그쪽 프로젝트에 신고해 주세요. 다만 ClaudeTool이 그것을 잘못 써서 생긴 문제는 범위 안이에요.
- **사용자가 동의 창에서 허락한 플러그인의 의도된 동작**(동의한 주소로 데이터를 보내는 것, 허락한 권한으로 말풍선을 띄우거나 펫을 움직이는 것 등)
- **알려진 한계**로 [DISCLAIMER.md](DISCLAIMER.md)에 적어 둔 것(DNS 조회로 적은 양의 정보가 새는 것, 선언한 이름이 내부망 주소로 풀리는 것, 켠 플러그인마다 메모리를 쓰는 것, 같은 Windows 계정의 다른 프로그램이 `secrets.bin`을 읽을 수 있는 것 등). 이미 알려진 것보다 큰 영향이나 새로운 우회라면 알려 주세요.
- 플러그인 **자기 창이 CPU·메모리를 많이 쓰는 것**(앱 본체나 다른 플러그인에 닿지 않는 경우)
- 이 PC에 **직접 접근하거나 관리자 권한이 있어야 하는** 공격, 사용자를 속여 설치하게 하는 사회공학, 코드 서명이 없어서 뜨는 Windows SmartScreen 경고

### 4. 신고를 받은 뒤

- 개인이 만드는 무료 프로젝트라 **최선을 다해(best effort)** 살펴봐요.
- **약속하지 않는 것:** 응답이나 수정 시점·기한, 수정 여부, 보상(현상금 등). 보상은 없어요.
- 재현이 안 되거나 더 알아야 하면 신고 창에서 되물을 수 있어요.
- 수정이 나오면 새 판의 안내나 GitHub의 보안 권고(Security advisories)로 알릴 수 있어요.
- 신고한 분의 정보는 신고를 처리하는 데만 쓰고 원하지 않으면 이름을 밝히지 않아요.

### 5. 책임 있는 공개(조율된 공개)

- 세부 내용은 **신고한 날부터 90일이 지난 때**와 **수정판이 나오고 쓰는 사람들이 업데이트할 시간을 둔 때** 가운데 더 이른 때부터 공개해 주세요. 그 전에는 공개하지 말아 주세요. 수정에 시간이 더 필요하거나 더 일찍 공개해야 할 사정이 있으면 신고 안에서 기간을 협의해요(협의 가능). 이 90일은 공개를 미뤄 달라는 부탁일 뿐, 그 안에 수정하겠다는 약속이 아니에요.
- 확인은 **자기 PC·자기 계정·자기 데이터**로만 해 주세요. 다른 사람의 PC·계정·데이터에 접근하거나 서비스를 방해하지 마세요. 확인에 꼭 필요한 만큼만 해 보고 우연히 알게 된 개인 정보는 보관하거나 공개하지 마세요.

### 6. 사용자가 사고를 의심한다면

키나 토큰이 샜을 수 있다면 [DISCLAIMER.md](DISCLAIMER.md)의 3.5처럼, (의심 가는 플러그인을 끄고) 앱 종료 → 키 폐기와 재발급 → 계정 비밀번호 변경 → 데이터 폴더의 `logs` 확인 순서로 해 주세요.

---

## English

*A courtesy translation. If it differs from the Korean version, the Korean version prevails.*

### 1. Supported versions

- Security fixes are made **only for the most recently distributed version**. Older versions are not supported. When you get a new installer from the Releases of the public repository (`claude-tool-page`), install it over the old one to stay current.
- You can see your version in Settings › General ("Version") or in the installer file name (`ClaudeTool-Setup-<version>.exe`).

### 2. How to report a security problem

1. Use this repository's **Security tab → "Report a vulnerability"**. Direct link: <https://github.com/BlackBuddle/claude-tool-page/security/advisories/new> (it is received privately; you must be signed in to GitHub to open the form).
2. **Do not post vulnerability details in public issues, discussions or social media.** If details are published before a fix, the people using the software are put at risk.
3. For bugs or questions unrelated to security, please use this repository's Issues.

**What is helpful to include**

- The ClaudeTool version you use and your Windows version
- One or two sentences on what the problem is
- Steps to reproduce (a very small example if possible; for a plugin problem, the `plugin.json` and the minimal code that causes it)
- Impact: what this problem lets someone do (what information leaks, what it can reach)
- Any workaround or fix you know of

**Please do not send:** real API keys, Admin keys, tokens, passwords or personal documents. If a key has already been exposed, revoke it first. When attaching logs, remove personal information such as paths and names.

### 3. Scope

**In scope — please report**

- **The app itself and its installer:** how it handles files, settings and keys (for example, writing or overwriting files elsewhere without permission, path escape), and problems caused by the installer or uninstaller
- **Plugin isolation and consent:** a plugin using permissions or addresses you did not consent to, reaching files outside its own folder, other plugins or the content of app screens, or breaking out of its isolated window; a consent window that shows something different from the real permissions or addresses (wording tricks), or displays that deceive users such as a fake login window; a plugin stopping the app itself or other plugins
- **Incoming connections:** being able to send to the channel without a token or from a web page or another device, bypassing the token check or rate limit, the channel opening beyond `127.0.0.1`
- **Secret storage:** keys, tokens or secret values in `secrets.bin` leaking into logs, screens, exported files or the settings file
- **Importing (zip):** path escape or zip bombs while extracting, files that should not be allowed getting in
- **Connecting Claude Code:** the connect/disconnect flow changing the Claude Code settings file in unintended ways

**Out of scope — I will take a look, but they are not covered by this policy**

- Vulnerabilities in **third-party services** such as Anthropic, Claude Code and GitHub → please report them to that service.
- Vulnerabilities in **Electron, Chromium, Node.js or Windows** themselves → please report them to those projects. Problems caused by ClaudeTool using them incorrectly are in scope.
- **Intended behavior of a plugin you allowed in the consent window** (sending data to the addresses you consented to, showing speech bubbles or moving the pet with the permissions you granted, etc.)
- **Known limits** listed in [DISCLAIMER.md](DISCLAIMER.md) (a small amount of information leaking through DNS lookups, declared names resolving to internal-network addresses, memory used by each plugin that is on, other programs under the same Windows account being able to read `secrets.bin`, etc.). If you find a bigger impact than already known, or a new bypass, please report it.
- A plugin's **own window using a lot of CPU or memory** (when it does not reach the app itself or other plugins)
- Attacks that require **physical access to this PC or administrator rights**, social engineering that tricks you into installing, and the Windows SmartScreen warning shown because the installer is not code-signed

### 4. After you report

- This is a free project made by an individual, so I look at reports on a **best-effort** basis.
- **What is not promised:** a response or fix time or deadline, whether a fix will be made, or any reward (bounty, etc.). There is no reward.
- If I cannot reproduce it or need to know more, I may ask you in the report.
- When a fix is released, it may be announced in the release notes or in a GitHub security advisory.
- Your information is used only to handle the report, and I will not reveal your name if you prefer.

### 5. Responsible disclosure

- Please do not disclose details until the **earlier** of **90 days after you report** and **the time when a fixed version is out and users have had time to update**. If more time is needed for a fix, or there is a reason to disclose earlier, the period can be discussed within the report (negotiable). The 90 days is a request to hold off disclosure, not a promise to fix within that time.
- Test **only with your own PC, your own account and your own data.** Do not access other people's PCs, accounts or data, and do not disrupt services. Do only as much as is needed to confirm the issue, and do not keep or disclose personal information you come across by accident.

### 6. If you suspect an incident as a user

If keys or tokens may have leaked, follow 3.5 of [DISCLAIMER.md](DISCLAIMER.md): (turn off the suspicious plugin and) quit the app → revoke and reissue keys → change account passwords → check the `logs` folder in the data folder.
