# 개인정보 안내 (Privacy)

> 이 문서는 법률 자문이 아니고, 변호사의 검토를 받은 문서도 아니에요. 회사 업무·영리 목적 등으로 쓰거나 배포하기 전에는 전문가의 검토를 받으세요.
>
> *This document is not legal advice and has not been reviewed by a lawyer. Get professional advice before any business or commercial use or distribution.*

ClaudeTool 0.4.2(2026-10-06 기준)이 이 PC에 무엇을 저장하고, 무엇을 읽고, 무엇을 밖으로 보내는지 정리한 안내예요. 소스 코드를 읽고, 개발용 데이터 폴더와 설치 산출물(빌드 결과)을 점검해 쓴 것이고, 실행 중인 앱의 통신을 캡처해 확인한 것은 아니에요. 앞으로 바뀔 수 있어요. 새 판은 저장소에 올린 때부터 그 뒤에 받거나 갱신하는 소프트웨어에 적용돼요. 이 문서는 이해를 돕는 안내이며 소프트웨어의 동작을 보증하는 것이 아니에요. 보증과 책임은 [DISCLAIMER.md](DISCLAIMER.md)를 따라요. 한국어본과 영어본이 함께 있고, 뜻이 다르면 한국어본이 우선해요. 함께 읽으면 좋은 문서: [LICENSE](LICENSE), [SECURITY.md](SECURITY.md)(보안 문제 신고), [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)(제3자 소프트웨어).

*This is a guide to what ClaudeTool 0.4.2 (as of 2026-10-06) stores on this PC, reads, and sends out. It was written from reading the source code and inspecting a development data folder and the built installer output; the running app's network traffic was not captured. It may change; a new version applies from the time it is posted to Software received or updated after that time. It is an explanatory guide, not a guarantee of how the software behaves; warranties and liability follow [DISCLAIMER.md](DISCLAIMER.md). A Korean and an English version are provided; if they differ, the Korean version prevails. See also: [LICENSE](LICENSE), [SECURITY.md](SECURITY.md) (reporting security problems), [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) (third-party software).*

---

## 한국어

### 1. 한눈에 보기

- ClaudeTool은 **내 PC에서 돌아가는 앱**이에요. 앱은 저작권자가 운영하는 서버와 통신하지 않고, 저작권자는 사용자의 질문·설정·사용 기록·키를 **받지 않아요.**
- ClaudeTool에는 **사용 통계·원격 분석·충돌 보고서 전송** 기능이 없어요(소스 코드에서 네트워크 호출을 모두 찾아보고 분석·충돌 보고와 관련된 부분이 없는 것을 확인했어요. 실행 중인 앱의 통신을 캡처해 확인한 것은 아니에요). 0.4.2부터는 **새 판 확인**이 있어요(설치 프로그램으로 설치한 앱에서 기본으로 켜져 있고 처음 확인하기 전에 알려 드려요. 끄는 법은 5.7).
- 데이터는 이 PC의 **데이터 폴더**에만 저장돼요(2절). **질문과 답의 내용은 파일로 저장하지 않아요.**
- 확인한 범위에서 밖으로 나가는 길은 다섯 가지예요(5절): ① 질문하기(Anthropic으로 가요. 트레이의 '질문 방식'에서 OpenAI 호환 서버를 골랐다면 내가 적은 주소로 가요. `ai` 권한을 허락한 플러그인이 AI를 부를 때도 같은 곳으로 가요), ② 조직 사용량(켠 경우만), ③ 설치한 플러그인이 동의받은 주소로 보내는 것(알려진 한계는 5.4), ④ 말풍선 안의 https 링크를 눌렀을 때 기본 브라우저가 열리는 것(허락받은 플러그인의 링크 버튼 포함), ⑤ 새 판 확인과 내려받기(5.7). 앱 창의 맞춤법 검사는 꺼 두어 사전을 내려받지 않아요(5.5). Electron·Chromium·Windows 같은 구성요소가 스스로 하는 일을 모두 보증하지는 못해요.
- 사용량을 보여 주려고 이 PC의 Claude Code 기록 파일을 **읽어요**(4절). 읽은 내용 가운데 모델 이름·시각·토큰 수만 쓰고, 질문과 답의 내용은 저장하거나 보내지 않아요.
- 설치한 플러그인에 **프로그램 실행(`run`)·고른 폴더 읽기와 쓰기(`files`)·파일이나 앱 열기(`open-app`)** 권한을 허락하면 그 플러그인이 이 PC에서 행동할 수 있어요. 실행·쓰기·열기는 매번 앱이 직접 띄우는 승인 카드로 물어요(내가 '이 플러그인은 늘 허용'을 켠 종류만 묻지 않아요). 앱은 이 행동의 내용을 저작권자나 어디로도 보내지 않아요. 다만 허락한 뒤 실행한 프로그램이 하는 일은 앱이 막지 못해요(5.4, [DISCLAIMER.md](DISCLAIMER.md)의 3.4).
- 사용자가 켜거나 허락한 경우에만 앱이 **이 PC의 다른 설정을 바꿔요**: Claude Code 연결(상태 줄), 플러그인의 Claude Code 훅 연결과 Codex CLI 알림 연결(4절), Windows 시작 시 실행(레지스트리 `Run` 항목 하나, 2절). 모두 기본으로는 꺼져 있고 끄면 되돌려요.

### 2. 내 PC에 저장되는 것

**데이터 폴더 위치**

- 설치 프로그램으로 설치했다면 설치 폴더 **옆**의 `<설치 폴더>-data`예요. 설치 폴더가 드라이브 맨 위(루트)라면 그 아래의 `ClaudeTool-data`예요.
- 설치 프로그램 없이 실행 파일만 두고 쓰면 실행 파일 옆의 `data` 폴더예요.
- 설정 창 › 일반의 "데이터 폴더 열기"·"로그 폴더 열기"로 열 수 있어요. 설치 프로그램으로 설치했다면 앱을 업데이트하거나 제거해도 이 폴더는 남아요.

**데이터 폴더 안**

