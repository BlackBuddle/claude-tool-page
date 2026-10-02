# 개인정보 안내 (Privacy)

> 이 문서는 법률 자문이 아니고 변호사의 검토를 받은 문서도 아니에요. 회사 업무·영리 목적 등으로 쓰거나 배포하기 전에는 전문가의 검토를 받으세요.
>
> *This document is not legal advice and has not been reviewed by a lawyer. Get professional advice before any business or commercial use or distribution.*

ClaudeTool 0.4.0(2026-10-02 기준)이 이 PC에 무엇을 저장하고 무엇을 읽고 무엇을 밖으로 보내는지 정리한 안내예요. 소스 코드를 읽고 개발용 데이터 폴더와 설치 산출물(빌드 결과)을 점검해 쓴 것이고 실행 중인 앱의 통신을 캡처해 확인한 것은 아니에요. 앞으로 바뀔 수 있어요. 새 판은 저장소에 올린 때부터 그 뒤에 받거나 갱신하는 소프트웨어에 적용돼요. 이 문서는 이해를 돕는 안내이며 소프트웨어의 동작을 보증하는 것이 아니에요. 보증과 책임은 [DISCLAIMER.md](DISCLAIMER.md)를 따라요. 한국어본과 영어본이 함께 있고 뜻이 다르면 한국어본이 우선해요. 함께 읽으면 좋은 문서: [LICENSE](LICENSE), [SECURITY.md](SECURITY.md)(보안 문제 신고), [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)(제3자 소프트웨어).

*This is a guide to what ClaudeTool 0.4.0 (as of 2026-10-02) stores on this PC, reads, and sends out. It was written from reading the source code and inspecting a development data folder and the built installer output; the running app's network traffic was not captured. It may change; a new version applies from the time it is posted to Software received or updated after that time. It is an explanatory guide, not a guarantee of how the software behaves; warranties and liability follow [DISCLAIMER.md](DISCLAIMER.md). A Korean and an English version are provided; if they differ, the Korean version prevails. See also: [LICENSE](LICENSE), [SECURITY.md](SECURITY.md) (reporting security problems), [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) (third-party software).*

---

## 한국어

### 1. 한눈에 보기

- ClaudeTool은 **내 PC에서 돌아가는 앱**이에요. 앱은 저작권자가 운영하는 서버와 통신하지 않고 저작권자는 사용자의 질문·설정·사용 기록·키를 **받지 않아요.**
- ClaudeTool에는 **사용 통계·원격 분석·충돌 보고서 전송·자동 업데이트·새 판 확인** 기능이 없어요(소스 코드에서 네트워크 호출을 모두 찾아보고 분석·충돌 보고·업데이트와 관련된 부분이 없는 것을 확인했어요. 실행 중인 앱의 통신을 캡처해 확인한 것은 아니에요). 새 판은 설치 파일을 직접 받아 설치해요.
- 데이터는 이 PC의 **데이터 폴더**에만 저장돼요(2절). **질문과 답의 내용은 파일로 저장하지 않아요.**
- 확인한 범위에서 밖으로 나가는 길은 네 가지예요(5절): ① 질문하기, ② 조직 사용량(켠 경우만), ③ 설치한 플러그인이 동의받은 주소로 보내는 것(알려진 한계는 5.4), ④ 말풍선 안의 https 링크를 눌렀을 때 기본 브라우저가 열리는 것. 앱 창의 맞춤법 검사는 꺼 두어 사전을 내려받지 않아요(5.5). Electron·Chromium·Windows 같은 구성요소가 스스로 하는 일을 모두 보증하지는 못해요.
- 사용량을 보여 주려고 이 PC의 Claude Code 기록 파일을 **읽어요**(4절). 읽은 내용 가운데 모델 이름·시각·토큰 수만 쓰고 질문과 답의 내용은 저장하거나 보내지 않아요.

### 2. 내 PC에 저장되는 것

**데이터 폴더 위치**

- 설치 프로그램으로 설치했다면 설치 폴더 **옆**의 `<설치 폴더>-data`예요. 설치 폴더가 드라이브 맨 위(루트)라면 그 아래의 `ClaudeTool-data`예요.
- 설치 프로그램 없이 실행 파일만 두고 쓰면 실행 파일 옆의 `data` 폴더예요.
- 설정 창 › 일반의 "데이터 폴더 열기"·"로그 폴더 열기"로 열 수 있어요. 설치 프로그램으로 설치했다면 앱을 업데이트하거나 제거해도 이 폴더는 남아요.

