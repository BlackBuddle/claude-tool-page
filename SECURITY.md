# 보안 정책 (Security Policy)

> 이 문서는 법률 자문이 아니고, 변호사의 검토를 받은 문서도 아니에요. 회사 업무·영리 목적 등으로 쓰거나 배포하기 전에는 전문가의 검토를 받으세요.
>
> *This document is not legal advice and has not been reviewed by a lawyer. Get professional advice before any business or commercial use or distribution.*

> **이 문서는 소스 저장소에 있는 복사본이에요.** 소스 저장소에는 외부 사람이 접근하지 못하므로, 보안 문제는 아래 2절처럼 **공개 저장소(소개 페이지 저장소 `claude-tool-page`)의 Security 탭**으로 알려 주세요.
>
> *This is the copy kept in the source repository. Outsiders cannot access the source repository, so report security problems through the **Security tab of the public repository (the introduction-page repository `claude-tool-page`)**, as described in Section 2.*

ClaudeTool은 한 사람이 만드는 개인 프로젝트예요. 취약점을 알려 주시면 고맙게 살펴볼게요. 다만 아래 "약속하지 않는 것"도 함께 읽어 주세요. 한국어본과 영어본이 함께 있고, 뜻이 다르면 한국어본이 우선해요. 함께 읽으면 좋은 문서: [DISCLAIMER.md](DISCLAIMER.md)(면책과 알려진 한계), [PRIVACY.md](PRIVACY.md)(개인정보), [LICENSE](LICENSE), [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

*ClaudeTool is a personal project made by one person. I am grateful for vulnerability reports and will look into them, but please also read "What is not promised" below. A Korean and an English version are provided; if they differ, the Korean version prevails. See also: [DISCLAIMER.md](DISCLAIMER.md) (disclaimer and known limits), [PRIVACY.md](PRIVACY.md) (privacy), [LICENSE](LICENSE), [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).*

---

## 한국어

### 1. 지원하는 버전

- 보안 수정은 **가장 최근에 배포한 판**에만 해요. 이전 판은 지원하지 않아요. 새 설치 파일은 공개 저장소(`claude-tool-page`)의 릴리스에서 받아 덮어 설치해 최신으로 쓰세요. 0.4.2부터는 앱이 새 판을 알려 줘요(설정 › 일반, 자동 확인은 끌 수 있어요). 0.4.1 이하는 새 판을 알리지 못하니 0.4.2는 한 번 직접 설치해 주세요.
- 앱 안 업데이트는 공개 저장소의 HTTPS 주소에서만 설치 파일을 받아 `latest.yml`에 기록된 해시(sha512)와 맞을 때만 설치해요. 설치 파일에는 코드 서명이 없어서 이 해시는 전송 중 손상·변조를 막을 뿐 저장소 자체가 침해된 경우까지는 막지 못해요([DISCLAIMER.md](DISCLAIMER.md)의 3.1). 업데이트 주소는 빌드 때 정해지고 앱 화면·플러그인·설정 파일로 바꿀 수 없어요. 내려받기와 설치는 사용자가 [받기]와 [다시 시작해서 설치]를 눌러야 해요.
- 쓰고 있는 판은 설정 창 › 일반의 "버전"이나 설치 파일 이름(`ClaudeTool-Setup-<버전>.exe`)에서 알 수 있어요.

### 2. 보안 문제를 알리는 방법

1. 공개 저장소 `claude-tool-page`의 **Security 탭 → "Report a vulnerability"** 로 알려 주세요. 바로 가기: <https://github.com/BlackBuddle/claude-tool-page/security/advisories/new> (비공개로 접수돼요. 신고 양식을 열려면 GitHub 계정으로 로그인해야 해요.)
2. **공개 이슈·토론·SNS 등에는 취약점 내용을 올리지 마세요.** 고쳐지기 전에 공개되면 쓰는 사람들이 위험해져요.
3. 보안과 상관없는 버그나 질문은 공개 저장소 `claude-tool-page`의 Issues에 올려 주세요.

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
- **세션 열기(`session` 권한):** 플러그인이 정하지 못해야 할 주소·명령·폴더·인자를 정하게 되는 것, 들어오는 연결로 받은 적 없는 세션을 여는 것, 버튼 클릭 없이 열리는 것
- **알림 훅 설치 도우미:** `settings.json`의 다른 설정·훅을 지우거나 바꾸는 것, `<데이터>\claude-notify`의 토큰·백업이 다른 Windows 계정에 읽히게 되는 것
- **훅 연결(`hooks` 권한):** 플러그인 코드가 Claude Code 설정 파일에 직접 닿거나 훅의 내용·넣을 곳을 정하게 되는 것, 사용자가 [연결]을 누르기 전에 훅이 들어가는 것, 다른 훅·설정이나 다른 플러그인의 훅이 지워지거나 바뀌는 것, 토큰 없이 또는 웹 페이지·다른 기기에서 훅 통로(`/v1/hooks/<플러그인 id>`)에 보낼 수 있는 것, 선언하지 않은 이벤트가 플러그인에 전달되는 것, `<데이터>\hooks\<플러그인 id>`의 토큰·백업이 다른 Windows 계정에 읽히게 되는 것(토큰은 평문 파일이고 같은 계정의 다른 프로그램이 읽는 것은 알려진 한계예요)
- **승인 카드(`run`·`files` 쓰기·`open-app`):** 플러그인이 사용자의 버튼 눌림 없이 허용을 얻는 것, 카드를 위장하거나 가리거나 닫아 묻지 않고 실행하는 것, 카드에 보이는 요약과 실제 실행·쓰기·열기 내용이 다른 것(숨은 글자로 가리기나 요약 잘림을 이용한 우회), "늘 허용"이 사용자의 클릭 없이 켜지는 것, 승인 기록이나 로그에 가리기로 한 모양의 비밀이 그대로 남는 것
- **프로그램 실행(`run`):** 선언하지 않은 프로그램이 실행되는 것, 인자·명령줄 주입(`.cmd`를 거치는 길 포함), 앱이 찾았거나 사용자가 지정한 경로가 아닌 파일이 실행되는 것, 플러그인을 끄거나 지운 뒤에도 실행 중인 프로세스가 남는 것
- **파일(`files`):** 고른 폴더 밖을 읽거나 쓰는 것(`..`·절대 경로·링크·접합점·대체 데이터 스트림·예약 이름 등), 승인 카드 없이 쓰는 것, 고르지 않은 폴더에 닿는 것, 읽기·쓰기 크기와 횟수 한도를 피하는 것
- **AI(`ai`)와 OpenAI 호환 서버 연결:** `ai` 권한 없이 AI를 부르는 것, 월 예산이나 동시 호출 한도를 피하는 것, 서버 키가 플러그인·로그·설정 파일로 새거나 저장한 주소가 아닌 곳으로 보내지는 것, 서버가 돌려보낸 다른 주소로 키가 넘어가는 것, 보낸 글이나 받은 글이 로그에 남는 것
- **Codex 연결(`hooks`의 `codex` 대상):** `config.toml`의 다른 설정이나 다른 알림 명령을 지우거나 바꾸는 것, 사용자가 [연결]을 누르기 전에 쓰는 것, 플러그인 코드가 알림 명령의 내용이나 넣을 곳을 정하게 되는 것, 선언하지 않은 소식이 플러그인에 전달되는 것
- **앱 열기(`open-app`):** 실행 파일이나 스크립트가 열리는 것, 승인 카드 없이 열리는 것
- **앱 안 업데이트:** 해시 검사를 건너뛰거나 속일 수 있는 것, 업데이트 주소나 공급자를 앱 화면·플러그인·설정 파일로 바꿀 수 있는 것, 사용자가 누르지 않았는데 내려받기·설치가 일어나는 것, 로그에 서명된 임시 주소가 남는 것
- **보통 권한과 시작 시 실행:** `open-link`가 사용자의 클릭 없이 열리거나 https가 아닌 주소를 여는 것, `secrets`의 값이 다른 플러그인·로그·내보내기 파일로 새는 것, `notify`·`clipboard-write`가 한도와 길이 제한을 넘는 것, 허락 없이 레지스트리 `Run` 항목이 써지는 것
- **비밀 저장:** `secrets.bin`의 키·토큰·비밀 값이 로그·화면·내보내기 파일·설정 파일로 새는 것
- **가져오기(zip):** 압축을 푸는 동안의 경로 탈출·압축 폭탄, 허용하지 않는 파일이 들어오는 것
- **Claude Code 연결:** 연결·해제 흐름이 Claude Code 설정 파일을 의도하지 않게 바꾸는 것

**범위 밖 — 받아 보지만 이 정책의 대상은 아니에요**

- Anthropic·Claude Code·GitHub 같은 **제3자 서비스**의 취약점 → 그 서비스에 신고해 주세요.
- **Electron·Chromium·Node.js·Windows** 자체의 취약점 → 그쪽 프로젝트에 신고해 주세요. 다만 ClaudeTool이 그것을 잘못 써서 생긴 문제는 범위 안이에요.
- **사용자가 동의 창에서 허락한 플러그인의 의도된 동작**(동의한 주소로 데이터를 보내는 것, 허락한 권한으로 말풍선을 띄우거나 펫을 움직이거나 Claude Code 세션을 열거나 알림·링크·클립보드·훅을 쓰거나 AI를 부르는 것, 승인 카드에서 허용한 명령·파일 쓰기·앱 열기의 결과 등)
- **알려진 한계**로 [DISCLAIMER.md](DISCLAIMER.md)에 적어 둔 것(DNS 조회로 적은 양의 정보가 새는 것, 선언한 이름이 내부망 주소로 풀리는 것, 켠 플러그인마다 메모리를 쓰는 것, 같은 Windows 계정의 다른 프로그램이 `secrets.bin`을 읽을 수 있는 것, 승인 카드의 요약이 300자에서 잘리는 것과 카드가 가리는 비밀이 세 가지 모양뿐인 것, 카드의 경로 표시가 Windows 짧은 이름이나 비슷한 글자를 가려내지 못하는 것, `files` 읽기에 승인 카드가 없는 것, 허락한 프로그램이 하는 일을 앱이 막지 못하는 것 등). 이미 알려진 것보다 큰 영향이나 새로운 우회라면 알려 주세요.
- 플러그인 **자기 창이 CPU·메모리를 많이 쓰는 것**(앱 본체나 다른 플러그인에 닿지 않는 경우)
- 이 PC에 **직접 접근하거나 관리자 권한이 있어야 하는** 공격, 사용자를 속여 설치하게 하는 사회공학, 코드 서명이 없어서 뜨는 Windows SmartScreen 경고

### 4. 신고를 받은 뒤

- 개인이 만드는 무료 프로젝트라 **최선을 다해(best effort)** 살펴봐요.
- **약속하지 않는 것:** 응답이나 수정 시점·기한, 수정 여부, 보상(현상금 등). 보상은 없어요.
- 재현이 안 되거나 더 알아야 하면 신고 창에서 되물을 수 있어요.
- 수정이 나오면 새 판의 안내나 GitHub의 보안 권고(Security advisories)로 알릴 수 있어요.
- 신고한 분의 정보는 신고를 처리하는 데만 쓰고, 원하지 않으면 이름을 밝히지 않아요.

### 5. 책임 있는 공개(조율된 공개)

- 세부 내용은 **신고한 날부터 90일이 지난 때**와 **수정판이 나오고 쓰는 사람들이 업데이트할 시간을 둔 때** 가운데 더 이른 때부터 공개해 주세요. 그 전에는 공개하지 말아 주세요. 수정에 시간이 더 필요하거나 더 일찍 공개해야 할 사정이 있으면 신고 안에서 기간을 협의해요(협의 가능). 이 90일은 공개를 미뤄 달라는 부탁일 뿐, 그 안에 수정하겠다는 약속이 아니에요.
- 확인은 **자기 PC·자기 계정·자기 데이터**로만 해 주세요. 다른 사람의 PC·계정·데이터에 접근하거나 서비스를 방해하지 마세요. 확인에 꼭 필요한 만큼만 해 보고, 우연히 알게 된 개인 정보는 보관하거나 공개하지 마세요.

### 6. 사용자가 사고를 의심한다면

키나 토큰이 샜을 수 있다면 [DISCLAIMER.md](DISCLAIMER.md)의 3.5처럼, (의심 가는 플러그인을 끄고) 앱 종료 → 키 폐기와 재발급 → 계정 비밀번호 변경 → 데이터 폴더의 `logs` 확인 순서로 해 주세요.

### 7. 승인 카드가 하는 일과 못 하는 일

`run`·`files`의 쓰기·`open-app`은 행동하기 전에 승인 카드로 사용자에게 물어요. 신고하기 전에 카드가 무엇을 보증하고 무엇을 보증하지 않는지 알아 두면 좋아요.

- **카드는 앱이 직접 띄우는 말풍선(panel)이에요.** 소유자는 앱이고 플러그인은 카드를 만들거나 내용·버튼·결과를 정할 수 없어요. `run.exec` 같은 호출의 결과로 앱이 띄울 뿐이에요. **허용은 사용자가 그 카드의 버튼을 누를 때만** 일어나요. 플러그인이 자기 말풍선에 카드처럼 생긴 글을 그려도 그것은 승인이 아니에요. 카드는 치던 앱의 포커스를 빼앗지 않아요.
- **카드의 글은 앱이 만들어요.** 제목은 앱이 만든 글이고 플러그인 이름의 마크다운 기호는 효력이 없어요. 요약(명령줄·경로)도 앱이 만든 글이며 보이지 않는 글자는 드러내고 비밀처럼 보이는 세 가지 모양은 가리고 300자에서 잘라요. [자세히]는 1000자까지 보여 줘요.
- **기본은 거부예요.** 60초 안에 버튼을 누르지 않으면 거부돼요. 펫이 숨겨져 있거나 플러그인마다 대기 요청이 5개를 넘거나 플러그인이 멈추거나 앱이 끝나도 거부돼요.
- **"늘 허용"은 카드의 버튼으로만 켜져요.** 설정 창에서 켜는 스위치는 없어요. 켜진 플러그인은 설정 창 상세 칸에 빨간 줄로 보이고 [끄기]로 꺼요. 켜는 순간 이후 그 종류의 행동은 카드 없이 실행돼요.
- **카드가 보증하지 않는 것:** 허용한 뒤 프로그램이 하는 일, 카드에 다 보이지 않은 긴 명령의 뒷부분, 비슷한 글자나 Windows 짧은 이름으로 다른 곳을 가리키는 경로, 세 가지 모양 밖의 비밀이에요. 이런 한계는 [DISCLAIMER.md](DISCLAIMER.md)의 3.4에도 적혀 있어요. 이미 알려진 것보다 큰 영향이나 카드를 건너뛰는 새로운 길을 찾았다면 알려 주세요.

---

## English

*A courtesy translation. If it differs from the Korean version, the Korean version prevails.*

### 1. Supported versions

- Security fixes are made **only for the most recently distributed version**. Older versions are not supported. When you get a new installer from the Releases of the public repository (`claude-tool-page`), install it over the old one to stay current. From 0.4.2 the app tells you about a new version (Settings › General; the automatic check can be turned off). Versions 0.4.1 and older cannot announce new versions, so please install 0.4.2 yourself once.
- The in-app update downloads the installer only from an HTTPS address of the public repository and installs it only if it matches the hash (sha512) recorded in `latest.yml`. The installer has no code signature, so this hash only guards against damage or tampering in transit and does not protect against a compromise of the repository itself (3.1 of [DISCLAIMER.md](DISCLAIMER.md)). The update address is fixed at build time and cannot be changed from an app screen, a plugin or a settings file, and downloading and installing require you to press [Download] and [Restart and install].
- You can see your version in Settings › General ("Version") or in the installer file name (`ClaudeTool-Setup-<version>.exe`).

### 2. How to report a security problem

1. Use the **Security tab → "Report a vulnerability"** of the public repository `claude-tool-page`. Direct link: <https://github.com/BlackBuddle/claude-tool-page/security/advisories/new> (it is received privately; you must be signed in to GitHub to open the form).
2. **Do not post vulnerability details in public issues, discussions or social media.** If details are published before a fix, the people using the software are put at risk.
3. For bugs or questions unrelated to security, please use the Issues of the public repository `claude-tool-page`.

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
- **Opening sessions (`session` permission):** a plugin getting to choose the address, command, folder or arguments that it must not choose, opening a session it never received through incoming connections, or opening one without a button click
- **The notification-hook setup helper:** deleting or changing other settings or hooks in `settings.json`, or the token and backups in `<data>\claude-notify` becoming readable by another Windows account
- **Hook connection (`hooks` permission):** plugin code reaching the Claude Code settings file directly or choosing what the hooks contain or where they go, hooks being put in before you press [Connect], other hooks or settings or another plugin's hooks being deleted or changed, being able to send to the hook channel (`/v1/hooks/<plugin id>`) without a token or from a web page or another device, an undeclared event being delivered to a plugin, the token and backups in `<data>\hooks\<plugin id>` becoming readable by another Windows account (the token is a plain file, and other programs under the same account being able to read it is a known limit)
- **Approval cards (`run`, `files` writing, `open-app`):** a plugin getting an allow without your pressing a button, disguising, covering or closing a card to act without asking, what the card summary shows differing from what is actually run, written or opened (workarounds that hide text with invisible characters or exploit the summary being cut off), "Always allow" being turned on without your click, a secret of a shape that is supposed to be masked remaining as it is in the approval record or log
- **Running programs (`run`):** a program that was not declared being run, argument or command-line injection (including the path through `.cmd`), a file other than the one the app found or you specified being run, a running process remaining after the plugin is turned off or deleted
- **Files (`files`):** reading or writing outside the chosen folder (`..`, absolute paths, links, junctions, alternate data streams, reserved names and so on), writing without an approval card, reaching a folder you did not choose, bypassing the size and rate limits for reading and writing
- **AI (`ai`) and the OpenAI-compatible server connection:** calling an AI without the `ai` permission, bypassing the monthly budget or the concurrent-call limit, the server key leaking into a plugin, the log or a settings file or being sent anywhere other than the address it was saved for, the key being passed on to another address the server redirects to, sent or received text remaining in the log
- **Codex connection (the `codex` target of `hooks`):** deleting or changing other settings or another notification command in `config.toml`, writing before you press [Connect], plugin code choosing what the notification command contains or where it goes, an undeclared event being delivered to a plugin
- **Opening apps (`open-app`):** an executable or script being opened, opening without an approval card
- **In-app update:** being able to skip or fool the hash check, being able to change the update address or provider from an app screen, a plugin or a settings file, a download or installation happening without your pressing, a signed temporary address being left in the log
- **Ordinary permissions and starting with Windows:** `open-link` opening without your click or opening a non-https address, a value of `secrets` leaking into another plugin, the log or an exported file, `notify` or `clipboard-write` exceeding their rate or length limits, a registry `Run` entry being written without your permission
- **Secret storage:** keys, tokens or secret values in `secrets.bin` leaking into logs, screens, exported files or the settings file
- **Importing (zip):** path escape or zip bombs while extracting, files that should not be allowed getting in
- **Connecting Claude Code:** the connect/disconnect flow changing the Claude Code settings file in unintended ways

**Out of scope — I will take a look, but they are not covered by this policy**

- Vulnerabilities in **third-party services** such as Anthropic, Claude Code and GitHub → please report them to that service.
- Vulnerabilities in **Electron, Chromium, Node.js or Windows** themselves → please report them to those projects. Problems caused by ClaudeTool using them incorrectly are in scope.
- **Intended behavior of a plugin you allowed in the consent window** (sending data to the addresses you consented to, showing speech bubbles, moving the pet, opening Claude Code sessions or using notifications, links, the clipboard or hooks or calling an AI with the permissions you granted, and the result of a command, file write or app opening you allowed on an approval card, etc.)
- **Known limits** listed in [DISCLAIMER.md](DISCLAIMER.md) (a small amount of information leaking through DNS lookups, declared names resolving to internal-network addresses, memory used by each plugin that is on, other programs under the same Windows account being able to read `secrets.bin`, an approval card summary being cut off at 300 characters and the card masking only three shapes of secret, the path shown on a card not telling Windows short names or look-alike characters apart, there being no approval card for reading with `files`, the app being unable to block what a program you allowed does, etc.). If you find a bigger impact than already known, or a new bypass, please report it.
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

### 7. What the approval card does and does not do

`run`, writing with `files` and `open-app` ask you with an approval card before they act. Before you report, it helps to know what the card does and does not guarantee.

- **The card is a speech bubble (panel) that the app shows itself.** The app is its owner, and a plugin cannot create a card or decide its contents, buttons or outcome. The app shows it only as a result of a call such as `run.exec`. **An allow happens only when you press a button on that card.** If a plugin draws text that looks like a card in its own speech bubble, that is not an approval. The card does not take focus away from the app you were typing in.
- **The text on the card is made by the app.** The title is text the app made, and Markdown symbols in the plugin name have no effect. The summary (command line or path) is also made by the app: invisible characters are revealed, three secret-looking shapes are masked and it is cut at 300 characters. [Details] shows up to 1,000 characters.
- **The default is deny.** If you do not press a button within 60 seconds it is denied. It is also denied if the pet is hidden, if more than 5 requests are waiting for a plugin, if the plugin stops or if the app ends.
- **"Always allow" is turned on only with a button on the card.** There is no switch in the settings window to turn it on. A plugin with it on is shown with a red line in the detail area of the settings window and is turned off with [Turn off]. From the moment it is on, actions of that kind run without a card.
- **What the card does not guarantee:** what a program does after you allowed it, the later part of a long command that the card does not fully show, a path that points elsewhere through look-alike characters or a Windows short name, and a secret in a shape outside the three. These limits are also written in 3.4 of [DISCLAIMER.md](DISCLAIMER.md). If you find a bigger impact than already known, or a new way around the card, please report it.