| 위치 | 들어 있는 것 | 비고 |
|---|---|---|
| `settings.json` | 캐릭터 선택과 크기·투명도, 움직임, 돌아다니는 범위와 모니터, 말풍선 설정, 사용량 소스 켜기·끄기, 질문 방식(Claude Code·API 키·OpenAI 호환 서버)·모델·OpenAI 호환 서버의 주소와 모델 이름·(지정했다면) Claude Code 실행 파일 경로, 설치형 플러그인별 켜짐 여부·**일반 설정 값**·동의 기록(권한·접속 주소·선언한 프로그램 이름과 폴더 이름표)·창 위치·AI 월 예산(토큰)·'늘 허용'을 켠 행동 종류·`files` 권한으로 고른 폴더의 경로·`run` 권한으로 직접 지정한 프로그램의 경로, 들어오는 연결 포트, 새 판 자동 확인 켜기·끄기(첫 안내를 봤는지 포함), Windows 시작 시 실행 켜기·끄기 | 일반 설정 값은 암호화하지 않아요(비밀 칸만 `secrets.bin`에 암호화해요). 파일이 깨지면 `settings.json.bak-<시각>`으로 옮겨 두고 새로 만들어요. |
| `secrets.bin` | Anthropic API 키, Admin API 키, OpenAI 호환 서버의 API 키(적었다면), 플러그인의 비밀 칸 값, 들어오는 연결 토큰, 플러그인 코드가 `secrets` 권한으로 맡긴 비밀(플러그인마다 20개까지), 훅 연결 토큰 | Windows 데이터 보호 기능(DPAPI)으로 파일 전체를 암호화해요. 풀지 못하면 `secrets.bin.unreadable-<시각>`으로 옮겨 두고 빈 상태로 시작해요. |
| `logs\app.log`, `logs\plugins.log` | 앱과 플러그인(내장 기능·설치형)의 로그 | 3절. 자동으로 지우거나 줄이지 않아요. |
| `packs\` | 내가 만들거나 가져온 캐릭터(그림 파일과 `pack.json`) | |
| `plugins\` | 설치한 플러그인의 파일(받은 zip을 푼 것, 또는 직접 넣은 폴더) | 가져오는 동안에는 `.staging` 임시 폴더가 잠깐 생겨요. |
| `plugin-data\<플러그인 id>.json` | 플러그인이 "저장 공간"에 저장한 값 | 암호화하지 않아요. 플러그인마다 1MB까지예요. |
| `plugin-data\<플러그인 id>\work\` | `run` 권한을 허락한 플러그인이 프로그램을 실행할 때 기본으로 쓰는 작업 폴더(처음 실행할 때 만들어져요) | 실행한 프로그램이 만든 파일이 들어 있어요. 앱은 자동으로 지우거나 줄이지 않고 플러그인을 지우면 함께 지워져요. |
| `usage\app-ledger.jsonl` | 이 앱이 보낸 질문의 사용 기록: 시각·모델 이름·토큰 수(서버가 알려 주지 않으면 글자 수로 어림한 값이라고 표시해요)·방식(API·Claude Code·OpenAI 호환)·`ai` 권한 플러그인이 부른 호출이면 그 플러그인 id·결과 | 질문과 답의 내용은 없어요. 자동으로 지우지 않아요. |
| `usage\subscription.json` | 구독 한도(5시간·7일)의 사용 비율·초기화 시각과 Claude Code 세션 번호(무작위 ID) | 4절 |
| `usage\cache\claude-code.json` | Claude Code 기록을 다시 읽지 않으려는 캐시: 읽은 기록 파일의 경로·크기·읽은 위치, 최근 8일치 응답별 모델·시각·토큰 수 | 파일 경로에 Claude Code가 만든 프로젝트 폴더 이름(작업 폴더 경로에서 만들어져요)이 들어 있어요. 몇 MB까지 커질 수 있어요. |
| `pricing.json` | 모델별 단가표(비용 추정용) | 앱이 기본값으로 만들어 두고, 직접 고칠 수 있어요. |
| `backup\` | "Claude Code 연결"·"연결 해제"를 적용하기 전 Claude Code `settings.json`의 복사본 | 내 Claude Code 설정이 그대로 들어 있어요. 연결을 해제해도 남아요. |
| `claude-notify\token`, `claude-notify\backup\` | 알림 플러그인(claude-notify)의 훅 설치 도우미를 쓴 경우에만 생겨요. `token`은 훅이 플러그인에 소식을 보낼 때 쓰는 통로 토큰이고, `backup\`은 훅을 넣거나 빼기 전 Claude Code `settings.json`의 복사본이에요 | 암호화하지 않아요. 폴더를 현재 사용자만 접근하도록 좁혀 두지만(권한 설정이 되지 않는 드라이브에서는 좁혀지지 않을 수 있어요) 같은 계정의 다른 프로그램은 읽을 수 있고, 복사본에는 `env`에 적은 키가 있을 수 있어요. 필요 없으면 직접 지우세요. 훅 빼기(`--remove`)는 `token`만 지워요. |
| `hooks\<플러그인 id>\token`, `hooks\<플러그인 id>\backup\` | 앱의 훅 연결(4절)을 쓴 경우에만 생겨요. `token`은 훅이 플러그인에 소식을 보낼 때 쓰는 통로 토큰(같은 값을 `secrets.bin`에도 둬요)이에요. `backup\`은 훅을 넣거나 빼기 전 Claude Code `settings.json`(Codex 연결이면 Codex `config.toml`)의 복사본이에요 | 암호화하지 않아요. 폴더를 현재 사용자만 접근하도록 좁혀 두지만(권한 설정이 되지 않는 드라이브에서는 좁혀지지 않을 수 있어요) 같은 계정의 다른 프로그램은 읽을 수 있어요. 복사본에는 `env`에 적은 키나 Codex 설정에 적은 값이 있을 수 있어요. 한쪽 대상(Claude Code·Codex)만 끊으면 앱이 그 대상의 훅만 빼고 다른 대상에 이 플러그인의 훅이 남아 있는 동안은 `token`도 남겨 둬요. 두 대상의 훅이 모두 빠지면(플러그인을 끄거나 지울 때 포함) 앱이 `token`을 지우고 `backup\`은 남겨 둬요. 필요 없으면 직접 지우세요. |
| `electron\.updaterId` | 새 판을 처음 확인할 때 만든 임의의 번호(UUID) 하나 | 확인 요청의 머리글에 실려요(5.7). 사람이나 PC를 가리키지 않지만 같은 번호의 요청을 서로 이어 줄 수는 있어요. 지우면 다음 확인 때 새 번호를 만들어요. |
| `claude-code-cwd\` | Claude Code로 질문할 때 쓰는 빈 작업 폴더 | |
| `electron\` | 앱 창이 쓰는 Chromium(브라우저 엔진)의 캐시·저장소·설정 | `secrets.bin`을 푸는 열쇠가 여기(`Local State`)에 있어서, 이 폴더를 지우면 `secrets.bin`을 읽을 수 없게 돼요. 키를 다시 넣어야 해요. |

**데이터 폴더 밖에 남는 것**

- **레지스트리 `Run` 항목(Windows 시작 시 실행을 켠 경우만).** 현재 사용자의 `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`에 항목 하나를 써요. 관리자 권한은 필요 없고 기본값은 꺼짐이에요. 설정 창 › 일반이나 트레이 메뉴에서 끄면 항목이 지워져요. Windows 설정의 "시작 앱"에서 끄면 Windows가 그 항목을 꺼 두고 앱은 다음에 켤 때 설정도 끈 것으로 맞춰요. 제거 프로그램이 이 항목을 지우는지는 확인하지 못했으니 앱을 제거하기 전에 먼저 끄세요.
- **`%LOCALAPPDATA%\claude-tool-updater\`의 `pending\` 폴더와 `current.blockmap` 파일.** **[받기]를 눌러 새 판을 받았을 때만** 생겨요. `pending\`에는 받은 설치 파일(약 125MB)과 그 정보가, `current.blockmap`에는 차등 내려받기가 쓰는 작은 정보가 들어요. Windows 기본 캐시 위치라서 데이터 폴더 밖이에요. 이미 설치한 판의 `pending\` 폴더는 새 판이 시작될 때 앱이 지우고 그렇지 않으면 다음 내려받기 때 비워져요. 앱을 끈 뒤 `pending\` 폴더를 지워도 돼요(5.7).
- **`%LOCALAPPDATA%\claude-tool-updater\installer.exe`.** 설치 프로그램이 설치하거나 업데이트할 때마다 설치 파일의 사본을 남겨요(0.4.0부터 이미 그랬고 설정으로 끌 수 없어요. 제거 프로그램도 지우지 않아요). 새 판을 받을 때 차등 내려받기가 이 사본과 견줘 바뀐 부분만 받아요(5.7). 필요 없으면 직접 지우세요(지우면 다음 새 판은 전체를 받아요).
- **다른 프로그램의 설정 파일(연결을 켠 경우만).** 훅 연결을 켜면 Claude Code의 `settings.json`에 그 플러그인의 훅이 들어가요(4절). Codex 연결을 켜면 Codex 설정 폴더(`CODEX_HOME`이 있으면 그 폴더, 없으면 사용자 폴더의 `.codex`)의 `config.toml` 맨 위에 알림 명령 한 줄이 들어가요. 둘 다 사용자가 상세 칸의 [연결]을 눌렀을 때만 써요. 끊거나 플러그인을 끄고 지우면 앱이 그 줄을 빼요. 앱이 없어진 뒤에는 직접 빼야 해요(7절).

**저장하지 않는 것**

- **질문과 답의 내용.** 이어서 묻기 위해 앱이 켜져 있는 동안 **메모리에만** 최근 대화(최대 6번, 마지막 답 뒤 10분까지)를 기억하고, 앱을 끄면 사라져요.
- **`ai` 권한 플러그인이 주고받는 글.** 앱은 저장하지 않고 로그에도 적지 않아요. 플러그인이 자기 저장 공간에 두는 것은 플러그인이 정해요.
- **고른 폴더의 파일 내용과 실행한 프로그램의 출력.** 앱은 플러그인에 전해 줄 뿐 복사하거나 저장하지 않아요.
- **플러그인 창의 쿠키·브라우저 저장소.** 플러그인 창의 임시 저장소는 메모리에만 있어 앱을 끄면 사라져요. 디스크에 남는 플러그인 데이터는 `plugin-data`뿐이에요.
- **화면 내용·클립보드·키 입력.** 앱은 이것들을 수집하지 않아요. 전역 단축키는 질문하기용 하나(기본 `Ctrl+Alt+K`)만 등록하고, 클립보드는 "토큰 복사"를 눌렀을 때 쓰기만 해요(읽지 않아요). `clipboard-write` 권한을 허락한 플러그인도 글을 클립보드에 쓸 수 있지만 읽지는 못해요. 다만 사용자가 직접 실행하는 알림 훅 설치 도우미(앱과 별개의 스크립트)는 `--apply`를 실행할 때 한 번 클립보드를 읽고, 토큰 모양일 때만 `claude-notify\token`에 저장해요(내용은 화면에 보이지 않아요).

### 3. 로그에 남는 것과 남지 않는 것

- 로그는 `logs\app.log`(앱)와 `logs\plugins.log`(내장 기능과 설치형 플러그인)에 한 줄씩 덧붙여요. 자동으로 지우거나 줄이지 않아서 계속 커져요.
- **남는 것:** 시각과 한 줄 설명이에요. 앱 시작(데이터 폴더 경로가 들어가요), 켜진 기능의 이름, 단축키 등록 결과, 키·토큰을 저장하거나 지운 사실(어느 칸인지 이름만 적고 값은 적지 않아요), 오류·경고 문구(파일 경로가 들어갈 수 있어요), 플러그인 시작·멈춤(id·버전·이유), 플러그인이 막힌 연결 시도(주소의 앞부분(origin)만 적고 경로·쿼리·헤더·본문은 적지 않아요)와 실패한 나가는 연결(방식·origin·오류 코드), 들어오는 연결 통로를 열고 닫은 사실(`127.0.0.1`과 포트), 새 판 확인·내려받기·설치 시작의 결과(주소는 쿼리 문자열을 지우고 적어요), 훅 연결·끊기의 결과와 훅 소식을 버린 사실(이벤트 이름만 적어요), 시작 시 실행을 바꾸지 못했을 때의 오류 이름, `ai` 호출 결과 한 줄(플러그인 id·방식·모델 이름·입력과 출력 토큰 수·걸린 시간·끝난 이유), 프로그램 실행 한 줄(가린 80자 요약과 종료 결과), 승인 요청의 결과 한 줄(허용·늘 허용·자동 허용·거부와 이유, 가린 80자 요약), 폴더 감시가 멈춘 사실, 플러그인이 직접 적은 로그와 콘솔 경고·오류(분당 60줄·한 줄 2000자까지이며, 무엇을 적을지는 플러그인이 정해요).
- **남기지 않게 만든 것:** 질문·답·시스템 프롬프트의 내용, `ai`로 보내고 받은 글, 프로그램의 출력, 파일 내용, API 키·Admin 키·OpenAI 호환 서버의 키·비밀 칸 값·토큰의 값, 성공한 플러그인 요청. 다만 오류 문구에는 Anthropic 서버나 Claude Code가 돌려준 오류 설명이 그대로 들어갈 수 있고, 플러그인이 비밀 값을 스스로 로그에 적으면 남아요. 승인 요약은 비밀처럼 보이는 세 가지 모양(`Bearer` 뒤의 값, `KEY=값`·`TOKEN=값`·`PASSWORD=값` 같은 꼴, `sk-`로 시작하는 키)만 `***`로 가려서 적어요. 명령줄에 다른 모양으로 적은 비밀은 80자 요약에 그대로 남을 수 있어요.
- 로그를 남에게 보여 주거나 올리기 전에 경로·이름 같은 개인 정보가 들어 있는지 확인하세요.

### 4. 읽는 것

- **Claude Code 기록(사용량 보기).** 사용량 소스 "Claude Code"(기본으로 켜져 있어요)는 사용량 창을 열면(열려 있는 동안 1분마다) Claude Code 폴더(보통 사용자 폴더 아래 `.claude`, `CLAUDE_CONFIG_DIR`을 쓰면 그 폴더)의 `projects` 아래 `.jsonl` 파일을 찾아 읽어요(`tool-results` 폴더는 건너뛰어요). 파일을 읽지만 모델 이름·시각·응답 번호·토큰 수만 뽑아 쓰고, 질문·답·도구 결과의 내용은 저장하거나 어디로 보내지 않아요. 트레이의 "사용량 소스"에서 끌 수 있어요.
- **Claude Code 설정 파일.** 사용량 창의 "Claude Code 연결"·"연결 해제"를 눌렀을 때와 아래 훅 연결을 쓸 때만 Claude Code 폴더의 `settings.json`을 읽어요. "Claude Code 연결"은 바뀔 내용을 보여 준 뒤 **적용**을 눌러야 고쳐요. 고치기 전의 원본은 `backup\`에 복사해 둬요. 그 밖의 때는 읽지 않아요.
- **훅 연결(`hooks` 권한을 허락한 플러그인).** 플러그인을 설치하거나 켠 직후에 앱이 "Claude Code에 연결할까요?"를 한 번 물어요. 설정 창에서 그 플러그인의 [연결]·[끊기]를 눌러도 같은 일을 해요. 연결하면 앱이 Claude Code의 `settings.json`에 그 플러그인의 알림 훅을 넣어요(사용자의 다른 훅과 설정은 그대로 두고 다른 플러그인의 훅도 건드리지 않아요). 고치기 전에 원본을 `hooks\<플러그인 id>\backup\`에 복사해 두고 읽은 뒤에 파일이 바뀌었으면 쓰지 않아요. 연결 상태를 보여 주려고 설정 창에서 그 플러그인 카드를 고를 때도 이 파일을 읽지만 읽기만 하고 쓰지 않아요. 플러그인을 끄거나 지울 때는 그 플러그인의 훅을 빼려고 한 번 더 고쳐요. 훅이 하는 일은 5.4의 "알림 훅"에 있어요. 플러그인 코드는 이 설정 파일에 닿지 못해요.
- **Codex 연결(`hooks` 권한의 `codex` 대상).** 설정 창에서 그 플러그인의 [연결]·[끊기]를 누를 때와 연결 상태를 보여 주려고 그 플러그인 카드를 고를 때 Codex 설정 폴더(`CODEX_HOME`이 있으면 그 폴더, 없으면 사용자 폴더의 `.codex`)의 `config.toml`을 읽어요. 읽기만 하는 때는 쓰지 않아요. [연결]을 누르면 `config.toml` 맨 위에 알림 명령 한 줄(`notify = [...]`)만 넣고 다른 줄은 건드리지 않아요. 고치기 전에 파일 전체를 `hooks\<플러그인 id>\backup\`에 복사해 두고 읽은 뒤에 파일이 바뀌었으면 쓰지 않아요. 이미 다른 알림 명령이 있거나 파일 모양을 판단할 수 없으면 넣지 않아요. 플러그인을 설치한 직후에 묻는 창은 Claude Code만 묻고 Codex 설정은 묻지도 고치지도 않아요. Codex의 로그인·인증 파일은 읽지 않아요. 이 알림 명령은 Codex가 작업을 한 차례 마칠 때마다 이 앱의 작은 스크립트를 실행하게 해요. 스크립트가 보내는 것은 5.4의 "Codex 알림"에 있어요. 플러그인 코드는 이 설정 파일에 닿지 못해요.
- **연결하면 일어나는 일.** Claude Code의 상태 줄(statusLine) 명령에 이 앱의 작은 스크립트가 등록돼요. Claude Code가 상태 줄을 그릴 때마다 설치 폴더 `resources\node`의 `node.exe`로 이 스크립트가 돌고, Claude Code가 넘겨 주는 상태 정보 가운데 **한도 사용 비율·초기화 시각·세션 번호만** `usage\subscription.json`에 적어요. 원래 쓰던 상태 줄 명령이 있었다면 같은 입력을 그 명령에도 넘겨 이어서 실행해요. 연결할 때는 설치 폴더 `resources\node`의 `node.exe`를 먼저 쓰고, 없거나 실패하면 PC의 Node.js를 찾으려고 `where node`와 `node --version`을 실행해요. "연결 해제"를 누르면 원래대로 되돌려요.
- **찾아보는 곳.** Claude Code 실행 파일(`claude.exe`)을 찾으려고 `PATH`와 사용자 폴더의 `.local\bin`을 살펴봐요. Claude Code의 로그인·인증 파일은 읽지 않아요.
- **프로그램 찾기(`run` 권한).** 플러그인이 `run`으로 선언한 프로그램 이름마다 `PATH`의 폴더를 훑어 그 프로그램 파일을 찾아요(현재 폴더는 보지 않아요). 찾은 경로는 설정 창 상세 칸에 보이고 직접 지정할 수도 있어요.
- **고른 폴더(`files` 권한).** 사용자가 설정 창 플러그인 카드에서 고른 폴더 안의 파일을 플러그인이 요청할 때마다 읽어서 그 플러그인에 전해요. 폴더 안의 파일 이름이 바뀌는 소식(경로만이고 내용은 아니에요)도 전해요. 폴더를 고르지 않으면 읽지 않아요. 5.4에 자세히 있어요.

### 5. 밖으로 나가는 것

**5.1 질문하기 — Claude Code 방식(기본)**

- 질문할 때마다 이 PC의 Claude Code를 새로 실행하고, 표준 입력으로 질문(이어서 묻는 중이면 앞선 대화 일부)을 넘겨요. 시스템 프롬프트(기본은 짧게 답하라는 안내이고 설정 창에서 바꿀 수 있어요)와 고른 모델 이름도 함께 가요. 시스템 프롬프트는 실행 인자로 넘어가니 비밀 내용을 넣지 마세요.
- Claude Code는 **답만 하도록** 실행해요. 파일을 읽거나 명령을 실행하는 도구와 MCP를 모두 끄고, Claude Code 설정 파일·`CLAUDE.md`·메모리를 읽지 않으며, 대화 기록(세션)도 남기지 않게 해요. 이 PC의 `ANTHROPIC_API_KEY` 같은 환경 변수는 넘기지 않아서 API 요금이 아니라 구독으로 처리돼요.
- 질문은 Claude Code를 거쳐 **Anthropic으로 전송돼요.** Anthropic이 그 내용을 어떻게 처리하고 얼마나 보관하는지는 Anthropic의 약관·개인정보 처리방침을 따라요. Claude Code 안에서 일어나는 일(자체 기록 등)은 ClaudeTool이 통제하지 않아요.
- 질문 창에 넣은 글만 가요. 파일·화면·클립보드·사용량 기록은 보내지 않아요.

**5.2 질문하기 — API 키 방식과 OpenAI 호환 서버 방식(선택)**

- **API 키 방식.** 트레이의 "질문 방식"에서 API 키 방식으로 바꿨을 때만 써요. 같은 내용을 Anthropic API 주소(`api.anthropic.com`)로 직접 보내고, API 키를 요청 머리글에 담아요. Anthropic SDK가 요청에 기본으로 붙이는 정보(SDK 버전, 운영체제와 CPU 종류, Node.js 버전)도 함께 가요. 설치판에서는 이 주소를 바꿀 수 없어요.
- **OpenAI 호환 서버 방식(0.4.3부터).** 트레이의 "질문 방식"이나 설정 창 › 일반 › "AI 연결"에서 OpenAI 호환 서버를 골랐을 때만 써요. 질문(이어서 묻는 중이면 앞선 대화 일부)·시스템 프롬프트·고른 모델 이름을 **내가 "AI 연결"에 적은 주소**의 `/chat/completions`로 보내요. 기본 주소는 이 PC에서 도는 서버를 가리키는 `http://127.0.0.1:11434/v1`이에요. 주소는 `http`나 `https`예요. 키를 적었다면 요청 머리글(`Authorization`)에 담고 `User-Agent`에 앱 이름(`ClaudeTool/…`)이 들어가요. 서버가 다른 주소로 돌려보내도 따라가지 않아요.
- 설정 창의 [연결 확인]을 누르면 그 주소의 `/models`로 모델 목록을 요청해요(저장해 둔 키는 저장된 같은 주소에만 보내요). 누를 때만 요청하고 5초 안에 답이 없으면 멈춰요.
- **주소가 이 PC 밖이면 질문 내용이 그 서버로 가요.** `https`가 아닌 `http` 주소는 중간에서 읽힐 수 있어요. 설정 창은 주소가 이 PC 안(`localhost`·`127.0.0.1`)도 집·회사 내부망(사설 주소·`.local` 이름)도 아니면 "이 PC 밖 주소예요. 질문 내용이 그 서버로 가요"를 늘 보여 줘요. 이름만으로 어디인지 알 수 없는 호스트(예: `nas`)도 밖으로 봐요. 내부망 주소는 경고가 없어도 같은 망의 다른 기기로 간다는 뜻이에요. 그 서버가 내용을 어떻게 처리하고 얼마나 보관하는지는 그 서버 운영자의 몫이고 ClaudeTool이 통제하지 않아요. 비밀번호·키·개인정보·회사 기밀은 쓰지 마세요.