**데이터 폴더 안**

| 위치 | 들어 있는 것 | 비고 |
|---|---|---|
| `settings.json` | 캐릭터 선택과 크기·투명도, 움직임, 돌아다니는 범위와 모니터, 말풍선 설정, 사용량 소스 켜기·끄기, 질문 방식·모델·(지정했다면) Claude Code 실행 파일 경로, 설치형 플러그인별 켜짐 여부·**일반 설정 값**·동의 기록(권한과 접속 주소)·창 위치, 들어오는 연결 포트 | 일반 설정 값은 암호화하지 않아요(비밀 칸만 `secrets.bin`에 암호화해요). 파일이 깨지면 `settings.json.bak-<시각>`으로 옮겨 두고 새로 만들어요. |
| `secrets.bin` | Anthropic API 키, Admin API 키, 플러그인의 비밀 칸 값, 들어오는 연결 토큰 | Windows 데이터 보호 기능(DPAPI)으로 파일 전체를 암호화해요. 풀지 못하면 `secrets.bin.unreadable-<시각>`으로 옮겨 두고 빈 상태로 시작해요. |
| `logs\app.log`, `logs\plugins.log` | 앱과 플러그인(내장 기능·설치형)의 로그 | 3절. 자동으로 지우거나 줄이지 않아요. |
| `packs\` | 내가 만들거나 가져온 캐릭터(그림 파일과 `pack.json`) | |
| `plugins\` | 설치한 플러그인의 파일(받은 zip을 푼 것, 또는 직접 넣은 폴더) | 가져오는 동안에는 `.staging` 임시 폴더가 잠깐 생겨요. |
| `plugin-data\<플러그인 id>.json` | 플러그인이 "저장 공간"에 저장한 값 | 암호화하지 않아요. 플러그인마다 1MB까지예요. |
| `usage\app-ledger.jsonl` | 이 앱이 보낸 질문의 사용 기록: 시각·모델 이름·토큰 수·방식(API 또는 Claude Code)·결과 | 질문과 답의 내용은 없어요. 자동으로 지우지 않아요. |
| `usage\subscription.json` | 구독 한도(5시간·7일)의 사용 비율·초기화 시각과 Claude Code 세션 번호(무작위 ID) | 4절 |
| `usage\cache\claude-code.json` | Claude Code 기록을 다시 읽지 않으려는 캐시: 읽은 기록 파일의 경로·크기·읽은 위치, 최근 8일치 응답별 모델·시각·토큰 수 | 파일 경로에 Claude Code가 만든 프로젝트 폴더 이름(작업 폴더 경로에서 만들어져요)이 들어 있어요. 몇 MB까지 커질 수 있어요. |
| `pricing.json` | 모델별 단가표(비용 추정용) | 앱이 기본값으로 만들어 두고 직접 고칠 수 있어요. |
| `backup\` | "Claude Code 연결"·"연결 해제"를 적용하기 전 Claude Code `settings.json`의 복사본 | 내 Claude Code 설정이 그대로 들어 있어요. 연결을 해제해도 남아요. |
| `claude-code-cwd\` | Claude Code로 질문할 때 쓰는 빈 작업 폴더 | |
| `electron\` | 앱 창이 쓰는 Chromium(브라우저 엔진)의 캐시·저장소·설정 | `secrets.bin`을 푸는 열쇠가 여기(`Local State`)에 있어서 이 폴더를 지우면 `secrets.bin`을 읽을 수 없게 돼요. 키를 다시 넣어야 해요. |

**저장하지 않는 것**

- **질문과 답의 내용.** 이어서 묻기 위해 앱이 켜져 있는 동안 **메모리에만** 최근 대화(최대 6번, 마지막 답 뒤 10분까지)를 기억하고 앱을 끄면 사라져요.
- **플러그인 창의 쿠키·브라우저 저장소.** 플러그인 창의 임시 저장소는 메모리에만 있어 앱을 끄면 사라져요. 디스크에 남는 플러그인 데이터는 `plugin-data`뿐이에요.
- **화면 내용·클립보드·키 입력.** 앱은 이것들을 수집하지 않아요. 전역 단축키는 질문하기용 하나(기본 `Ctrl+Alt+K`)만 등록하고 클립보드는 "토큰 복사"를 눌렀을 때 쓰기만 해요(읽지 않아요).

### 3. 로그에 남는 것과 남지 않는 것

- 로그는 `logs\app.log`(앱)와 `logs\plugins.log`(내장 기능과 설치형 플러그인)에 한 줄씩 덧붙여요. 자동으로 지우거나 줄이지 않아서 계속 커져요.
- **남는 것:** 시각과 한 줄 설명이에요. 앱 시작(데이터 폴더 경로가 들어가요), 켜진 기능의 이름, 단축키 등록 결과, 키·토큰을 저장하거나 지운 사실(어느 칸인지 이름만 적고 값은 적지 않아요), 오류·경고 문구(파일 경로가 들어갈 수 있어요), 플러그인 시작·멈춤(id·버전·이유), 플러그인이 막힌 연결 시도(주소의 앞부분(origin)만 적고 경로·쿼리·헤더·본문은 적지 않아요)와 실패한 나가는 연결(방식·origin·오류 코드), 들어오는 연결 통로를 열고 닫은 사실(`127.0.0.1`과 포트), 플러그인이 직접 적은 로그와 콘솔 경고·오류(분당 60줄·한 줄 2000자까지이며 무엇을 적을지는 플러그인이 정해요).
- **남기지 않게 만든 것:** 질문·답·시스템 프롬프트의 내용, API 키·Admin 키·비밀 칸 값·토큰의 값, 성공한 플러그인 요청. 다만 오류 문구에는 Anthropic 서버나 Claude Code가 돌려준 오류 설명이 그대로 들어갈 수 있고 플러그인이 비밀 값을 스스로 로그에 적으면 남아요.
- 로그를 남에게 보여 주거나 올리기 전에 경로·이름 같은 개인 정보가 들어 있는지 확인하세요.

### 4. 읽는 것

- **Claude Code 기록(사용량 보기).** 사용량 소스 "Claude Code"(기본으로 켜져 있어요)는 사용량 창을 열면(열려 있는 동안 1분마다) Claude Code 폴더(보통 사용자 폴더 아래 `.claude`, `CLAUDE_CONFIG_DIR`을 쓰면 그 폴더)의 `projects` 아래 `.jsonl` 파일을 찾아 읽어요(`tool-results` 폴더는 건너뛰어요). 파일을 읽지만 모델 이름·시각·응답 번호·토큰 수만 뽑아 쓰고 질문·답·도구 결과의 내용은 저장하거나 어디로 보내지 않아요. 트레이의 "사용량 소스"에서 끌 수 있어요.
- **Claude Code 설정 파일.** 사용량 창의 "Claude Code 연결"·"연결 해제"를 눌렀을 때만 Claude Code 폴더의 `settings.json`을 읽어요. 바뀔 내용을 보여 준 뒤 **적용**을 눌러야 고치고 고치기 전의 원본을 `backup\`에 복사해 둬요. 그 밖의 때는 읽지 않아요.
- **연결하면 일어나는 일.** Claude Code의 상태 줄(statusLine) 명령에 이 앱의 작은 스크립트가 등록돼요. Claude Code가 상태 줄을 그릴 때마다 시스템의 Node.js로 이 스크립트가 돌고 Claude Code가 넘겨 주는 상태 정보 가운데 **한도 사용 비율·초기화 시각·세션 번호만** `usage\subscription.json`에 적어요. 원래 쓰던 상태 줄 명령이 있었다면 같은 입력을 그 명령에도 넘겨 이어서 실행해요. 연결할 때 Node.js를 찾으려고 `where node`와 `node --version`을 실행해요. "연결 해제"를 누르면 원래대로 되돌려요.
- **찾아보는 곳.** Claude Code 실행 파일(`claude.exe`)을 찾으려고 `PATH`와 사용자 폴더의 `.local\bin`을 살펴봐요. Claude Code의 로그인·인증 파일은 읽지 않아요.

### 5. 밖으로 나가는 것

**5.1 질문하기 — Claude Code 방식(기본)**

- 질문할 때마다 이 PC의 Claude Code를 새로 실행하고 표준 입력으로 질문(이어서 묻는 중이면 앞선 대화 일부)을 넘겨요. 시스템 프롬프트(기본은 짧게 답하라는 안내이고 설정 창에서 바꿀 수 있어요)와 고른 모델 이름도 함께 가요. 시스템 프롬프트는 실행 인자로 넘어가니 비밀 내용을 넣지 마세요.
- Claude Code는 **답만 하도록** 실행해요. 파일을 읽거나 명령을 실행하는 도구와 MCP를 모두 끄고 Claude Code 설정 파일·`CLAUDE.md`·메모리를 읽지 않으며 대화 기록(세션)도 남기지 않게 해요. 이 PC의 `ANTHROPIC_API_KEY` 같은 환경 변수는 넘기지 않아서 API 요금이 아니라 구독으로 처리돼요.
- 질문은 Claude Code를 거쳐 **Anthropic으로 전송돼요.** Anthropic이 그 내용을 어떻게 처리하고 얼마나 보관하는지는 Anthropic의 약관·개인정보 처리방침을 따라요. Claude Code 안에서 일어나는 일(자체 기록 등)은 ClaudeTool이 통제하지 않아요.
- 질문 창에 넣은 글만 가요. 파일·화면·클립보드·사용량 기록은 보내지 않아요.

**5.2 질문하기 — API 키 방식(선택)**

- 트레이의 "질문 방식"에서 API 키 방식으로 바꿨을 때만 써요. 같은 내용을 Anthropic API 주소(`api.anthropic.com`)로 직접 보내고 API 키를 요청 머리글에 담아요. Anthropic SDK가 요청에 기본으로 붙이는 정보(SDK 버전, 운영체제와 CPU 종류, Node.js 버전)도 함께 가요. 설치판에서는 이 주소를 바꿀 수 없어요.

**5.3 조직 사용량(선택, 기본으로 꺼져 있어요)**

- 트레이의 "사용량 소스"에서 켜고 Admin API 키를 넣었을 때만 써요. 켜 둔 동안 5분마다(사용량 창이 열려 있으면 1분마다) `api.anthropic.com`에 조직의 사용량·비용 보고서를 요청해요. Admin 키를 요청 머리글에 담고 User-Agent에 앱 이름(`ClaudeTool/…`)이 들어가요. 결과는 화면에만 보여 주고 파일로 저장하지 않아요.

**5.4 설치형 플러그인**

- 플러그인은 설치할 때 동의한 "접속할 주소"로만 연결되도록 막아 뒀지만 완벽하지는 않아요(HTTP·HTTPS는 앱이 대신 요청하고 WebSocket은 선언한 주소로만 열려요). 무엇을 보낼지는 플러그인이 정하고 앱은 그 내용을 검열하거나 기록하지 않아요(막거나 실패한 시도의 주소만 로그에 남겨요).
- **알려진 한계:** 플러그인 화면이 DNS 이름 조회(`dns-prefetch`)에 짧은 정보를 실어 **동의하지 않은 곳으로도** 보낼 수 있고 앱은 이를 막지 못해요(받는 쪽이 DNS 서버를 운영해야 하는 통로라 보낼 수 있는 양은 적어요). 자세한 내용은 [DISCLAIMER.md](DISCLAIMER.md)의 3.4를 보세요.
- 플러그인이 알 수 있는 것은 6절에 있어요.

**5.5 맞춤법 검사**

- 앱 창의 맞춤법 검사는 꺼 두어 사전을 내려받지 않아요. 그래서 맞춤법 사전 때문에 밖으로 나가는 연결은 없어요.

**5.6 링크**

- 말풍선 답 속의 링크를 **눌렀을 때만** https 주소를 기본 브라우저로 열어요(다른 형식의 링크는 열지 않아요). 그 뒤의 일은 브라우저와 그 사이트의 몫이에요. 플러그인 말풍선의 링크는 글자로만 보이고 눌러도 열리지 않아요.

**5.7 하지 않는 것**

- 자동 업데이트, 새 판 확인, 사용 통계, 충돌 보고서 전송, 광고 추적을 하지 않아요.
- 앱 화면(펫·설정 창)은 이 PC의 파일만 불러오고 인터넷의 스크립트·글꼴·그림을 불러오지 않아요.

### 6. 플러그인이 알 수 있는 것

설치형 플러그인은 플러그인마다 보이지 않는 창에서 도는 웹 코드예요.

- **닿지 못하게 만든 것(보증은 아니에요):** 이 PC의 파일, 다른 플러그인의 데이터, 앱 화면의 내용, 질문과 답의 내용, API 키·Admin 키, 클립보드 읽기, 카메라·마이크·위치·화면 캡처. 위험을 줄이려는 장치일 뿐 안전을 보증하지 않아요([DISCLAIMER.md](DISCLAIMER.md)의 3.4 "격리의 한계").
- **닿을 수 있는 것:** 자기 설정 값(비밀 칸의 값 포함), 자기 저장 공간, 허락받은 앱 소식(펫을 눌렀다는 사실, 질문에 답이 왔다는 사실 — 내용은 아니에요), 들어오는 연결로 온 메시지, 창이 기본으로 아는 정보(언어·시간대·화면 크기·현재 시각 등). 동의받은 주소의 서버는 이 PC의 IP 주소를 알게 돼요.
- 플러그인이 이런 값을 동의받은 주소로 보낼 수 있다는 점은 [DISCLAIMER.md](DISCLAIMER.md)의 3.4에도 적혀 있어요. 동의 창을 읽고 믿을 수 있는 플러그인만 쓰세요.

### 7. 데이터 지우는 방법

- **플러그인 하나:** 설정 창 › 플러그인에서 "지우기"를 누르면 그 플러그인의 폴더·저장 데이터·비밀 값·토큰·동의 기록·설정 값이 함께 지워져요(되돌릴 수 없어요).
- **키·비밀 값 전부:** 앱을 끈 뒤 `secrets.bin`을 지우면 저장한 API 키·Admin 키·비밀 칸 값·토큰이 모두 지워져요.
- **로그·사용 기록·캐시:** 앱을 끈 뒤 `logs`, `usage` 폴더를 지워도 돼요. 앱이 다시 만들어요(`usage`를 지우면 이 앱의 사용 기록이 사라져요).
- **Claude Code 연결 흔적:** 사용량 창에서 "연결 해제"를 누르면 상태 줄이 원래대로 돌아가요. `backup\`에 남은 복사본은 직접 지우세요.
- **전부:** 트레이의 "종료"로 앱을 끈 뒤 제거하고 데이터 폴더를 직접 지우세요(Claude Code 연결을 했다면 제거하기 전에 먼저 "연결 해제"를 누르세요). 설치 프로그램으로 설치했다면 제거해도 데이터 폴더는 남아요.
- **밖에 있는 데이터:** Anthropic 쪽에 남은 질문 기록이나 플러그인이 밖으로 보낸 데이터는 ClaudeTool이 지울 수 없어요. 그 서비스에 문의하세요.

### 8. 소개 페이지와 배포 안내

- 소개 페이지는 GitHub Pages가 제공하는 정적 페이지예요. 접속 기록은 GitHub가 자신의 개인정보 처리방침에 따라 다뤄요. 소개 페이지에는 외부 스크립트·분석·글꼴·그림이 없어요.
- 소개 페이지의 테마(밝게·어둡게) 버튼은 고른 값을 방문자 브라우저의 localStorage(`ct-theme`)에만 저장하고 서버로 보내지 않아요. 브라우저의 사이트 데이터를 지우면 사라져요.
- 공개 설치 파일은 아직 준비 중이라, 소개 페이지 저장소(`claude-tool-page`)에서 내려받을 수 있는 설치 파일은 없어요.

### 9. 문의와 변경

- 개인정보에 관한 문의는 소개 페이지 저장소(`claude-tool-page`)의 Issues로 해 주세요(민감한 정보는 공개된 곳에 쓰지 마세요). 보안 문제는 [SECURITY.md](SECURITY.md)를 따라 주세요.
- 이 문서에 적지 않은 것은 확인하지 못했거나 앱이 하지 않는 일이에요. 문서와 앱이 다르면 알려 주세요.

---

## English

*A courtesy translation. If it differs from the Korean version, the Korean version prevails.*

### 1. At a glance

- ClaudeTool is an **app that runs on your PC.** The app does not talk to any server operated by the Licensor, and the Licensor **does not receive** your questions, settings, usage history or keys.
- ClaudeTool has **no usage statistics, remote analytics, crash-report upload, automatic update or new-version check** (the source code was searched for every network call and for anything related to analytics, crash reporting and updates, and none of those was found; the running app's network traffic was not captured). You get the installer and install new versions yourself.
- Data is stored **only in the data folder on this PC** (Section 2). **The content of questions and answers is not saved to files.**
- Within what was checked, there are four ways data leaves the PC (Section 5): (1) asking questions, (2) organization usage (only if you turn it on), (3) what an installed plugin sends to the addresses you consented to (for a known limit, see 5.4), (4) your default browser opening when you click an https link in a speech bubble. The app windows' spell checker is turned off, so no dictionary is downloaded (5.5). No guarantee can be given for everything that components such as Electron, Chromium and Windows do on their own.
- To show usage, the app **reads** the log files Claude Code leaves on this PC (Section 4). Of what it reads it uses only the model name, time and token counts, and it does not store or send the content of questions and answers.

### 2. What is stored on your PC

**Where the data folder is**

- If you used the installer, it is `<install folder>-data`, **next to** the install folder. If the install folder is the root of a drive, it is `ClaudeTool-data` under that root.
- If you run the executable without the installer, it is the `data` folder next to the executable.
- You can open it from Settings › General with "Open data folder" / "Open log folder". If you used the installer, the folder remains when you update or uninstall the app.

**Inside the data folder**

| Location | What it contains | Notes |
|---|---|---|
| `settings.json` | Chosen character and its size/opacity, movement, roaming area and monitor, speech-bubble settings, usage-source on/off, question method and model, (if set) the path to the Claude Code executable, and for each installed plugin: on/off, **ordinary setting values**, consent record (permissions and addresses), window positions, plus the incoming-connection port | Ordinary setting values are not encrypted (only secret fields are encrypted, in `secrets.bin`). If the file is damaged it is moved to `settings.json.bak-<time>` and a new one is created. |
| `secrets.bin` | Anthropic API key, Admin API key, plugin secret-field values, incoming-connection tokens | The whole file is encrypted with Windows data protection (DPAPI). If it cannot be decrypted it is moved to `secrets.bin.unreadable-<time>` and the app starts empty. |
| `logs\app.log`, `logs\plugins.log` | Logs of the app and of plugins (built-in features and installed ones) | Section 3. Never deleted or trimmed automatically. |
| `packs\` | Characters you made or imported (image files and `pack.json`) | |
| `plugins\` | Files of installed plugins (the extracted zip, or a folder you put there yourself) | A `.staging` temporary folder briefly appears while importing. |
| `plugin-data\<plugin id>.json` | Values a plugin saved in its "storage" | Not encrypted. Up to 1 MB per plugin. |
| `usage\app-ledger.jsonl` | A usage record of questions the app sent: time, model name, token counts, method (API or Claude Code), outcome | No question or answer content. Never deleted automatically. |
| `usage\subscription.json` | Subscription limit (5-hour / 7-day) usage ratios, reset times and the Claude Code session number (a random ID) | Section 4 |
| `usage\cache\claude-code.json` | A cache so Claude Code logs need not be re-read: path, size and read position of each log file read, and per-response model, time and token counts for the last 8 days | File paths contain the project folder names Claude Code created (they are made from working-folder paths). Can grow to several MB. |
| `pricing.json` | A per-model price table (for cost estimates) | Created by the app with default values; you may edit it. |
| `backup\` | A copy of Claude Code's `settings.json` made before "Connect"/"Disconnect" is applied | Contains your Claude Code settings as they were. Remains after you disconnect. |
| `claude-code-cwd\` | An empty working folder used when asking questions through Claude Code | |
| `electron\` | Cache, storage and settings of Chromium (the browser engine) used by the app windows | The key used to decrypt `secrets.bin` is kept here (`Local State`), so deleting this folder makes `secrets.bin` unreadable and you must enter your keys again. |

**What is not stored**

- **The content of questions and answers.** To let you ask follow-ups, the app remembers the recent conversation **in memory only** (up to 6 turns, up to 10 minutes after the last answer) while it is running; it is gone when you quit.
- **Cookies and browser storage of plugin windows.** A plugin window's temporary storage exists only in memory and disappears when you quit. The only plugin data left on disk is `plugin-data`.
- **Screen content, clipboard and keystrokes.** The app does not collect these. It registers one global shortcut, for asking questions (default `Ctrl+Alt+K`), and only writes to the clipboard when you press "Copy token" (it never reads it).

### 3. What the logs contain and what they do not

- Logs are appended line by line to `logs\app.log` (the app) and `logs\plugins.log` (built-in features and installed plugins). They are never deleted or trimmed automatically, so they keep growing.
- **What is recorded:** a time and a one-line description. App start (including the data folder path), names of enabled features, the result of registering the shortcut, the fact that a key or token was saved or removed (only which field, never the value), error and warning messages (which may contain file paths), plugin start/stop (id, version, reason), connection attempts a plugin was blocked from (only the origin, never path, query, headers or body) and failed outgoing connections (method, origin, error code), the fact that the incoming-connection channel was opened or closed (`127.0.0.1` and the port), and what a plugin itself writes to the log plus console warnings and errors (up to 60 lines per minute and 2,000 characters per line; what is written is up to the plugin).
- **What is built not to be recorded:** the content of questions, answers and system prompts; the values of API keys, Admin keys, secret fields and tokens; successful plugin requests. However, an error message can include the error description returned as is by an Anthropic server or Claude Code, and if a plugin writes a secret value to its own log it will remain.
- Before showing or uploading a log, check whether it contains personal information such as paths and names.

### 4. What the app reads

- **Claude Code logs (usage view).** The usage source "Claude Code" (on by default) looks for and reads the `.jsonl` files under `projects` in the Claude Code folder (normally `.claude` under your user folder, or the folder named by `CLAUDE_CONFIG_DIR`) when you open the usage window (and every minute while it stays open); it skips `tool-results` folders. It reads the files but uses only the model name, time, response number and token counts, and does not store or send the content of questions, answers or tool results. You can turn it off under "Usage sources" in the tray menu.
- **Claude Code settings file.** It reads `settings.json` in the Claude Code folder only when you press "Connect Claude Code" or "Disconnect" in the usage window. It shows what will change, edits the file only after you press **Apply**, and first copies the original to `backup\`. It does not read it at any other time.
- **What connecting does.** A small script of this app is registered as Claude Code's status line (statusLine) command. Each time Claude Code draws its status line this script runs with the system's Node.js and, of the status information Claude Code passes in, writes **only the limit usage ratios, reset times and session number** to `usage\subscription.json`. If you already had a status-line command, the same input is passed to it and it keeps running. When connecting, the app runs `where node` and `node --version` to find Node.js. Pressing "Disconnect" restores the original.
- **Where it looks.** To find the Claude Code executable (`claude.exe`) it looks through `PATH` and `.local\bin` under your user folder. It does not read Claude Code's sign-in or credential files.

### 5. What leaves your PC

**5.1 Asking questions: Claude Code method (default)**

- For each question the app starts your PC's Claude Code afresh and passes the question (plus part of the earlier conversation when you are following up) through standard input. The system prompt (by default a short instruction to answer briefly, which you can change in the settings window) and the chosen model name go along. The system prompt is passed as a launch argument, so do not put secrets in it.
- Claude Code is run **to answer only**: all tools that read files or run commands and MCP are turned off, Claude Code's settings files, `CLAUDE.md` and memory are not read, and no conversation record (session) is kept. Environment variables such as `ANTHROPIC_API_KEY` on this PC are not passed on, so the question is handled by your subscription, not by API charges.
- The question is **sent to Anthropic** through Claude Code. How Anthropic processes and how long it keeps that content follows Anthropic's terms and privacy policy. ClaudeTool does not control what happens inside Claude Code (its own records, etc.).
- Only the text you typed in the question box goes out. Files, the screen, the clipboard and usage records are not sent.

**5.2 Asking questions: API-key method (optional)**

- Used only if you switch to the API-key method under "Question method" in the tray menu. The same content is sent directly to the Anthropic API address (`api.anthropic.com`) with your API key in a request header. The information the Anthropic SDK adds to requests by default (SDK version, operating system and CPU type, Node.js version) goes along. This address cannot be changed in an installed build.

**5.3 Organization usage (optional, off by default)**

- Used only if you turn it on under "Usage sources" in the tray menu and enter an Admin API key. While on, it asks `api.anthropic.com` for the organization's usage and cost reports every 5 minutes (every minute while the usage window is open), with the Admin key in a request header and the app name (`ClaudeTool/…`) in the User-Agent. The result is only shown on screen and is not saved to a file.

**5.4 Installed plugins**

- A plugin is made to connect only to the "addresses it can connect to" you consented to when installing, but this is not perfect (HTTP/HTTPS requests are made by the app on its behalf; WebSocket opens only to declared addresses). What it sends is up to the plugin, and the app does not censor or record it (only the addresses of blocked or failed attempts are logged).
- **Known limit:** a plugin screen can carry a small amount of information in the names of DNS lookups (`dns-prefetch`) and send it **even to places you did not consent to**, and the app cannot block this (the receiver has to run a DNS server, so the amount is small). See 3.4 of [DISCLAIMER.md](DISCLAIMER.md).
- What a plugin can know is in Section 6.

**5.5 Spell checking**

- The app windows' spell checker is turned off, so no dictionary is downloaded. There is therefore no outside connection for a spell-check dictionary.

**5.6 Links**

- **Only when you click** a link inside a speech-bubble answer, an https address is opened in your default browser (links of other kinds are not opened). What happens afterwards is up to the browser and that site. Links in a plugin's speech bubble are shown as plain text and do not open.

**5.7 What it does not do**

- No automatic updates, new-version checks, usage statistics, crash-report uploads, advertising or tracking.
- The app's own screens (the pet and the settings window) load only files from this PC and load no scripts, fonts or images from the internet.

### 6. What a plugin can know

An installable plugin is web code running in its own invisible window.

- **What it is built not to reach (not a guarantee):** files on this PC, other plugins' data, the content of app screens, the content of questions and answers, API/Admin keys, reading the clipboard, the camera, microphone, location and screen capture. These are ways to reduce risk and do not guarantee safety (see "Limits of isolation" in 3.4 of [DISCLAIMER.md](DISCLAIMER.md)).
- **What it can reach:** its own setting values (including secret-field values), its own storage, the app events it was allowed to receive (that the pet was clicked, that an answer to a question arrived — not its content), messages arriving through incoming connections, and what a window knows by default (language, time zone, screen size, current time, etc.). The servers at the addresses it was allowed to contact learn this PC's IP address.
- That a plugin can send such values to the addresses you consented to is also stated in 3.4 of [DISCLAIMER.md](DISCLAIMER.md). Read the consent window and use only plugins you trust.

### 7. How to delete data

- **One plugin:** pressing "Delete" in Settings › Plugins also deletes that plugin's folder, saved data, secret values, token, consent record and setting values (it cannot be undone).
- **All keys and secret values:** after quitting the app, delete `secrets.bin` to erase all saved API keys, Admin keys, secret-field values and tokens.
- **Logs, usage records, caches:** after quitting the app you may delete the `logs` and `usage` folders. The app recreates them (deleting `usage` erases this app's usage history).
- **Traces of connecting Claude Code:** press "Disconnect" in the usage window to restore the status line. Delete the copies left in `backup\` yourself.
- **Everything:** quit the app with "Quit" in the tray menu, uninstall it, and delete the data folder yourself (if you connected Claude Code, press "Disconnect" before uninstalling). If you used the installer, the data folder remains after uninstalling.
- **Data outside your PC:** question records kept on Anthropic's side and data a plugin sent out cannot be deleted by ClaudeTool. Contact those services.

### 8. The introduction page and distribution

- The introduction page is a static page served by GitHub Pages. Access logs are handled by GitHub under its own privacy policy. The introduction page contains no external scripts, analytics, fonts or images.
- The theme (light/dark) button on the introduction page stores your choice only in your own browser's localStorage (`ct-theme`) and does not send it to any server. It disappears when you clear the browser's site data.
- The public installer is still in preparation, so there is no installer to download from the introduction-page repository (`claude-tool-page`).

### 9. Questions and changes

- For privacy questions, please use the Issues of the introduction-page repository (`claude-tool-page`) (do not post sensitive information in public). For security problems, follow [SECURITY.md](SECURITY.md).
- Anything not written here is either something that could not be confirmed or something the app does not do. If this document and the app differ, please report it.
