# 면책조항과 보안사고 면책 (Disclaimer)

> 이 문서는 법률 자문이 아니고, 변호사의 검토를 받은 문서도 아니에요. 회사 업무·영리 목적 등으로 쓰거나 배포하기 전에는 전문가의 검토를 받으세요.
>
> *This document is not legal advice and has not been reviewed by a lawyer. Get professional advice before any business or commercial use or distribution.*

ClaudeTool 개인 사용 라이선스 v1.0([LICENSE](LICENSE))의 일부예요. 소프트웨어를 쓰기 전에 읽어 주세요. 한국어본과 영어본이 함께 있고, 뜻이 다르면 한국어본이 우선해요. 함께 읽으면 좋은 문서: [SECURITY.md](SECURITY.md)(보안 문제 신고), [PRIVACY.md](PRIVACY.md)(개인정보), [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)(제3자 소프트웨어).

*This document is part of the ClaudeTool Personal Use License v1.0 ([LICENSE](LICENSE)). A Korean and an English version are provided; if they differ, the Korean version prevails. See also: [SECURITY.md](SECURITY.md) (reporting security problems), [PRIVACY.md](PRIVACY.md) (privacy) and [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) (third-party software).*

---

## 한국어

### 1. 있는 그대로 제공해요(무보증)

ClaudeTool(이하 "소프트웨어")은 **개인 사용자에게 무료로, 있는 그대로("AS IS")** 제공해요. 저작권자는 관련 법령이 허락하는 가장 넓은 범위에서 다음을 포함한 모든 명시적·묵시적 보증을 하지 않아요.

- 오류가 없다는 것, 끊기지 않고 동작한다는 것, 모든 환경(Windows 버전·화면 배율·다른 프로그램)에서 동작한다는 것
- 상품성, 특정 목적에 대한 적합성, 제3자의 권리를 침해하지 않는다는 것
- 이 소프트웨어가 보여 주는 정보(사용량·한도·비용·답변)가 정확하거나 완전하다는 것
- 격리·동의·연결 제한·토큰·암호화 저장 같은 **안전 장치가 빈틈없이 동작하거나, 모든 공격과 사고를 막아 준다는 것**

### 2. 책임의 제한

관련 법령이 허락하는 가장 넓은 범위에서, 저작권자는 소프트웨어를 쓰거나 쓰지 못해서 생긴 **직접·간접·특별·결과적 손해**(데이터·파일 손실, 설정 손상, 이익 손실, 금전 손실, 업무 중단, 계정 정지, 뜻하지 않은 요금, 구독 사용량이나 API 한도 초과, 기기 고장, 제3자 서비스의 문제로 생긴 손해 등)에 대해 책임을 지지 않아요. 소프트웨어는 무료이므로, 책임이 인정되더라도 그 한도는 사용자가 저작권자에게 낸 금액(0원)으로 해요.

다만 **저작권자의 고의 또는 중대한 과실로 생긴 손해**와 **법령상 배제할 수 없는 책임**(소비자 보호 관련 법령 등)은 이 조항에서 제외해요.

### 3. 보안사고 면책

#### 3.1 이 소프트웨어가 하는 일(알아 두세요)

무엇을 저장하고 읽고 보내는지는 [PRIVACY.md](PRIVACY.md)에 자세히 적혀 있고, 핵심은 이래요.