**5.3 조직 사용량(선택, 기본으로 꺼져 있어요)**

- 트레이의 "사용량 소스"에서 켜고 Admin API 키를 넣었을 때만 써요. 켜 둔 동안 5분마다(사용량 창이 열려 있으면 1분마다) `api.anthropic.com`에 조직의 사용량·비용 보고서를 요청해요. Admin 키를 요청 머리글에 담고, User-Agent에 앱 이름(`ClaudeTool/…`)이 들어가요. 결과는 화면에만 보여 주고 파일로 저장하지 않아요.

**5.4 설치형 플러그인**

- 플러그인은 설치할 때 동의한 "접속할 주소"로만 연결되도록 막아 뒀지만 완벽하지는 않아요(HTTP·HTTPS는 앱이 대신 요청하고, WebSocket은 선언한 주소로만 열려요). 무엇을 보낼지는 플러그인이 정하고, 앱은 그 내용을 검열하거나 기록하지 않아요(막거나 실패한 시도의 주소만 로그에 남겨요).
- **알려진 한계:** 플러그인 화면이 DNS 이름 조회(`dns-prefetch`)에 짧은 정보를 실어 **동의하지 않은 곳으로도** 보낼 수 있고, 앱은 이를 막지 못해요(받는 쪽이 DNS 서버를 운영해야 하는 통로라 보낼 수 있는 양은 적어요). 자세한 내용은 [DISCLAIMER.md](DISCLAIMER.md)의 3.4를 보세요.
- **알림 훅(claude-notify):** 앱의 훅 연결로 넣었든 0.4.1의 수동 설치 도우미로 넣었든 훅은 소식을 이 PC의 `127.0.0.1`(들어오는 연결 통로)로만 보내요. 인터넷이나 다른 기기로는 보내지 않아요. 보내는 것은 알림 종류, 훅 이벤트 이름과 이유(도구 이름 같은 짧은 표시), Claude Code 세션 번호, 작업 폴더 경로, 세션을 연 진입점, 데스크톱 앱 안의 세션 번호, 도구 호출 번호, 짧은 한 줄 글(제목과 본문이고, 명령·질문·마지막 응답의 앞부분이며, 비밀처럼 보이는 모양은 `***`로 가려요)이에요. 프롬프트 내용과 대화 기록 파일 경로는 보내지 않아요.
- **세션 열기(`session` 권한):** 사용자가 플러그인 화면의 버튼을 눌렀을 때만 앱이 Claude 앱 주소를 열거나, 새 창에서 `claude --resume <세션 번호>`를 실행해요. 이 일로 앱이 따로 내보내는 데이터는 없어요. 새로 뜬 Claude Code가 하는 통신은 Claude Code의 몫이에요.
- **훅 연결(`hooks` 권한, 주의 권한):** 이 권한을 허락하면 앱이 Claude Code 설정 파일에 그 플러그인의 훅을 넣어요(4절). 허락한 플러그인만 쓰고 연결은 사용자가 [연결]을 눌렀을 때만 해요. 훅은 Claude Code가 질문·승인 요청·알림·끝남·오류·프롬프트 제출 때마다 이 앱의 작은 스크립트를 설치 폴더 `resources\node`의 `node.exe`로 실행하게 해요. 이 일로 앱이 따로 내보내는 데이터는 없어요(소식은 위 "알림 훅"대로 이 PC 안으로만 가요). 플러그인은 선언한 이벤트의 소식만 받아요.
- **Codex 알림(`hooks` 권한의 `codex` 대상):** 사용자가 [연결]을 눌렀을 때만 Codex 설정에 알림 명령이 들어가요(4절). Codex가 작업을 한 차례 마칠 때마다 이 앱의 스크립트가 실행되어 소식을 **이 PC의 `127.0.0.1`(들어오는 연결 통로)로만** 보내요. 인터넷이나 다른 기기로는 보내지 않아요. 보내는 것은 "끝났다"는 표시와 Codex의 마지막 답의 앞부분 한 줄(최대 300자이고 비밀처럼 보이는 모양은 `***`로 가려요)뿐이에요. 프롬프트·작업 폴더·Codex 대화 번호는 보내지 않아요. 플러그인은 그 글을 받아요. Codex의 알림 명령은 하나뿐이라 다른 알림 명령이 이미 있으면 연결할 수 없어요. Codex가 나중에 이 방식을 없애면 연결이 끊길 수 있어요. 앱을 지우기 전에 [끊기]로 빼 두세요(7절).
- **Windows 알림(`notify` 권한):** 플러그인이 정한 제목과 본문이 Windows 알림으로 떠요(제목 앞에 플러그인 이름이 붙어요). 알림은 Windows가 보여 주고 알림 센터에 남을 수 있어요. 앱은 그 내용을 따로 저장하거나 보내지 않아요. 알림을 눌렀다는 사실(알림의 짧은 표식)이 그 플러그인에 전해져요.
- **링크 열기(`open-link` 권한):** 사용자가 말풍선 카드의 링크 버튼을 **눌렀을 때만** https 주소를 기본 브라우저로 열어요(버튼 옆에 열릴 호스트가 보여요). 앱이 따로 내보내는 데이터는 없어요. 그 뒤의 일은 브라우저와 그 사이트의 몫이에요.
- **클립보드 쓰기(`clipboard-write` 권한):** 플러그인이 글을 클립보드에 복사할 수 있어요. 읽지는 못해요. 사용자의 클릭 없이도 바꿀 수 있으니 붙여 넣기 전에 내용이 맞는지 확인하세요.
- **비밀 보관(`secrets` 권한):** 플러그인 코드가 받은 토큰·키를 이 PC의 `secrets.bin`에 암호화해 맡겨요. 값은 그 플러그인 코드에는 풀려서 전달되고 같은 Windows 계정의 다른 프로그램은 알아낼 수 있어요. 설정 창의 플러그인 상세 칸에서 개수를 보고 모두 지울 수 있어요(값은 보이지 않아요).
- **AI 사용(`ai` 권한, 주의 권한):** 허락한 플러그인이 보낸 글(시스템 안내·사용자 글·앞선 답·도구 결과)이 지금 고른 질문 방식의 곳으로 가요. Claude Code 방식이면 Claude Code를 거쳐 Anthropic으로 가고(이 방식은 도구 호출을 쓸 수 없어요) API 키 방식이면 `api.anthropic.com`으로 가며 OpenAI 호환 방식이면 내가 "AI 연결"에 적은 주소로 가요(5.1·5.2). **무엇을 보낼지는 플러그인이 정하고** 앱은 그 글을 검열하지 않아요. 플러그인이 읽은 파일 내용이나 비밀 값을 글에 넣으면 그것도 같이 가요. 질문 방식을 바꾸면 이미 허락한 플러그인의 글도 새 곳으로 가요. 앱은 글을 저장하지 않고 로그에는 플러그인 id·방식·모델 이름·토큰 수·걸린 시간만 적어요. 사용량은 `usage\app-ledger.jsonl`에 플러그인 id와 함께 남아요. 플러그인마다 정하는 월 토큰 예산은 API 키 방식에서만 지켜요(OpenAI 호환·Claude Code 방식은 예산을 보지 않아요).
- **프로그램 실행(`run` 권한, 주의 권한):** 허락한 플러그인이 선언한 프로그램을(`shell`을 선언했다면 PowerShell·cmd 명령을) **내 Windows 계정 권한**으로 **내 환경 변수 그대로** 실행해요. 앱 전용 변수(`CLAUDETOOL_`로 시작하는 것과 `ELECTRON_RUN_AS_NODE`)만 빼요. 그래서 실행된 프로그램은 내 계정이 닿는 파일·네트워크·환경 변수(여기에 적어 둔 키 포함)에 닿고 프로그램이 인터넷으로 보내는 통신은 앱이 막지 못해요. 실행할 때마다 승인 카드가 명령줄을 보여 줘요(내가 "이 플러그인은 늘 허용"을 켠 종류는 묻지 않아요). 앱은 프로그램의 출력(표준 출력과 오류 각각 1MB까지)을 플러그인에 돌려줄 뿐 저장하지 않고 로그에는 가린 80자 요약과 종료 결과만 남겨요. 기본 작업 폴더는 `plugin-data\<플러그인 id>\work`예요.
- **파일 읽기·쓰기(`files` 권한, 주의 권한):** 사용자가 설정 창 플러그인 카드에서 **고른 폴더 안의 파일만** 읽고 써요. 폴더 밖이나 링크로 빠져나가는 경로는 막아 뒀어요. 폴더를 고르지 않으면 닿지 못해요. 읽은 내용은 그 플러그인에 전해지고 플러그인이 동의받은 주소나 `ai` 권한의 AI 서버로 보낼 수 있어요. **읽기에는 승인 카드가 없어요**(파일 하나에 1MB까지예요). 쓰기는 쓰기 키로 선언한 폴더에서만 하고 승인 카드를 거쳐요. 드라이브 맨 위나 사용자 폴더처럼 너무 넓은 폴더를 고르면 설정 창이 한 번 더 물어요. 고른 폴더의 경로는 `settings.json`에 적혀요.
- **파일·앱 열기(`open-app` 권한, 주의 권한):** 허락한 플러그인이 파일이나 앱을 **Windows의 기본 프로그램으로 열게** 해요. 열 때마다 승인 카드가 경로를 보여 줘요. 실행 파일과 스크립트(`.exe`·`.bat`·`.ps1` 같은 확장자)는 열지 않아요. 앱이 이 일로 따로 내보내는 데이터는 없어요. 열린 프로그램이 하는 통신은 그 프로그램의 몫이에요.
- **승인 카드와 "늘 허용"(`run`·`files` 쓰기·`open-app`):** 승인 카드는 앱이 직접 띄우는 말풍선이고 60초 안에 답하지 않으면 거부돼요. 카드의 요약은 비밀처럼 보이는 모양을 가려 300자까지 보이고 [자세히]는 1000자까지 보여요. "이 플러그인은 늘 허용"을 누르면 그 플러그인의 그 종류 행동은 `settings.json`에 적어 두고 카드 없이 해요(설정 창 상세 칸에 빨간 줄로 보이고 [끄기]로 꺼요). 최근 승인 20건은 메모리에만 있어서 앱을 끄면 사라지고 로그에는 한 줄씩 남아요.
- 플러그인이 알 수 있는 것은 6절에 있어요.

**5.5 맞춤법 검사**

- 앱 창의 맞춤법 검사는 꺼 두어 사전을 내려받지 않아요. 새 판 확인에 쓰는 네트워크 세션도 확인하기 전에 맞춤법 검사를 꺼 두어요(그렇게 하지 않으면 그 세션이 맞춤법 사전을 Google의 배포 서버에서 내려받아요). 그래서 맞춤법 사전 때문에 밖으로 나가는 연결은 없어요.

**5.6 링크**

- 말풍선 답 속의 링크를 **눌렀을 때만** https 주소를 기본 브라우저로 열어요(다른 형식의 링크는 열지 않아요). 그 뒤의 일은 브라우저와 그 사이트의 몫이에요. 플러그인 말풍선의 마크다운 링크는 글자로만 보이고 눌러도 열리지 않아요. 다만 `open-link` 권한을 허락한 플러그인의 카드 버튼은 사용자가 누를 때 https 주소를 열어요(5.4).

**5.7 새 판 확인과 업데이트**

- 설치 프로그램으로 설치한 앱에서만 켜져요(개발용 실행이나 설치하지 않은 빌드는 확인하지 않아요). 앱을 켠 지 1분 뒤에 말풍선으로 새 판 확인을 처음 안내하고 이때는 접속하지 않아요. 안내에서 [좋아요]를 누르거나 설정 창 › 일반의 [새 판 확인]을 누르면 그때부터 `github.com`에서 공개 저장소의 최신 릴리스 정보를 확인하고 그 뒤로는 앱을 켠 지 1분 뒤에 한 번, 그리고 앱을 켜 두는 동안 24시간마다 확인해요(마지막 확인 시각은 저장하지 않아서 앱을 자주 켜면 켤 때마다 접속해요). [확인 끄기]를 누르면 확인하지 않아요.
- 접속 대상은 `github.com`과 GitHub가 파일을 내려주는 `release-assets.githubusercontent.com`이에요. 저작권자 서버는 없고 GitHub 로그인이나 토큰도 쓰지 않아요. 접속 대상과 요청 머리글은 소스 코드와 이 PC 안의 시험용 서버로 확인한 것이고 실제 GitHub와의 통신을 캡처해 확인한 것은 아니에요.
- 이때 GitHub에는 PC의 IP 주소와 요청 시각이 전해지고 접속 기록은 GitHub가 자신의 개인정보 처리방침에 따라 다뤄요. 요청 머리글에는 도구 이름(`electron-builder`)과 앱 언어(예: `ko`)와 앱이 처음 확인할 때 만들어 데이터 폴더에 저장한 **임의의 번호(UUID)**가 들어가요. 앱 이름·판·운영체제 판은 보내지 않아요. 이 번호는 확인 요청과 GitHub가 파일 서버로 넘기는 요청에 실려요. 사람이나 PC를 가리키지 않지만 같은 번호의 요청을 서로 이어 줄 수는 있어요. 지우려면 데이터 폴더의 `electron\.updaterId` 파일을 지우세요. 질문·설정·키·사용 기록은 보내지 않아요.
- 새 판이 있으면 말풍선과 설정 창과 트레이 메뉴로 알려요. **[받기]를 눌러야** 설치 파일을 GitHub에서 내려받고 **[다시 시작해서 설치]를 눌러야** 설치해요. 설치할 때는 앱이 종료되고 설치가 끝날 때까지 1분쯤 앱이 보이지 않아요. 받은 파일은 Windows 기본 캐시 위치인 `%LOCALAPPDATA%\claude-tool-updater\pending\`에 남아요(데이터 폴더 밖이에요, 2절). 이때 차등 내려받기를 써서, 설치 프로그램이 `%LOCALAPPDATA%\claude-tool-updater\installer.exe`에 남긴 옛 판의 설치 파일 사본과 견줘 **바뀐 부분만** 받아요(견줄 수 없으면 전체를 받아요). 그 사본은 0.4.0부터 남았고 끌 수 없어요(2절).
- 끄는 법: 설정 창 › 일반의 "새 판이 나왔는지 앱을 켠 1분 뒤와 켜 두는 동안 24시간마다 자동으로 확인해요(GitHub에 접속해요)"를 끄세요. 끈 동안은 [새 판 확인]을 누를 때만 접속해요.
- 받은 설치 파일은 `latest.yml`에 적힌 해시(sha512)와 맞을 때만 설치해요. 설치 파일에 코드 서명이 없어서 발행자를 확인하지는 못해요([DISCLAIMER.md](DISCLAIMER.md)의 3.1).

**5.8 하지 않는 것**

- 사용자가 누르지 않은 내려받기·설치, 사용 통계, 충돌 보고서 전송, 광고, 추적을 하지 않아요.
- 승인 카드 없이(내가 "이 플러그인은 늘 허용"을 켠 종류는 빼고) 프로그램을 실행하거나 파일을 쓰거나 앱을 여는 일을 하지 않아요. 내가 [연결]을 누르기 전에 Claude Code나 Codex 설정을 고치는 일도 하지 않아요.
- 앱 화면(펫·설정 창)은 이 PC의 파일만 불러오고, 인터넷의 스크립트·글꼴·그림을 불러오지 않아요.

### 6. 플러그인이 알 수 있는 것

설치형 플러그인은 플러그인마다 보이지 않는 창에서 도는 웹 코드예요.

- **닿지 못하게 만든 것(보증은 아니에요):** 이 PC의 파일(`files` 권한으로 사용자가 고른 폴더 안은 예외예요), 다른 플러그인의 데이터, 앱 화면의 내용, 앱의 질문 기능에서 오간 글, API 키·Admin 키·OpenAI 호환 서버의 키, 클립보드 읽기, 카메라·마이크·위치·화면 캡처. 위험을 줄이려는 장치일 뿐 안전을 보증하지 않아요([DISCLAIMER.md](DISCLAIMER.md)의 3.4 "격리의 한계").
- **닿을 수 있는 것:** 자기 설정 값(비밀 칸의 값 포함), 자기 저장 공간, 허락받은 앱 소식(펫을 눌렀다는 사실, 질문에 답이 왔다는 사실 — 내용은 아니에요), 들어오는 연결로 온 메시지, 창이 기본으로 아는 정보(언어·시간대·화면 크기·현재 시각 등). 허락받은 권한에 따라 자기가 맡긴 비밀(`secrets`), 자기가 띄운 Windows 알림을 눌렀다는 사실(`notify`), 훅이 보낸 Claude Code·Codex 소식(`hooks`), 자기가 AI에 보낸 글과 AI 서버가 돌려준 답(`ai`), 실행한 프로그램의 출력과 종료 코드(`run`), 고른 폴더 안 파일의 내용·목록·이름이 바뀐 소식(`files`), 승인 카드에서 허용했는지 거부했는지(`run`·`files` 쓰기·`open-app`)도 알 수 있어요. 동의받은 주소의 서버는 이 PC의 IP 주소를 알게 돼요.
- 플러그인이 이런 값을 동의받은 주소로 보낼 수 있다는 점은 [DISCLAIMER.md](DISCLAIMER.md)의 3.4에도 적혀 있어요. 동의 창을 읽고 믿을 수 있는 플러그인만 쓰세요.

### 7. 데이터 지우는 방법

- **플러그인 하나:** 설정 창 › 플러그인에서 "지우기"를 누르면 그 플러그인의 폴더·저장 데이터·작업 폴더(`plugin-data\<플러그인 id>\work`)·비밀 값·코드가 맡긴 비밀·토큰·동의 기록·설정 값(고른 폴더·직접 지정한 프로그램 경로·늘 허용·AI 예산 포함)이 함께 지워져요(되돌릴 수 없어요). 고른 폴더 안의 파일은 앱이 지우지 않아요. 훅을 연결했다면 앱이 Claude Code 설정과 Codex 설정에서 그 플러그인의 훅과 알림 명령도 빼요. `hooks\<플러그인 id>\backup\`의 복사본은 남으니 직접 지우세요. 플러그인을 남겨 두고 코드가 맡긴 비밀만 지우려면 상세 칸의 "모두 지우기"를 쓰세요.
- **훅 연결:** 상세 칸의 [끊기]를 누르거나 플러그인을 끄면 앱이 그 플러그인의 훅만 빼요. 앱이 설치된 채 훅이 남았다면 설치 도우미를 `node "<설치 폴더>\resources\app\bridge\claude-notify-setup.mjs" --remove --plugin <플러그인 id>`로 실행해 빼세요(`node`는 `<설치 폴더>\resources\node\node.exe`). 플러그인을 업데이트하면서 새 판에서 `hooks` 권한이 빠졌거나 플러그인 폴더를 직접 지운 경우에는 앱이 훅을 빼지 않으니 이 방법으로 빼세요(남은 훅은 앱이 소식을 받지 않아 아무 일도 하지 않아요). 앱을 지운 뒤에는 도우미도 설치 폴더와 함께 지워지므로 `settings.json`의 `hooks`에서 `claude-notify-hook.mjs`가 든 항목을 직접 지우거나 백업으로 되돌리세요.
- **Codex 연결:** 상세 칸의 Codex [끊기]를 누르거나 플러그인을 끄거나 지우면 앱이 `config.toml`에서 그 플러그인의 알림 명령 한 줄을 빼요. 앱이 설치된 채 남았다면 설치 도우미를 `node "<설치 폴더>\resources\app\bridge\claude-notify-setup.mjs" --remove --plugin <플러그인 id> --target codex`로 실행해 빼세요(`node`는 `<설치 폴더>\resources\node\node.exe`). 앱을 지운 뒤에는 도우미도 함께 지워지므로 `config.toml` 맨 위에서 `claude-notify-hook.mjs`가 든 `notify = [...]` 줄을 직접 지우거나 `hooks\<플러그인 id>\backup\`의 `config.toml.<시각>` 복사본으로 되돌리세요. 남은 줄은 앱을 지운 뒤에는 없어진 스크립트를 가리켜요.
- **시작 시 실행:** 설정 창 › 일반의 체크나 트레이 메뉴의 "Windows 시작 시 실행"을 끄거나 Windows 설정의 "시작 앱"에서 끄세요. 앱을 제거하기 전에 먼저 끄는 것이 안전해요(2절).
- **새 판 확인과 내려받은 파일:** 설정 창 › 일반에서 자동 확인을 끄세요. 받은 설치 파일은 앱을 끈 뒤 `%LOCALAPPDATA%\claude-tool-updater\pending` 폴더를 지우면 없어져요. 요청 머리글의 임의 번호는 `electron\.updaterId`를 지우면 없어져요. `%LOCALAPPDATA%\claude-tool-updater\installer.exe`는 설치 프로그램이 남긴 것이라 직접 지우세요(지우면 다음 새 판은 전체를 받아요). 0.4.2에서 새 판을 받은 적이 있다면 데이터 폴더에 `updater-cache`가 남아 있을 수 있어요. 0.4.3부터는 쓰지 않으니 앱을 끈 뒤 지워도 돼요.
- **AI 연결(OpenAI 호환 서버):** 설정 창 › 일반 › "AI 연결"에서 키 [지우기]를 누르면 `secrets.bin`에서 그 키가 빠져요. 주소와 모델은 칸을 비워 지워요. 질문 방식을 바꾸면 더는 그 서버로 가지 않지만 이미 간 내용은 그 서버에 남아 있을 수 있어요.
- **늘 허용과 승인 기록:** 설정 창 상세 칸의 [끄기]로 "늘 허용"을 꺼요. 최근 승인 20건은 앱을 끄면 사라지고 `plugins.log`의 줄은 남아요.
- **키·비밀 값 전부:** 앱을 끈 뒤 `secrets.bin`을 지우면 저장한 API 키·Admin 키·OpenAI 호환 서버의 키·비밀 칸 값·토큰이 모두 지워져요.
- **로그·사용 기록·캐시:** 앱을 끈 뒤 `logs`, `usage` 폴더를 지워도 돼요. 앱이 다시 만들어요(`usage`를 지우면 이 앱의 사용 기록이 사라져요).
- **Claude Code 연결 흔적:** 사용량 창에서 "연결 해제"를 누르면 상태 줄이 원래대로 돌아가요. `backup\`에 남은 복사본은 직접 지우세요.
- **전부:** 트레이의 "종료"로 앱을 끈 뒤 제거하고, 데이터 폴더를 직접 지우세요(Claude Code 연결을 했다면 제거하기 전에 먼저 "연결 해제"를 누르세요). 설치 프로그램으로 설치했다면 제거해도 데이터 폴더는 남아요.
- **밖에 있는 데이터:** Anthropic이나 내가 적은 OpenAI 호환 서버 쪽에 남은 질문 기록, 플러그인이 밖으로 보낸 데이터는 ClaudeTool이 지울 수 없어요. 그 서비스에 문의하세요.

### 8. 소개 페이지와 배포 안내

- 소개 페이지는 GitHub Pages가 제공하는 정적 페이지예요. 접속 기록은 GitHub가 자신의 개인정보 처리방침에 따라 다뤄요. 소개 페이지에는 외부 스크립트·분석·글꼴·그림이 없어요.
- 소개 페이지의 테마(밝게·어둡게) 버튼은 고른 값을 방문자 브라우저의 localStorage(`ct-theme`)에만 저장하고 서버로 보내지 않아요. 브라우저의 사이트 데이터를 지우면 사라져요.
- 설치 파일은 소개 페이지 저장소(`claude-tool-page`)의 릴리스에서 내려받아요. 내려받을 때의 접속 기록은 GitHub가 자신의 개인정보 처리방침에 따라 다뤄요. 앱은 사용자가 [받기]를 누를 때만 설치 파일을 내려받아요(5.7).

### 9. 문의와 변경

- 개인정보에 관한 문의는 소개 페이지 저장소(`claude-tool-page`)의 Issues로 해 주세요(민감한 정보는 공개된 곳에 쓰지 마세요). 보안 문제는 [SECURITY.md](SECURITY.md)를 따라 주세요.
- 이 문서에 적지 않은 것은 확인하지 못했거나 앱이 하지 않는 일이에요. 문서와 앱이 다르면 알려 주세요.

---

## English

*A courtesy translation. If it differs from the Korean version, the Korean version prevails.*

### 1. At a glance

- ClaudeTool is an **app that runs on your PC.** The app does not talk to any server operated by the Licensor, and the Licensor **does not receive** your questions, settings, usage history or keys.
- ClaudeTool has **no usage statistics, remote analytics or crash-report upload** (the source code was searched for every network call and nothing related to analytics or crash reporting was found; the running app's network traffic was not captured). From 0.4.2 there is a **new-version check** (on by default in an app installed with the installer, and you are told before the first check; how to turn it off is in 5.7).
- Data is stored **only in the data folder on this PC** (Section 2). **The content of questions and answers is not saved to files.**
- Within what was checked, there are five ways data leaves the PC (Section 5): (1) asking questions (they go to Anthropic; if you chose the OpenAI-compatible server under "Question method" in the tray menu they go to the address you entered; when a plugin you allowed the `ai` permission calls an AI, it goes to the same place), (2) organization usage (only if you turn it on), (3) what an installed plugin sends to the addresses you consented to (for a known limit, see 5.4), (4) your default browser opening when you click an https link in a speech bubble (including a link button of a plugin you allowed), (5) the new-version check and download (5.7). The app windows' spell checker is turned off, so no dictionary is downloaded (5.5). No guarantee can be given for everything that components such as Electron, Chromium and Windows do on their own.
- To show usage, the app **reads** the log files Claude Code leaves on this PC (Section 4). Of what it reads it uses only the model name, time and token counts, and it does not store or send the content of questions and answers.
- If you allow an installed plugin the permission to **run programs (`run`), read and write a folder you chose (`files`) or open files and apps (`open-app`)**, that plugin can act on this PC. Running, writing and opening are asked about each time with an approval card that the app shows itself (only the kinds you set to "Always allow this plugin" are not asked). The app does not send the content of these actions to the Licensor or anywhere else. However, what a program does after you allowed it to run cannot be blocked by the app (5.4, 3.4 of [DISCLAIMER.md](DISCLAIMER.md)).
- Only when you turn it on or allow it does the app **change other settings on this PC**: connecting Claude Code (status line), a plugin's Claude Code hook connection and Codex CLI notification connection (Section 4), and starting with Windows (one registry `Run` entry, Section 2). All are off by default and are undone when you turn them off.

### 2. What is stored on your PC

**Where the data folder is**

- If you used the installer, it is `<install folder>-data`, **next to** the install folder. If the install folder is the root of a drive, it is `ClaudeTool-data` under that root.
- If you run the executable without the installer, it is the `data` folder next to the executable.
- You can open it from Settings › General with "Open data folder" / "Open log folder". If you used the installer, the folder remains when you update or uninstall the app.

**Inside the data folder**

| Location | What it contains | Notes |
|---|---|---|
| `settings.json` | Chosen character and its size/opacity, movement, roaming area and monitor, speech-bubble settings, usage-source on/off, question method (Claude Code, API key or OpenAI-compatible server) and model, the address and model name of the OpenAI-compatible server, (if set) the path to the Claude Code executable, and for each installed plugin: on/off, **ordinary setting values**, consent record (permissions, addresses, and the program names and folder labels it declared), window positions, the monthly AI budget (tokens), the kinds of action you set to "always allow", the paths of folders chosen for the `files` permission and the paths of programs you specified for the `run` permission, plus the incoming-connection port, the new-version auto-check on/off (including whether you have seen the first notice) and the start-with-Windows on/off | Ordinary setting values are not encrypted (only secret fields are encrypted, in `secrets.bin`). If the file is damaged it is moved to `settings.json.bak-<time>` and a new one is created. |
| `secrets.bin` | Anthropic API key, Admin API key, the API key of the OpenAI-compatible server (if you entered one), plugin secret-field values, incoming-connection tokens, secrets a plugin's code entrusts to it through the `secrets` permission (up to 20 per plugin), hook-connection tokens | The whole file is encrypted with Windows data protection (DPAPI). If it cannot be decrypted it is moved to `secrets.bin.unreadable-<time>` and the app starts empty. |
| `logs\app.log`, `logs\plugins.log` | Logs of the app and of plugins (built-in features and installed ones) | Section 3. Never deleted or trimmed automatically. |
| `packs\` | Characters you made or imported (image files and `pack.json`) | |
| `plugins\` | Files of installed plugins (the extracted zip, or a folder you put there yourself) | A `.staging` temporary folder briefly appears while importing. |
| `plugin-data\<plugin id>.json` | Values a plugin saved in its "storage" | Not encrypted. Up to 1 MB per plugin. |
| `plugin-data\<plugin id>\work\` | The working folder that a plugin you allowed the `run` permission uses by default when it runs programs (created at the first run) | Files created by the programs that ran. The app does not delete or trim them automatically, and they are deleted together with the plugin when you delete it. |
| `usage\app-ledger.jsonl` | A usage record of questions the app sent: time, model name, token counts (marked as an estimate by character count when the server does not report them), method (API, Claude Code or OpenAI-compatible), the plugin id if a plugin with the `ai` permission made the call, outcome | No question or answer content. Never deleted automatically. |
| `usage\subscription.json` | Subscription limit (5-hour / 7-day) usage ratios, reset times and the Claude Code session number (a random ID) | Section 4 |
| `usage\cache\claude-code.json` | A cache so Claude Code logs need not be re-read: path, size and read position of each log file read, and per-response model, time and token counts for the last 8 days | File paths contain the project folder names Claude Code created (they are made from working-folder paths). Can grow to several MB. |
| `pricing.json` | A per-model price table (for cost estimates) | Created by the app with default values; you may edit it. |
| `backup\` | A copy of Claude Code's `settings.json` made before "Connect"/"Disconnect" is applied | Contains your Claude Code settings as they were. Remains after you disconnect. |
| `claude-notify\token`, `claude-notify\backup\` | Created only if you used the hook setup helper of the notification plugin (claude-notify). `token` is the channel token the hook uses to send news to the plugin; `backup\` holds copies of Claude Code's `settings.json` made before the hooks are added or removed | Not encrypted. The folder is narrowed so only the current user can access it (on a drive that does not support permission settings it may not be narrowed), but other programs under the same account can read it, and a copy may contain keys written in `env`. Delete them yourself if you no longer need them. Removing the hooks (`--remove`) deletes only `token`. |
| `hooks\<plugin id>\token`, `hooks\<plugin id>\backup\` | Created only if you used the app's hook connection (Section 4). `token` is the channel token the hook uses to send news to the plugin (the same value is also kept in `secrets.bin`); `backup\` holds copies of Claude Code's `settings.json` (or, for the Codex connection, Codex's `config.toml`) made before the hooks are added or removed | Not encrypted. The folder is narrowed so only the current user can access it (on a drive that does not support permission settings it may not be narrowed), but other programs under the same account can read it, and a copy may contain keys written in `env` or values written in the Codex settings. If you disconnect only one target (Claude Code or Codex), the app removes only that target's hooks and keeps the `token` while this plugin's hooks remain on the other target. Once the hooks of both targets are gone (including when you turn the plugin off or delete it), the app removes the `token` and leaves `backup\`. Delete it yourself if you no longer need it. |
| `electron\.updaterId` | A random number (UUID) created when the new-version check first ran | Sent in a request header of the check (5.7). It does not identify a person or this PC but can link requests carrying the same number. If you delete it, a new number is created at the next check. |
| `claude-code-cwd\` | An empty working folder used when asking questions through Claude Code | |
| `electron\` | Cache, storage and settings of Chromium (the browser engine) used by the app windows | The key used to decrypt `secrets.bin` is kept here (`Local State`), so deleting this folder makes `secrets.bin` unreadable and you must enter your keys again. |

**What is left outside the data folder**

- **A registry `Run` entry (only if you turn on starting with Windows).** One entry is written under the current user's `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`. No administrator rights are needed and the default is off. Turning it off in Settings › General or from the tray menu deletes the entry. If you turn it off in Windows Settings under "Startup apps", Windows disables the entry and the app aligns its setting by turning it off the next time it starts. It could not be confirmed whether the uninstaller deletes this entry, so turn it off before you uninstall the app.
- **The `pending\` folder and the `current.blockmap` file in `%LOCALAPPDATA%\claude-tool-updater\`.** Created **only when you press [Download] and get a new version**. `pending\` holds the installer you downloaded (about 125 MB) and its information, and `current.blockmap` holds a small piece of information the differential download uses. This is the default Windows cache location, so it is outside the data folder. The app deletes the `pending\` folder of an already installed version when the new version starts; otherwise it is cleared at the next download. You may also delete the `pending\` folder after quitting the app (5.7).
- **`%LOCALAPPDATA%\claude-tool-updater\installer.exe`.** Each time the installer installs or updates, it leaves a copy of the installer file there (it has done so since 0.4.0, it cannot be turned off by a setting, and the uninstaller does not delete it). When you download a new version, the differential download compares against this copy and downloads only what changed (5.7). Delete it yourself if you no longer need it (if you do, the next new version is downloaded whole).
- **Another program's settings file (only if you turn a connection on).** If you turn on a hook connection, that plugin's hooks are put into Claude Code's `settings.json` (Section 4). If you turn on the Codex connection, one notification-command line is put at the top of `config.toml` in the Codex settings folder (the folder named by `CODEX_HOME` if set, otherwise `.codex` under your user folder). Both are written only when you press [Connect] in the detail area. When you disconnect, or turn the plugin off and delete it, the app removes that line. After the app is gone you must remove it yourself (Section 7).

**What is not stored**

- **The content of questions and answers.** To let you ask follow-ups, the app remembers the recent conversation **in memory only** (up to 6 turns, up to 10 minutes after the last answer) while it is running; it is gone when you quit.
- **Text a plugin with the `ai` permission sends and receives.** The app does not store it and does not write it to the log. What a plugin keeps in its own storage is up to the plugin.
- **The content of files in a chosen folder and the output of programs that ran.** The app only hands them to the plugin and does not copy or store them.
- **Cookies and browser storage of plugin windows.** A plugin window's temporary storage exists only in memory and disappears when you quit. The only plugin data left on disk is `plugin-data`.
- **Screen content, clipboard and keystrokes.** The app does not collect these. It registers one global shortcut, for asking questions (default `Ctrl+Alt+K`), and only writes to the clipboard when you press "Copy token" (it never reads it). A plugin you gave the `clipboard-write` permission can also write text to the clipboard but cannot read it. The notification-hook setup helper that you run yourself (a script separate from the app), however, reads the clipboard once when you run `--apply` and saves it to `claude-notify\token` only if it looks like a token (the content is not shown on screen).

### 3. What the logs contain and what they do not

- Logs are appended line by line to `logs\app.log` (the app) and `logs\plugins.log` (built-in features and installed plugins). They are never deleted or trimmed automatically, so they keep growing.
- **What is recorded:** a time and a one-line description. App start (including the data folder path), names of enabled features, the result of registering the shortcut, the fact that a key or token was saved or removed (only which field, never the value), error and warning messages (which may contain file paths), plugin start/stop (id, version, reason), connection attempts a plugin was blocked from (only the origin, never path, query, headers or body) and failed outgoing connections (method, origin, error code), the fact that the incoming-connection channel was opened or closed (`127.0.0.1` and the port), the result of a new-version check, download or installer start (addresses are written with the query string removed), the result of connecting or disconnecting hooks and the fact that a hook message was dropped (only the event name), the name of the error when starting with Windows could not be changed, one line per `ai` call (plugin id, method, model name, input and output token counts, time taken, why it ended), one line per program run (an 80-character masked summary and the result), one line per approval request (allowed, always allowed, auto-allowed or denied, with the reason, and an 80-character masked summary), the fact that a folder watch stopped, and what a plugin itself writes to the log plus console warnings and errors (up to 60 lines per minute and 2,000 characters per line; what is written is up to the plugin).
- **What is built not to be recorded:** the content of questions, answers and system prompts; text sent to and received from an AI through `ai`; the output of programs; file contents; the values of API keys, Admin keys, the OpenAI-compatible server key, secret fields and tokens; successful plugin requests. However, an error message can include the error description returned as is by an Anthropic server or Claude Code, and if a plugin writes a secret value to its own log it will remain. An approval summary is written with only three secret-looking shapes (the value after `Bearer`, forms such as `KEY=value`, `TOKEN=value` or `PASSWORD=value`, and keys starting with `sk-`) masked as `***`. A secret written in the command line in any other shape can remain in the 80-character summary.
- Before showing or uploading a log, check whether it contains personal information such as paths and names.

### 4. What the app reads

- **Claude Code logs (usage view).** The usage source "Claude Code" (on by default) looks for and reads the `.jsonl` files under `projects` in the Claude Code folder (normally `.claude` under your user folder, or the folder named by `CLAUDE_CONFIG_DIR`) when you open the usage window (and every minute while it stays open); it skips `tool-results` folders. It reads the files but uses only the model name, time, response number and token counts, and does not store or send the content of questions, answers or tool results. You can turn it off under "Usage sources" in the tray menu.
- **Claude Code settings file.** It reads `settings.json` in the Claude Code folder only when you press "Connect Claude Code" or "Disconnect" in the usage window and when you use the hook connection below. "Connect Claude Code" shows what will change, edits the file only after you press **Apply**, and first copies the original to `backup\`. It does not read it at any other time.
- **Hook connection (a plugin you gave the `hooks` permission).** Right after you install or turn on such a plugin the app asks once "Connect to Claude Code?", and pressing the plugin's [Connect] or [Disconnect] in the settings window does the same. When you connect, the app puts that plugin's notification hooks into Claude Code's `settings.json` (your other hooks and settings and other plugins' hooks are left alone). Before changing it the app copies the original to `hooks\<plugin id>\backup\`, and it does not write if the file changed after it was read. To show the connection state it also reads this file when you select that plugin's card in the settings window, but it only reads and does not write. When you turn the plugin off or delete it, the app edits the file once more to remove that plugin's hooks. What the hooks do is in "The notification hook" in 5.4. Plugin code cannot reach this settings file.
- **Codex connection (the `codex` target of the `hooks` permission).** When you press [Connect] or [Disconnect] for that plugin in the settings window, and when you select that plugin's card to show the connection state, it reads `config.toml` in the Codex settings folder (the folder named by `CODEX_HOME` if set, otherwise `.codex` under your user folder). When it only reads, it does not write. When you press [Connect] it puts only one notification-command line (`notify = [...]`) at the top of `config.toml` and does not touch other lines. Before changing it the app copies the whole file to `hooks\<plugin id>\backup\` and does not write if the file changed after it was read. If another notification command already exists, or the shape of the file cannot be judged, it does not put one in. The window asked right after you install a plugin asks only about Claude Code and neither asks about nor changes the Codex settings. It does not read Codex's sign-in or credential files. This notification command makes Codex run a small script of this app each time Codex finishes a turn. What the script sends is in "Codex notifications" in 5.4. Plugin code cannot reach this settings file.
- **What connecting does.** A small script of this app is registered as Claude Code's status line (statusLine) command. Each time Claude Code draws its status line this script runs with the `node.exe` in the `resources\node` folder of the install folder and, of the status information Claude Code passes in, writes **only the limit usage ratios, reset times and session number** to `usage\subscription.json`. If you already had a status-line command, the same input is passed to it and it keeps running. When connecting, the app uses the `node.exe` in the install folder's `resources\node` first; if it is missing or fails, it runs `where node` and `node --version` to find the Node.js on your PC. Pressing "Disconnect" restores the original.
- **Where it looks.** To find the Claude Code executable (`claude.exe`) it looks through `PATH` and `.local\bin` under your user folder. It does not read Claude Code's sign-in or credential files.
- **Finding programs (`run` permission).** For each program name a plugin declared in `run`, it looks through the folders of `PATH` for that program file (it does not look in the current folder). The path it found is shown in the plugin's detail area in the settings window, and you can also set one yourself.
- **A chosen folder (`files` permission).** Each time a plugin asks, the app reads files inside the folder you chose in the plugin card of the settings window and hands them to that plugin. It also tells the plugin when file names in the folder change (only the path, not the content). If you have not chosen a folder, it reads nothing. Details are in 5.4.

### 5. What leaves your PC

**5.1 Asking questions: Claude Code method (default)**

- For each question the app starts your PC's Claude Code afresh and passes the question (plus part of the earlier conversation when you are following up) through standard input. The system prompt (by default a short instruction to answer briefly, which you can change in the settings window) and the chosen model name go along. The system prompt is passed as a launch argument, so do not put secrets in it.
- Claude Code is run **to answer only**: all tools that read files or run commands and MCP are turned off, Claude Code's settings files, `CLAUDE.md` and memory are not read, and no conversation record (session) is kept. Environment variables such as `ANTHROPIC_API_KEY` on this PC are not passed on, so the question is handled by your subscription, not by API charges.
- The question is **sent to Anthropic** through Claude Code. How Anthropic processes and how long it keeps that content follows Anthropic's terms and privacy policy. ClaudeTool does not control what happens inside Claude Code (its own records, etc.).
- Only the text you typed in the question box goes out. Files, the screen, the clipboard and usage records are not sent.

**5.2 Asking questions: API-key method and OpenAI-compatible server method (optional)**

- **API-key method.** Used only if you switch to the API-key method under "Question method" in the tray menu. The same content is sent directly to the Anthropic API address (`api.anthropic.com`) with your API key in a request header. The information the Anthropic SDK adds to requests by default (SDK version, operating system and CPU type, Node.js version) goes along. This address cannot be changed in an installed build.
- **OpenAI-compatible server method (from 0.4.3).** Used only if you choose the OpenAI-compatible server under "Question method" in the tray menu or under Settings › General › "AI connection". The question (plus part of the earlier conversation when you are following up), the system prompt and the chosen model name are sent to `/chat/completions` of **the address you entered under "AI connection"**. The default address is `http://127.0.0.1:11434/v1`, which points to a server running on this PC. The address is `http` or `https`. If you entered a key, it goes in a request header (`Authorization`), and the app name (`ClaudeTool/…`) is put in the `User-Agent`. If the server redirects to another address, the app does not follow it.
- Pressing [Check connection] in the settings window requests the model list from `/models` of that address (a saved key is sent only to the same address it was saved for). It requests only when you press it and stops if there is no answer within 5 seconds.
- **If the address is outside this PC, the content of your questions goes to that server.** An `http` address that is not `https` can be read on the way. The settings window always shows "This is an address outside this PC. The content of your questions goes to that server" when the address is neither on this PC (`localhost`, `127.0.0.1`) nor on your home or office network (private addresses, `.local` names). A host whose location cannot be told from its name alone (for example `nas`) is also treated as outside. An internal-network address means a different device on the same network even though no warning is shown. How that server handles and how long it keeps the content is up to the operator of that server, and ClaudeTool does not control it. Do not type passwords, keys, personal data or confidential information.