- **사용량을 보여 주려고** Claude Code가 이 PC에 남긴 기록 파일(`.claude\projects`)을 읽어요. 파일을 읽지만 모델 이름·시각·토큰 수만 뽑아 쓰고, 질문과 답의 내용은 저장하거나 어디로 보내지 않아요.
- **Claude Code 설정 파일**은 사용자가 "Claude Code 연결"·"연결 해제"를 누를 때만 읽고 고쳐요(고치기 전에 보여 주고, 원래 파일은 백업해요).
- **"Claude Code 연결"을 하면 Claude Code의 `settings.json`에 이 앱의 상태 줄(statusLine) 명령이 써 넣어져요.** 그러면 Claude Code가 상태 줄을 그릴 때마다 이 앱의 작은 스크립트가 설치 폴더 `resources\node`의 `node.exe`로 실행되고(없거나 실패하면 PC의 Node.js를 찾아요) 한도 정보만 데이터 폴더에 적어요(자세한 내용은 [PRIVACY.md](PRIVACY.md)의 4절). 원래 쓰던 상태 줄 명령이 있었다면 그것도 이어서 실행해요.
- **앱을 제거하기 전에는 먼저 "연결 해제"를 누르세요.** 그러지 않으면 이 앱의 상태 줄 명령이 Claude Code 설정에 그대로 남아요(남은 명령은 `settings.json`에서 직접 지우거나 원래 값으로 되돌려야 하고, 원래 값은 데이터 폴더 `backup\`의 복사본에 있어요). 설치 위치를 바꿔 다시 설치했다면 "연결 해제"를 한 뒤 다시 연결하세요(스크립트의 위치가 달라지기 때문이에요).
- **알림 훅(claude-notify)을 연결하면** 설치 도우미(`bridge\claude-notify-setup.mjs`)가 Claude Code의 `settings.json`에 알림 훅 6개를 써 넣어요(미리보기로 보여 주고, 고치기 전에 원래 파일을 백업해요). 데이터 폴더의 `claude-notify\`에는 통로 토큰(`token`)과 `settings.json` 복사본(`backup\`)이 쌓여요. 이 폴더는 현재 사용자만 접근하도록 좁혀 쓰지만(권한 설정이 되지 않는 드라이브에서는 좁혀지지 않을 수 있어요) **같은 Windows 계정의 다른 프로그램은 읽을 수 있고**, 백업에는 `env`에 적어 둔 키 같은 비밀이 들어 있을 수 있어요. 훅은 소식을 이 PC의 `127.0.0.1`로만 보내요. 앱을 제거하기 전에는 설치 도우미의 `--remove`로 훅을 빼세요(그러지 않으면 훅이 Claude Code 설정에 남고, 없어진 스크립트를 가리켜요).
- **API 키·Admin 키·플러그인의 비밀 칸 값·들어오는 연결 토큰**은 Windows의 보호 기능(DPAPI)으로 암호화해 `secrets.bin`에 저장해요. 이 방식은 **같은 Windows 계정에서 실행되는 다른 프로그램(악성 프로그램 포함)이 값을 알아낼 수 있어요.** 완전한 금고가 아니에요.
- **질문**은 이 PC에 로그인된 Claude Code(기본) 또는 Anthropic API(API 키 방식을 고른 경우)를 거쳐 **Anthropic으로 전송돼요.** 비밀번호·키·개인정보·회사 기밀은 입력하지 마세요.
- **설치형 플러그인**과 **가져온 캐릭터·플러그인 zip**은 저작권자가 아닌 사람이 만든 것일 수 있어요(아래 3.4). 플러그인은 동의받은 주소로 인터넷에 연결할 수 있어요.
- 플러그인이 "들어오는 연결"을 쓰면, 켜져 있는 동안 이 PC의 `127.0.0.1`(이 PC 안에서만 닿는 주소)에 연결을 받는 통로가 열려요. 다른 기기에서는 닿지 않지만, **같은 PC에서 실행되는 다른 프로그램**은 이 통로에 접속을 시도할 수 있어요(플러그인별 토큰이 있어야 받아 줘요).
- 이와 별개로 앱은 **켜질 때마다** 설치형 플러그인 창의 인터넷 연결을 막는 데 쓰는 "막힌 프록시"를 이 PC의 `127.0.0.1`에서 운영체제가 정해 주는 빈 포트(실행할 때마다 번호가 달라질 수 있어요)에 열어 둬요. 플러그인을 쓰지 않아도 열려요. 이 포트는 연결을 받는 즉시 끊고, 아무 데도 잇지 않으며, 받은 내용을 읽거나 처리하지 않아요. 같은 PC의 다른 프로그램이 접속해도 바로 끊기고, 위의 "들어오는 연결" 통로(토큰이 있어야 받아 줘요)와는 다른 것이에요.

#### 3.2 사용자의 책임

다음은 **사용자의 몫**이에요: 이 PC와 Windows 계정의 보안, 운영체제와 이 소프트웨어의 업데이트, 백신·방화벽, API 키·Admin 키·Claude 계정·구독의 관리와 보호, 데이터 폴더(`settings.json`·`secrets.bin`·`backup` 등)의 접근 제한과 백업, 누구에게 무엇을 입력하고 전송하는지의 판단, 공용·공유 PC에서 쓰지 않는 것, Claude Code 연결을 했다면 앱을 제거하기 전에 연결을 해제하는 것, 그리고 **플러그인·zip을 어디서 받아 무엇에 동의하는지의 판단과, 들어오는 연결 토큰·플러그인에 넣은 비밀 값의 관리**.

#### 3.3 저작권자가 책임지지 않는 것

**보안사고**(예: API 키·토큰·비밀번호·개인정보의 유출, 무단 접근이나 무단 사용, 뜻하지 않은 요금, 악성 프로그램·랜섬웨어 감염, 데이터의 삭제·변조·유출, 계정 정지·제재)가 다음 가운데 어느 것에서 비롯되었든, 관련 법령이 허락하는 가장 넓은 범위에서 **저작권자는 책임을 지지 않아요.**

1. 소프트웨어의 오류나 알려지지 않은 취약점
2. 플러그인, 가져온 캐릭터·플러그인 zip, 다른 사람이 만든 콘텐츠(플러그인이 사용자가 동의한 권한·주소 범위 안에서 한 일을 포함해요)
3. Electron·Chromium·Node.js·Windows 등 구성요소의 취약점
4. 사용자의 설정·환경·부주의(키나 토큰을 남에게 알려 준 것, 클립보드·명령 기록·화면 캡처·백업 파일에 남긴 것, 같은 PC를 여럿이 쓴 것 등)
5. 제3자의 공격이나 악의적 행위
6. Anthropic 등 제3자 서비스의 장애·정책 변경·보안 사고
7. 격리·동의·연결 제한 같은 안전 장치의 한계나 우회

다만 저작권자의 고의 또는 중대한 과실로 생긴 사고와 법령상 배제할 수 없는 책임은 제외해요(2조).

#### 3.4 플러그인과 가져온 파일

설치형 플러그인은 **제3자가 만든 프로그램 코드**예요. 아래는 그 위험과 한계예요.

- **저작권자가 만들거나 검증한 것이 아니에요**(앱에 들어 있는 내장 기능은 제외). 어디서 받은 플러그인인지, 믿을 수 있는지는 사용자가 판단해요. 플러그인·캐릭터에 쓰인 그림·이름·코드의 권리(저작권·상표 등) 문제도 그것을 만든 사람의 몫이에요.
- **동의는 사용자의 책임이에요.** 플러그인은 가져올 때 동의 창이 보여 준 "할 수 있는 일"(말풍선 띄우기, 펫 움직이기, 따로 뜨는 창 열기, 앱 소식 받기, 이 PC의 다른 프로그램이 보내는 신호 받기, Claude Code 세션 열기)과 "접속할 주소" 범위 안에서 동작해요. 주소 뒤의 "(이 PC 안)"·"(내부망)"은 이 PC나 집·회사 내부망의 기기에 닿을 수 있다는 뜻이고, "인터넷의 모든 주소"(`*`)는 공용 인터넷의 어느 주소로든 HTTP로 보낼 수 있다는 뜻이에요. 플러그인이 그리는 화면(말풍선 안·설정 창 안·따로 뜨는 창)과 캐릭터에 보내는 신호도 플러그인이 정해요. 권한이나 주소가 늘어난 업데이트는 다시 묻지만, **동의 창을 읽고 허락할지 정하는 것은 사용자예요.** 동의한 범위 안에서 플러그인이 한 일은 저작권자가 책임지지 않아요. 플러그인 화면에는 비밀번호·키·개인정보를 입력하지 마세요(그 화면은 플러그인이 그린 것이고, 플러그인이 입력한 내용을 읽을 수 있어요).
- **들어오는 연결(내 PC 안의 통로).** 이 권한을 가진 플러그인이 켜져 있으면 앱은 `127.0.0.1`의 한 포트(기본 47823)를 열고, 플러그인마다 다른 **토큰**을 아는 프로그램만 그 플러그인에 신호를 보낼 수 있어요. 토큰을 남에게 알려 주거나, 클립보드(Windows 클립보드 기록 포함)·명령 기록(PowerShell 기록 등)·화면 캡처·메모 파일에 남겨서 생기는 일은 사용자 책임이에요. 같은 PC의 다른 프로그램이 이 통로에 접속을 시도할 수 있다는 한계가 있어요. 이 권한을 가진 플러그인이 모두 꺼지면 통로가 닫혀 그 포트를 다른 프로그램이 쓸 수 있으니, 토큰이 엉뚱한 프로그램에 넘어갈 수 있다는 점도 알아 두세요. 토큰이 샜다고 의심되면 설정 창의 "토큰 재발급"을 쓰세요.
- **세션 열기(`session` 권한).** 이 권한을 가진 플러그인은 사용자가 화면의 버튼을 눌렀을 때 앱이 Claude Code 세션을 열게 할 수 있어요. 앱이 Claude 앱 주소를 열거나, 새 창에서 `claude` 명령을 실행해요. 주소·명령·폴더는 앱이 정하고 플러그인은 세션 id만 넘기며, 그 플러그인이 들어오는 연결로 받은 세션만 열 수 있어요. 그래도 사용자의 PC에서 프로그램이 실행된다는 사실은 같으니, 믿을 수 있는 플러그인에만 이 권한을 허락하세요.
- **비밀 칸.** 플러그인이 받는 비밀 값(키·웹훅 주소 등)은 Windows 계정으로 암호화해 저장하지만, ① 같은 Windows 계정의 다른 프로그램은 읽을 수 있고, ② 그 플러그인이 켜져 있으면 풀린 값이 플러그인에 **그대로 전달돼요**(플러그인은 그 값을 동의받은 주소로 보낼 수 있어요), ③ 비밀 칸이 아닌 일반 설정 칸의 값은 암호화하지 않고 `settings.json`에 그대로 저장돼요. 플러그인에는 그 플러그인만을 위해 따로 만든 키(권한과 사용 한도를 최소로 건 것)만 넣으세요.
- **나가는 연결.** 플러그인은 동의받은 주소로 데이터를 보낼 수 있어요. 무엇을 보낼지는 플러그인이 정하고, ClaudeTool은 그 내용을 검열하거나 보증하지 않아요. 알려진 한계: ① 선언한 이름의 주소가 DNS 설정에 따라 내부망 주소를 가리키면 그곳에 닿을 수 있어요(동의 창은 이름만 보여 줘요). ② 플러그인 화면에 DNS 미리 풀기(`dns-prefetch`)가 있으면 조회하는 이름에 적은 양의 정보를 실어 밖으로 보낼 수 있고, 앱은 이를 막지 못해요(받는 쪽이 DNS 서버를 운영해야 하는 통로라 양은 적어요). ③ "인터넷의 모든 주소"를 허락한 플러그인은 연결 오류의 차이로 이 PC의 DNS에 어떤 이름이 있는지 구별할 수 있어요.
- **격리의 한계.** 설치형 플러그인은 플러그인마다 보이지 않는 창(샌드박스)에서 따로 돌고, 이 PC의 파일·다른 플러그인·앱 화면 내용에 닿지 못하게 만들었어요. 하지만 이 격리는 Electron·Chromium·Windows의 보안 기능에 기대는 **위험을 줄이는 장치일 뿐, 안전을 보증하지 않아요.** 구성요소에 취약점이 있거나 앱의 구현이 완벽하지 않으면(일부는 Electron의 실험 기능에 기대요) 격리가 뚫릴 수 있어요. 이 문서나 앱 어디에 "격리"라는 말이 나와도 안전하다는 뜻이 아니에요.
- **자원과 자동 꺼짐.** 켠 플러그인마다 보이지 않는 창이 하나씩 열려 메모리를 약 70MB쯤 더 써요(측정값이고 PC와 플러그인에 따라 달라요). 응답이 10초 넘게 없으면 그 플러그인의 창만 끝내고 다시 시작하며, 10분 안에 세 번 멈추면 꺼 두지만, **이것은 편의 기능일 뿐 보장이 아니에요.** 응답은 하면서 CPU·메모리·배터리를 많이 쓰는 플러그인은 막지 못할 수 있어요.
- **AI가 만든 플러그인.** "만드는 법" 문서를 AI에게 건네 만든 플러그인·캐릭터는 AI가 틀리거나 위험한 코드를 쓸 수 있어요. 만든 사람이 내용(특히 권한과 접속 주소)을 검토하고 책임져야 하고, 남에게 줄 때도 마찬가지예요.
- **가져온 zip(캐릭터·플러그인).** 가져올 때 형식·파일 종류·크기를 검사하지만(경로 탈출, 압축 폭탄 등), **내용이 안전하다는 것은 보증하지 않아요.**
- **공유 공간(Discussions)에 올라온 플러그인.** 이 저장소의 Discussions에는 누구나 플러그인을 올릴 수 있어요. 올라온 플러그인은 올린 사람이 만들거나 올린 것이고 **저작권자가 검토하거나 보증하지 않아요.** 올린 사람이 적은 이름·권한 설명·SHA-256도 확인되지 않은 값이에요. 올라온 글과 첨부 파일의 권리와 책임은 올린 사람에게 있고 이를 내려받아 설치하는 것과 그 결과는 사용자의 책임이에요(위의 제3자 플러그인과 같아요).
- **믿을 수 있는 곳의 것만** 설치하고, 동의 창에 나온 "할 수 있는 일"과 "접속할 주소"를 읽고, 이상하면 바로 끄고 지우세요. 플러그인을 지우면 그 폴더와 저장한 데이터·비밀 값·토큰·동의 기록이 함께 지워져요.

#### 3.5 이렇게 하시길 권해요

- API 키는 **사용 한도와 최소 권한**을 걸고, 정기적으로 바꾸고, 유출이 의심되면 **바로 폐기**하세요.
- 플러그인의 비밀 칸에는 그 플러그인 전용 키만 넣고, "인터넷의 모든 주소"는 믿을 수 있는 플러그인에만 허락하세요.
- 들어오는 연결 토큰은 남에게 주지 말고, 명령줄에 직접 적거나 클립보드에 오래 두지 마세요. 필요하면 재발급하세요.
- 데이터 폴더를 남과 공유하거나 온라인에 올리지 마세요(키·설정·사용 기록이 들어 있어요).
- 믿을 수 없는 zip·플러그인은 가져오지 마세요.
- 설치 파일은 공개 저장소(`claude-tool-page`)의 릴리스에서만 받으세요. 저작권자가 직접 건네준 것이 아니거나 다른 곳에서 받은 설치 파일은 쓰지 마세요. 설치 파일에는 코드 서명이 없어서 Windows SmartScreen 경고가 뜰 수 있고, 같은 이름으로 다른 곳에서 받은 파일은 위조일 수 있어요.
- Claude Code 연결을 했다면, 앱을 제거하기 전에 사용량 창에서 "연결 해제"를 먼저 누르세요(3.1).
- 사고가 의심되면: (의심 가는 플러그인을 끄고) 앱 종료 → 키 폐기와 재발급 → 계정 비밀번호 변경 → 데이터 폴더의 `logs` 확인 순서로 하세요.

#### 3.6 보안 문제를 알려 주세요

취약점을 발견하면 **공개 이슈에 자세히 쓰지 말고**, 소개 페이지 저장소(`claude-tool-page`)의 **Security 탭 → "Report a vulnerability"(비공개 취약점 보고)** 로 알려 주세요. 보고하는 방법과 범위는 [SECURITY.md](SECURITY.md)에 있어요. 최선을 다해 살펴보지만, 처리 시점과 결과를 약속하지는 않아요.

### 4. 제3자 서비스와 상표

Anthropic의 API·Claude Code·구독 같은 **제3자 서비스**, 그리고 플러그인이 접속하는 서비스(채팅·웹훅·내부망 기기 등)의 약관·요금·사용 한도·중단·계정 제재·응답 오류·보안은 그 서비스 제공자와 사용자 사이의 일이며, 저작권자는 관여하지 않고 책임지지 않아요. 질문하기는 사용자가 이 PC에 로그인해 둔 Claude Code(또는 사용자의 API 키)를 거쳐 Anthropic으로 가서 **사용자의 구독 사용량이나 API 요금을 쓰며**, 그 사용량·한도 초과·계정 제재는 사용자와 Anthropic 사이의 일이에요.

"Claude", "Anthropic"은 Anthropic PBC의 상표예요. ClaudeTool은 개인이 만든 **비공식 프로젝트**이며 Anthropic과 제휴·후원·승인·보증 관계가 없고, Anthropic의 공식 제품도 아니에요. "ClaudeTool"의 "Claude"는 이 소프트웨어가 Claude와 함께 쓰는 도구라는 뜻이고, 이 이름을 쓰는 데 Anthropic의 허락이나 제휴가 있는 것은 아니에요.

### 5. 사용량·비용 표시는 참고용이에요

소프트웨어가 보여 주는 사용량·한도·비용은 추정치이고, 실제 청구·한도와 다를 수 있어요. 요금과 한도의 기준은 항상 서비스 제공자가 알려 주는 값이에요.

### 6. AI가 만든 답과 AI가 만든 결과물

Claude가 만든 답의 정확성·완전성·적합성은 보증하지 않아요. 의료·법률·재정·안전에 관한 중요한 결정에 쓰지 마세요. AI의 도움으로 만든 플러그인·캐릭터·코드도 마찬가지예요. 쓰기 전에 만든 사람이 직접 검토해야 해요(3.4).

### 7. 데이터와 백업

소프트웨어의 오류·업데이트·삭제나 플러그인의 동작으로 설정·캐릭터·플러그인 데이터·사용 기록이 사라지거나 바뀔 수 있어요. 중요한 것은 직접 백업하세요(데이터 폴더를 복사하면 돼요). 다만 `secrets.bin`에 든 키·비밀 값·토큰은 이 Windows 계정에서만 풀려서 복사해도 다른 PC나 계정에서는 쓸 수 없으니, 키는 따로 안전하게 보관하세요. 플러그인을 지우거나 데이터 폴더를 지워서 사라진 데이터는 되돌릴 수 없어요.

### 8. 법령상 권리

이 면책조항은 법령이 정한 소비자의 권리를 없애지 않아요. 법령이 허락하지 않는 범위에서는 이 조항의 해당 부분이 적용되지 않고, 나머지는 그대로 유효해요.

### 9. 변경과 효력

저작권자는 이 문서를 바꿀 수 있고, 새 판은 저장소에 올린 때부터 그 뒤에 받거나 갱신하는 소프트웨어에 적용돼요. 소프트웨어를 설치하거나 쓰면 이 문서에 동의한 것으로 봐요.

---

## English

*A courtesy translation. If it differs from the Korean version, the Korean version prevails.*

### 1. Provided "AS IS" (no warranty)

ClaudeTool (the "Software") is provided free of charge to personal users **"AS IS"**. To the fullest extent permitted by law, the Licensor gives no warranty of any kind, express or implied, including:

- that it is error-free or uninterrupted, or works in every environment (Windows version, display scaling, other programs);
- that it is merchantable, fit for a particular purpose, or does not infringe third-party rights;
- that the information it shows (usage, limits, costs, answers) is accurate or complete;
- that its **safety measures (isolation, consent, connection limits, tokens, encrypted storage) work without gaps or stop every attack or incident**.

### 2. Limitation of liability

To the fullest extent permitted by law, the Licensor is not liable for any **direct, indirect, special or consequential damages** (loss of data or files, damaged settings, lost profits, monetary loss, business interruption, account suspension, unexpected charges, exceeding subscription usage or API limits, device failure, damages caused by problems of third-party services, etc.) arising from the use of, or inability to use, the Software. Because the Software is free, any liability that is found to exist is limited to the amount you paid the Licensor (zero).

This does not exclude damage caused by the Licensor's **intent or gross negligence**, or liability that cannot be excluded by law (such as consumer-protection law).

### 3. Security incident disclaimer

#### 3.1 What the Software does (please know this)

What is stored, read and sent is described in detail in [PRIVACY.md](PRIVACY.md). In short:

- To show usage, it reads the log files that Claude Code leaves on this PC (`.claude\projects`). It reads the files but uses only the model name, time and token counts, and does not store or send the content of questions and answers anywhere.
- It reads and edits the **Claude Code settings file** only when you press "Connect"/"Disconnect" (it shows the change first and backs up the original).
- **When you "Connect Claude Code", this app's status-line (statusLine) command is written into Claude Code's `settings.json`.** After that, each time Claude Code draws its status line, a small script of this app is run with the `node.exe` in the install folder's `resources\node` (if it is missing or fails, the Node.js on your PC is used) and writes only limit information to the data folder (details in Section 4 of [PRIVACY.md](PRIVACY.md)). If you already had a status-line command, it keeps running too.
- **Press "Disconnect" before you uninstall the app.** Otherwise this app's status-line command stays in Claude Code's settings (a leftover command has to be removed from `settings.json` by hand or replaced with the original value, which is in the copies kept in the `backup\` folder of the data folder). If you reinstall in a different location, press "Disconnect" and then connect again (the location of the script changes).
- **When you connect the notification hook (claude-notify),** the setup helper (`bridge\claude-notify-setup.mjs`) writes 6 notification hooks into Claude Code's `settings.json` (it shows a preview first and backs up the original before changing it). The `claude-notify\` folder of the data folder collects the channel token (`token`) and copies of `settings.json` (`backup\`). The folder is narrowed so that only the current user can access it (on a drive that does not support permission settings it may not be narrowed), but **other programs under the same Windows account can read it**, and a backup may contain secrets such as keys written in `env`. The hook sends its news only to this PC's `127.0.0.1`. Before you uninstall the app, remove the hooks with the helper's `--remove` (otherwise the hooks stay in Claude Code's settings and point to a script that no longer exists).
- **API keys, Admin keys, plugin secret-field values and incoming-connection tokens** are encrypted with Windows DPAPI and stored in `secrets.bin`. **Other programs running under the same Windows account, including malware, may be able to obtain the values.** It is not a perfect vault.
- **Questions** are sent **to Anthropic** through the Claude Code that is signed in on this PC (default) or through the Anthropic API (if you choose the API-key method). Do not enter passwords, keys, personal data or confidential information.
- **Installable plugins** and **imported character/plugin zips** may have been made by other people (see 3.4 below). A plugin can connect to the internet at addresses you consented to.
- If a plugin uses "incoming connections", a channel that accepts connections is opened on this PC's `127.0.0.1` (an address reachable only from this PC) while it is on. Other devices cannot reach it, but **other programs running on the same PC** may try to connect to it (a per-plugin token is required for it to accept).
- Separately from this, **each time the app starts** it opens a "blocked proxy", which is used to cut off the internet connections of installable plugin windows, on a free port chosen by the operating system on this PC's `127.0.0.1` (the number can differ from run to run). It is opened even if you use no plugin. It drops every connection the moment it is received, connects to nowhere and does not read or process any data it receives. Another program on the same PC that connects to it is cut off at once, and it is not the "incoming connections" channel above (which accepts only requests that carry the token).

#### 3.2 Your responsibility

The following are **your responsibility**: security of your PC and Windows account, updates of the operating system and this Software, antivirus and firewall, management and protection of your API/Admin keys, Claude account and subscription, access control and backup of the data folder (`settings.json`, `secrets.bin`, `backup`, etc.), what you type and send and to whom, not using the Software on shared PCs, disconnecting Claude Code before you uninstall the app if you connected it, and **deciding where you get plugins/zips and what you consent to, and managing incoming-connection tokens and any secret values you put into plugins**.

#### 3.3 What the Licensor is not responsible for

To the fullest extent permitted by law, the Licensor is not responsible for any **security incident** (leak of keys, tokens, passwords or personal data; unauthorized access or use; unexpected charges; malware or ransomware; deletion, tampering or leakage of data; account suspension or sanctions) regardless of whether it arises from:

1. errors or unknown vulnerabilities in the Software;
2. plugins, imported character/plugin zips or other people's content (including whatever a plugin does within the permissions and addresses you consented to);
3. vulnerabilities in components such as Electron, Chromium, Node.js or Windows;
4. your settings, environment or carelessness (giving keys or tokens to others, leaving them in the clipboard, command history, screenshots or backup files, sharing a PC, etc.);
5. attacks or malicious acts by third parties;
6. outages, policy changes or security incidents of third-party services such as Anthropic;
7. limits or bypasses of safety measures such as isolation, consent and connection limits.

Incidents caused by the Licensor's intent or gross negligence, and liability that cannot be excluded by law, are not excluded (Section 2).

#### 3.4 Plugins and imported files

An installable plugin is **program code made by a third party**. The risks and limits are as follows.

- **It is not made or verified by the Licensor** (built-in features excluded). Where a plugin comes from and whether you trust it is for you to judge. Rights issues (copyright, trademarks, etc.) in the images, names and code used in a plugin or character are also the responsibility of whoever made it.
- **Consent is your responsibility.** A plugin runs within the "what it can do" (showing speech bubbles, moving the pet, opening separate windows, receiving app events, receiving signals sent by other programs on this PC, opening Claude Code sessions) and "addresses it can connect to" shown in the consent window when you import it. "(this PC)" or "(internal network)" after an address means it can reach this PC or devices on your home/office network; "any address on the internet" (`*`) means it can send HTTP requests to any public internet address. The screens a plugin draws (inside a bubble, inside the settings window, separate windows) and the signals it sends to a character are also decided by the plugin. An update that adds permissions or addresses asks again, but **reading the consent window and deciding whether to allow is up to you.** The Licensor is not responsible for what a plugin does within the range you consented to. Do not type passwords, keys or personal data into plugin screens (the screen is drawn by the plugin, and the plugin can read what you type).
- **Incoming connections (a channel inside your PC).** While a plugin with this permission is on, the app opens one port on `127.0.0.1` (default 47823), and only a program that knows the plugin's own **token** can send signals to that plugin. What happens when you give the token to someone or leave it in the clipboard (including Windows clipboard history), command history (such as PowerShell history), screenshots or note files is your responsibility. A limit: other programs on the same PC can try to connect to this channel. When every plugin with this permission is off, the channel closes and another program may take that port, so be aware that a token may end up with the wrong program. If you suspect the token has leaked, use "reissue token" in the settings window.
- **Opening sessions (`session` permission).** A plugin with this permission can make the app open a Claude Code session when you press a button on its screen. The app opens a Claude app address, or runs the `claude` command in a new window. The app decides the address, command and folder; the plugin passes only a session id, and can open only sessions it received through incoming connections. Still, a program runs on your PC, so grant this permission only to plugins you trust.
- **Secret fields.** Secret values a plugin receives (keys, webhook addresses, etc.) are stored encrypted with your Windows account, but (1) other programs under the same Windows account can read them, (2) while the plugin is on, the decrypted value is **passed to the plugin as is** (the plugin can send it to addresses you consented to), and (3) values of ordinary settings fields (not secret fields) are stored unencrypted in `settings.json`. Put only a key made just for that plugin, with the minimum permissions and usage limits, into a plugin.
- **Outgoing connections.** A plugin can send data to the addresses you consented to. What it sends is up to the plugin, and ClaudeTool does not censor or vouch for it. Known limits: (1) if a declared host name points to an internal-network address through DNS settings, it can reach it (the consent window shows only the name); (2) if a plugin screen contains a DNS prefetch (`dns-prefetch`), a small amount of information can be carried out in the names it looks up, and the app cannot block this (the receiver has to run a DNS server, so the amount is small); (3) a plugin allowed "any address on the internet" can tell, from differences in connection errors, which names exist in this PC's DNS.
- **Limits of isolation.** Each installable plugin runs separately in its own invisible window (sandbox) and is built so that it cannot reach files on this PC, other plugins or the content of app screens. But this isolation relies on the security features of Electron, Chromium and Windows and is **only a way to reduce risk; it does not guarantee safety.** If a component has a vulnerability or the app's implementation is imperfect (some parts rely on experimental Electron features), the isolation can be broken. Wherever the word "isolation" appears in this document or the app, it does not mean "safe".
- **Resources and automatic shut-off.** Each plugin that is on opens one invisible window and uses roughly 70 MB more memory (a measured value that varies by PC and plugin). If a plugin does not respond for more than 10 seconds only its window is ended and restarted, and if it stops three times within 10 minutes it is turned off, but **this is a convenience, not a guarantee.** A plugin that keeps responding while using a lot of CPU, memory or battery may not be stopped.
- **Plugins made with AI.** A plugin or character made by giving the "how to make" document to an AI may contain wrong or dangerous code. The person who made it must review it (especially the permissions and addresses) and is responsible, also when giving it to others.
- **Imported zips (characters/plugins).** Format, file types and sizes are checked on import (path escape, zip bombs, etc.), but **the content is not guaranteed to be safe.**
- **Plugins posted in the sharing space (Discussions).** Anyone can post a plugin in this repository's Discussions. A posted plugin was made or uploaded by the person who posted it, and **the Licensor does not review or vouch for it.** The name, permission description and SHA-256 written by the poster are also unverified values. The rights in and responsibility for posts and attachments belong to the person who posted them, and downloading and installing them, and the result, are your responsibility (the same as for the third-party plugins above).
- **Install only from sources you trust**, read the "what it can do" and "addresses it can connect to" lists in the consent window, and turn off and delete anything suspicious. Deleting a plugin also deletes its folder, saved data, secret values, token and consent record.

#### 3.5 Recommendations

- Set **usage limits and least privilege** on API keys, rotate them regularly, and **revoke immediately** if leakage is suspected.
- Put only a key made for that plugin into a plugin's secret field, and allow "any address on the internet" only for plugins you trust.
- Do not give incoming-connection tokens to others, and do not type them directly on the command line or leave them in the clipboard for long. Reissue if needed.
- Do not share or upload the data folder (it contains keys, settings and usage history).
- Do not import untrusted zips or plugins.
- Get the installer only from the Releases of the public repository (`claude-tool-page`). Do not use any installer that the Licensor did not hand to you directly or that you got from anywhere else. The installer is not code-signed, so Windows SmartScreen may show a warning, and a file with the same name from anywhere else may be forged.
- If you connected Claude Code, press "Disconnect" in the usage window before you uninstall the app (3.1).
- If you suspect an incident: (turn off the suspicious plugin and) quit the app → revoke and reissue keys → change account passwords → check the `logs` folder in the data folder.

#### 3.6 Reporting a security problem

Do not post vulnerability details in a public issue. Use the **Security tab → "Report a vulnerability"** (private vulnerability reporting) of the introduction-page repository (`claude-tool-page`). How to report and what is in scope is described in [SECURITY.md](SECURITY.md). The Licensor will make a best effort to look into reports but does not promise a response time or outcome.

### 4. Third-party services and trademarks

The terms, prices, usage limits, outages, account sanctions, response errors and security of **third-party services** such as Anthropic's API, Claude Code and subscriptions, and of services a plugin connects to (chat services, webhooks, devices on your internal network, etc.), are matters between you and the service provider; the Licensor is not involved and not responsible. Questions go to Anthropic through the Claude Code signed in on this PC (or your own API key) and **use your subscription usage or API charges**; that usage, exceeding limits and account sanctions are matters between you and Anthropic.

"Claude" and "Anthropic" are trademarks of Anthropic PBC. ClaudeTool is an **unofficial project** made by an individual; it is not affiliated with, sponsored by, approved by or endorsed by Anthropic and is not an official Anthropic product. The "Claude" in "ClaudeTool" means that this is a tool used together with Claude; the name is not used with Anthropic's permission or in cooperation with Anthropic.

### 5. Usage and cost figures are for reference only

They are estimates and may differ from actual billing or limits. The service provider's figures are always authoritative.

### 6. AI-generated answers and AI-made results

The accuracy, completeness and suitability of Claude's answers are not guaranteed. Do not rely on them for important medical, legal, financial or safety decisions. The same applies to plugins, characters and code made with the help of AI: the person who made them must review them before use (3.4).

### 7. Data and backups

Settings, characters, plugin data and usage history may be lost or changed due to bugs, updates, deletion or the behavior of a plugin. Back up what matters (copying the data folder is enough). However, the keys, secret values and tokens in `secrets.bin` can be decrypted only under this Windows account, so copying them to another PC or account will not work; keep your keys safe somewhere else. Data lost by deleting a plugin or the data folder cannot be restored.

### 8. Statutory rights

This disclaimer does not remove consumer rights granted by law. To the extent a part is not permitted by law it does not apply, and the rest remains in force.

### 9. Changes and effect

The Licensor may change this document; a new version applies from the time it is posted to Software received or updated after that time. Installing or using the Software means you accept this document.