**5.3 Organization usage (optional, off by default)**

- Used only if you turn it on under "Usage sources" in the tray menu and enter an Admin API key. While on, it asks `api.anthropic.com` for the organization's usage and cost reports every 5 minutes (every minute while the usage window is open), with the Admin key in a request header and the app name (`ClaudeTool/…`) in the User-Agent. The result is only shown on screen and is not saved to a file.

**5.4 Installed plugins**

- A plugin is made to connect only to the "addresses it can connect to" you consented to when installing, but this is not perfect (HTTP/HTTPS requests are made by the app on its behalf; WebSocket opens only to declared addresses). What it sends is up to the plugin, and the app does not censor or record it (only the addresses of blocked or failed attempts are logged).
- **Known limit:** a plugin screen can carry a small amount of information in the names of DNS lookups (`dns-prefetch`) and send it **even to places you did not consent to**, and the app cannot block this (the receiver has to run a DNS server, so the amount is small). See 3.4 of [DISCLAIMER.md](DISCLAIMER.md).
- **The notification hook (claude-notify):** whether it was added by the app's hook connection or by the 0.4.1 manual setup helper, the hook sends its news only to this PC's `127.0.0.1` (the incoming-connection channel). It does not send anything to the internet or to other devices. What it sends is the kind of notice, the hook event name and reason (a short label such as a tool name), the Claude Code session number, the working-folder path, the entry point the session was opened from, the session number inside the desktop app, the tool-call number, and a short one-line text (a title and a body, which are the beginning of a command, a question or the last answer, with secret-looking shapes masked as `***`). It does not send the content of prompts or the path of conversation record files.
- **Opening sessions (`session` permission):** only when you press a button on a plugin screen, the app opens a Claude app address or runs `claude --resume <session number>` in a new window. The app sends no data out of its own for this. What the newly started Claude Code communicates is up to Claude Code.
- **Hook connection (`hooks` permission, a caution permission):** if you allow this permission, the app puts that plugin's hooks into Claude Code's settings file (Section 4). Only a plugin you allowed uses it, and the connection is made only when you press [Connect]. The hooks make Claude Code run a small script of this app, with the `node.exe` in the `resources\node` folder of the install folder, whenever Claude Code asks a question, requests approval, notifies, finishes, fails or receives a prompt. The app sends no data out of its own for this (the news goes only inside this PC, as in "The notification hook" above). A plugin receives only the events it declared.
- **Codex notifications (the `codex` target of the `hooks` permission):** a notification command is put into the Codex settings only when you press [Connect] (Section 4). Each time Codex finishes a turn, a script of this app runs and sends the news **only to this PC's `127.0.0.1` (the incoming-connection channel)**. It does not send anything to the internet or to other devices. What it sends is only a "finished" mark and one short line from the beginning of Codex's last answer (up to 300 characters, with secret-looking shapes masked as `***`). It does not send prompts, the working folder or the Codex conversation number. The plugin receives that text. Codex has only one notification command, so if another one already exists you cannot connect. If Codex later removes this mechanism, the connection may stop working. Remove it with [Disconnect] before you delete the app (Section 7).
- **Windows notifications (`notify` permission):** the title and body a plugin chooses are shown as a Windows notification (the plugin name is put in front of the title). Windows shows it and it may remain in the notification center. The app does not store or send its content. That you clicked a notification (a short tag of it) is passed to that plugin.
- **Opening links (`open-link` permission):** **only when you press** a link button on a speech-bubble card, an https address is opened in your default browser (the host that will open is shown next to the button). The app sends no data out of its own for this. What happens afterwards is up to the browser and that site.
- **Writing to the clipboard (`clipboard-write` permission):** a plugin can copy text to the clipboard. It cannot read it. It can change it even without your click, so check that what you paste is right.
- **Keeping secrets (`secrets` permission):** a plugin's code entrusts tokens and keys it received to `secrets.bin` on this PC, encrypted. The value is decrypted and handed to that plugin's code, and other programs under the same Windows account can find it out. In the plugin's detail area of the settings window you can see the count and delete them all (the values are not shown).
- **Using AI (`ai` permission, a caution permission):** the text a plugin you allowed sends (system instructions, user text, earlier answers, tool results) goes to wherever the question method you chose now sends it. With the Claude Code method it goes to Anthropic through Claude Code (this method cannot use tool calls); with the API-key method it goes to `api.anthropic.com`; with the OpenAI-compatible method it goes to the address you entered under "AI connection" (5.1 and 5.2). **What is sent is up to the plugin**, and the app does not censor it. If a plugin puts the contents of a file it read or a secret value into the text, that goes along. If you change the question method, the text of plugins you already allowed goes to the new place. The app does not store the text, and the log records only the plugin id, method, model name, token counts and time taken. Usage is kept in `usage\app-ledger.jsonl` with the plugin id. The monthly token budget you set for each plugin is enforced only with the API-key method (the OpenAI-compatible and Claude Code methods do not check the budget).
- **Running programs (`run` permission, a caution permission):** a plugin you allowed runs the programs it declared (or, if it declared `shell`, PowerShell or cmd commands) **with your Windows account's rights** and **with your environment variables as they are**. Only the app's own variables (those starting with `CLAUDETOOL_` and `ELECTRON_RUN_AS_NODE`) are removed. So a program that ran can reach the files, network and environment variables (including keys written there) that your account can reach, and the app cannot block what the program sends over the internet. Each run shows an approval card with the command line (kinds you set to "Always allow this plugin" are not asked). The app only hands the program's output (up to 1 MB each for standard output and error) back to the plugin and does not store it, and the log keeps only an 80-character masked summary and the exit result. The default working folder is `plugin-data\<plugin id>\work`.
- **Reading and writing files (`files` permission, a caution permission):** a plugin reads and writes **only files inside the folder you chose** in the plugin card of the settings window. Paths that escape the folder or leave it through a link are blocked. Without a chosen folder it cannot reach anything. What it reads is handed to that plugin, and the plugin can send it to addresses you consented to or to the AI server through the `ai` permission. **There is no approval card for reading** (up to 1 MB per file). Writing is done only in a folder declared with a write key, and goes through an approval card. If you choose a folder that is too wide, such as the top of a drive or your user folder, the settings window asks once more. The path of the chosen folder is written in `settings.json`.
- **Opening files and apps (`open-app` permission, a caution permission):** a plugin you allowed can make **Windows open a file or app with its default program**. Each time, an approval card shows the path. Executables and scripts (extensions such as `.exe`, `.bat` and `.ps1`) are not opened. The app sends no data out of its own for this. What the opened program communicates is up to that program.
- **Approval cards and "Always allow" (`run`, `files` writing, `open-app`):** the approval card is a speech bubble that the app shows itself, and it is denied if you do not answer within 60 seconds. The card summary is shown up to 300 characters with secret-looking shapes masked, and [Details] shows up to 1,000 characters. If you press "Always allow this plugin", that plugin's actions of that kind are written in `settings.json` and done without a card (it is shown as a red line in the detail area of the settings window and turned off with [Turn off]). The latest 20 approvals are kept only in memory and disappear when you quit the app, and one line each stays in the log.
- What a plugin can know is in Section 6.

**5.5 Spell checking**

- The app windows' spell checker is turned off, so no dictionary is downloaded. The network session used for the new-version check also has its spell checker turned off before the check (otherwise that session would download a spell-check dictionary from Google's distribution server). There is therefore no outside connection for a spell-check dictionary.

**5.6 Links**

- **Only when you click** a link inside a speech-bubble answer, an https address is opened in your default browser (links of other kinds are not opened). What happens afterwards is up to the browser and that site. Markdown links in a plugin's speech bubble are shown as plain text and do not open. However, a card button of a plugin you gave the `open-link` permission opens an https address when you press it (5.4).

**5.7 New-version check and updates**

- It is on only in an app installed with the installer (a development run or a build that was not installed does not check). One minute after the app starts it first shows a speech-bubble notice about the new-version check and does not connect at this point. When you press [OK] in the notice or press [Check for new version] in Settings › General, it checks `github.com` for the latest release information of the public repository from then on, and after that it checks one minute after each time the app starts and every 24 hours while the app stays open (the time of the last check is not saved, so if you start the app often it connects at every start). If you press [Turn off checking], it does not check.
- It connects to `github.com` and to `release-assets.githubusercontent.com`, from which GitHub serves files. There is no server of the Licensor and no GitHub login or token is used. The connection targets and request headers were confirmed from the source code and a test server inside this PC; the actual communication with GitHub was not captured.
- GitHub learns this PC's IP address and the time of the request, and handles the access records under its own privacy policy. The request headers contain the name of a tool (`electron-builder`), the app language (for example `ko`) and a **random number (UUID)** that the app created at its first check and saved in the data folder. The app name, version and Windows version are not sent. This number is carried by the check request and by the requests GitHub redirects to its file server. It does not identify a person or this PC but can link requests carrying the same number. To remove it, delete the file `electron\.updaterId` in the data folder. Questions, settings, keys and usage records are not sent.
- If a new version exists, it is announced in a speech bubble, the settings window and the tray menu. **Only when you press [Download]** does it download the installer from GitHub, and **only when you press [Restart and install]** does it install. While installing, the app quits and is not visible for about a minute until the installation ends. The downloaded file stays in the default Windows cache location, `%LOCALAPPDATA%\claude-tool-updater\pending\` (outside the data folder, Section 2). The download is differential: it compares against the copy of the old version's installer that the installer left at `%LOCALAPPDATA%\claude-tool-updater\installer.exe` and downloads **only the parts that changed** (if it cannot compare, it downloads the whole file). That copy has been left since 0.4.0 and this cannot be turned off (Section 2).
- To turn it off: turn off "Check for a new version automatically one minute after the app starts and every 24 hours while it stays open (connects to GitHub)" in Settings › General (the label of the Korean screen is "새 판이 나왔는지 앱을 켠 1분 뒤와 켜 두는 동안 24시간마다 자동으로 확인해요(GitHub에 접속해요)"). While it is off, the app connects only when you press [Check for new version].
- The downloaded installer is installed only if it matches the hash (sha512) written in `latest.yml`. The installer is not code-signed, so the publisher cannot be verified (3.1 of [DISCLAIMER.md](DISCLAIMER.md)).

**5.8 What it does not do**

- No downloads or installations you did not press for, usage statistics, crash-report uploads, advertising or tracking.
- No running programs, writing files or opening apps without an approval card (except for the kinds you set to "Always allow this plugin"), and no changing of Claude Code or Codex settings before you press [Connect].
- The app's own screens (the pet and the settings window) load only files from this PC and load no scripts, fonts or images from the internet.

### 6. What a plugin can know

An installable plugin is web code running in its own invisible window.

- **What it is built not to reach (not a guarantee):** files on this PC (except inside a folder you chose through the `files` permission), other plugins' data, the content of app screens, text exchanged in the app's own question feature, API/Admin keys and the OpenAI-compatible server key, reading the clipboard, the camera, microphone, location and screen capture. These are ways to reduce risk and do not guarantee safety (see "Limits of isolation" in 3.4 of [DISCLAIMER.md](DISCLAIMER.md)).
- **What it can reach:** its own setting values (including secret-field values), its own storage, the app events it was allowed to receive (that the pet was clicked, that an answer to a question arrived — not its content), messages arriving through incoming connections, and what a window knows by default (language, time zone, screen size, current time, etc.). Depending on the permissions it was given, it can also know the secrets it entrusted itself (`secrets`), that a Windows notification it showed was clicked (`notify`), the Claude Code and Codex news the hooks sent (`hooks`), the text it sent to an AI and the answer the AI server returned (`ai`), the output and exit code of programs it ran (`run`), the contents and list of files in a chosen folder and news that a file name changed (`files`), and whether you allowed or denied an approval card (`run`, `files` writing, `open-app`). The servers at the addresses it was allowed to contact learn this PC's IP address.
- That a plugin can send such values to the addresses you consented to is also stated in 3.4 of [DISCLAIMER.md](DISCLAIMER.md). Read the consent window and use only plugins you trust.

### 7. How to delete data

- **One plugin:** pressing "Delete" in Settings › Plugins also deletes that plugin's folder, saved data, working folder (`plugin-data\<plugin id>\work`), secret values, secrets entrusted by its code, token, consent record and setting values (including chosen folders, program paths you specified, always-allow and the AI budget) (it cannot be undone). The app does not delete files inside a chosen folder. If you connected hooks, the app also removes that plugin's hooks and notification command from the Claude Code and Codex settings. The copies in `hooks\<plugin id>\backup\` remain, so delete them yourself. To keep the plugin and delete only the secrets entrusted by its code, use "Delete all" in the detail area.
- **Hook connection:** pressing [Disconnect] in the detail area or turning the plugin off makes the app remove only that plugin's hooks. If hooks are left behind while the app is still installed, remove them by running the setup helper as `node "<install folder>\resources\app\bridge\claude-notify-setup.mjs" --remove --plugin <plugin id>` (`node` is `<install folder>\resources\node\node.exe`). If you updated a plugin to a version that no longer has the `hooks` permission, or deleted the plugin folder by hand, the app does not remove the hooks, so remove them this way (the remaining hooks do nothing because the app does not receive their news). After the app is deleted, the helper is deleted together with the install folder, so delete the entries containing `claude-notify-hook.mjs` from `hooks` in `settings.json` yourself or restore the backup.
- **Codex connection:** pressing Codex [Disconnect] in the detail area, or turning the plugin off or deleting it, makes the app remove that plugin's notification-command line from `config.toml`. If it was left behind while the app is still installed, remove it by running the setup helper as `node "<install folder>\resources\app\bridge\claude-notify-setup.mjs" --remove --plugin <plugin id> --target codex` (`node` is `<install folder>\resources\node\node.exe`). After the app is deleted the helper is deleted together with it, so delete the `notify = [...]` line containing `claude-notify-hook.mjs` at the top of `config.toml` yourself, or restore the `config.toml.<time>` copy in `hooks\<plugin id>\backup\`. A leftover line points at a script that no longer exists after the app is deleted.
- **Starting with Windows:** turn off the check in Settings › General or "Windows 시작 시 실행" (start with Windows) in the tray menu, or turn it off in Windows Settings under "Startup apps". It is safer to turn it off before uninstalling the app (Section 2).
- **New-version check and downloaded files:** turn off the automatic check in Settings › General. After quitting the app, deleting the `%LOCALAPPDATA%\claude-tool-updater\pending` folder removes the downloaded installer. Deleting `electron\.updaterId` removes the random number in the request headers. `%LOCALAPPDATA%\claude-tool-updater\installer.exe` was left by the installer, so delete it yourself (if you do, the next new version is downloaded whole). If you downloaded a new version with 0.4.2, `updater-cache` may remain in the data folder; 0.4.3 and later do not use it, so you may delete it after quitting the app.
- **AI connection (OpenAI-compatible server):** pressing [Delete] for the key under Settings › General › "AI connection" removes that key from `secrets.bin`. Clear the address and model by emptying the fields. If you change the question method, nothing goes to that server any more, but what was already sent may remain there.
- **Always allow and approval records:** turn "Always allow" off with [Turn off] in the detail area of the settings window. The latest 20 approvals disappear when you quit the app, and the lines in `plugins.log` remain.
- **All keys and secret values:** after quitting the app, delete `secrets.bin` to erase all saved API keys, Admin keys, the OpenAI-compatible server key, secret-field values and tokens.
- **Logs, usage records, caches:** after quitting the app you may delete the `logs` and `usage` folders. The app recreates them (deleting `usage` erases this app's usage history).
- **Traces of connecting Claude Code:** press "Disconnect" in the usage window to restore the status line. Delete the copies left in `backup\` yourself.
- **Everything:** quit the app with "Quit" in the tray menu, uninstall it, and delete the data folder yourself (if you connected Claude Code, press "Disconnect" before uninstalling). If you used the installer, the data folder remains after uninstalling.
- **Data outside your PC:** question records kept on Anthropic's side or on the OpenAI-compatible server you entered, and data a plugin sent out, cannot be deleted by ClaudeTool. Contact those services.

### 8. The introduction page and distribution

- The introduction page is a static page served by GitHub Pages. Access logs are handled by GitHub under its own privacy policy. The introduction page contains no external scripts, analytics, fonts or images.
- The theme (light/dark) button on the introduction page stores your choice only in your own browser's localStorage (`ct-theme`) and does not send it to any server. It disappears when you clear the browser's site data.
- The installer is downloaded from the Releases of the introduction-page repository (`claude-tool-page`). GitHub handles the access records of downloads under its own privacy policy. The app downloads an installer only when you press [Download] (5.7).

### 9. Questions and changes

- For privacy questions, please use the Issues of the introduction-page repository (`claude-tool-page`) (do not post sensitive information in public). For security problems, follow [SECURITY.md](SECURITY.md).
- Anything not written here is either something that could not be confirmed or something the app does not do. If this document and the app differ, please report it.
