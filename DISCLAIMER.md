# 면책조항과 보안사고 면책 (Disclaimer)

ClaudeTool 개인 사용 라이선스 v1.0([LICENSE](LICENSE))의 일부예요. 소프트웨어를 쓰기 전에 읽어 주세요. 한국어본과 영어본이 함께 있고, 뜻이 다르면 한국어본이 우선해요.

*This document is part of the ClaudeTool Personal Use License v1.0 ([LICENSE](LICENSE)). A Korean and an English version are provided; if they differ, the Korean version prevails.*

---

## 한국어

### 1. 있는 그대로 제공해요(무보증)

ClaudeTool(이하 "소프트웨어")은 **개인 사용자에게 무료로, 있는 그대로("AS IS")** 제공해요. 저작권자는 관련 법령이 허락하는 가장 넓은 범위에서 다음을 포함한 모든 명시적·묵시적 보증을 하지 않아요.

- 오류가 없다는 것, 끊기지 않고 동작한다는 것, 모든 환경(Windows 버전·화면 배율·다른 프로그램)에서 동작한다는 것
- 상품성, 특정 목적에 대한 적합성, 제3자의 권리를 침해하지 않는다는 것
- 이 소프트웨어가 보여 주는 정보(사용량·한도·비용·답변)가 정확하거나 완전하다는 것

### 2. 책임의 제한

관련 법령이 허락하는 가장 넓은 범위에서, 저작권자는 소프트웨어를 쓰거나 쓰지 못해서 생긴 **직접·간접·특별·결과적 손해**(데이터 손실, 이익 손실, 업무 중단, 계정 정지, 뜻하지 않은 요금, 기기 고장 등)에 대해 책임을 지지 않아요. 소프트웨어는 무료이므로, 책임이 인정되더라도 그 한도는 사용자가 저작권자에게 낸 금액(0원)으로 해요.

다만 **저작권자의 고의 또는 중대한 과실로 생긴 손해**와 **법령상 배제할 수 없는 책임**(소비자 보호 관련 법령 등)은 이 조항에서 제외해요.

### 3. 보안사고 면책

#### 3.1 이 소프트웨어가 하는 일(알아 두세요)

README의 "개인정보와 안전"에 자세히 적혀 있고, 핵심은 이래요.

- **사용량을 보여 주려고** Claude Code가 이 PC에 남긴 기록 파일(`.claude\projects`)을 읽어요. 모델 이름·시각·토큰 수만 뽑고, 질문과 답의 내용은 가져오지 않아요.
- **Claude Code 설정 파일**은 사용자가 "Claude Code 연결"·"연결 해제"를 누를 때만 읽고 고쳐요(고치기 전에 보여 주고, 원래 파일은 백업해요).
- **API 키·Admin 키**는 Windows의 보호 기능(DPAPI)으로 암호화해 `secrets.bin`에 저장해요. 이 방식은 **같은 Windows 계정에서 실행되는 다른 프로그램(악성 프로그램 포함)이 키를 알아낼 수 있어요.** 완전한 금고가 아니에요.
- **질문**은 Anthropic API 또는 이 PC의 Claude Code를 거쳐 **Anthropic으로 전송돼요.** 비밀번호·키·개인정보·회사 기밀은 입력하지 마세요.
- **설치형 플러그인**과 **가져온 캐릭터·플러그인 zip**은 저작권자가 아닌 사람이 만든 것일 수 있어요(아래 3.4).
- 로컬 주소로 연결을 받는 기능 같은 **네트워크 기능**이 있다면, 켜는 순간부터 이 PC의 다른 프로그램(방화벽 설정에 따라 다른 기기)이 접근할 수 있는 문이 열려요.

#### 3.2 사용자의 책임

다음은 **사용자의 몫**이에요: 이 PC와 Windows 계정의 보안, 운영체제와 이 소프트웨어의 업데이트, 백신·방화벽, API 키·Admin 키·Claude 계정·구독의 관리와 보호, 데이터 폴더(`settings.json`·`secrets.bin`·`backup` 등)의 접근 제한과 백업, 누구에게 무엇을 입력하고 전송하는지의 판단, 공용·공유 PC에서 쓰지 않는 것.

#### 3.3 저작권자가 책임지지 않는 것

**보안사고**(예: API 키·토큰·비밀번호·개인정보의 유출, 무단 접근이나 무단 사용, 뜻하지 않은 요금, 악성 프로그램·랜섬웨어 감염, 데이터의 삭제·변조·유출, 계정 정지·제재)가 다음 가운데 어느 것에서 비롯되었든, 관련 법령이 허락하는 가장 넓은 범위에서 **저작권자는 책임을 지지 않아요.**

1. 소프트웨어의 오류나 알려지지 않은 취약점
2. 플러그인, 가져온 캐릭터·플러그인 zip, 다른 사람이 만든 콘텐츠
3. Electron·Chromium·Node.js·Windows 등 구성요소의 취약점
4. 사용자의 설정·환경·부주의(키를 남에게 알려 준 것, 같은 PC를 여럿이 쓴 것 등)
5. 제3자의 공격이나 악의적 행위
6. Anthropic 등 제3자 서비스의 장애·정책 변경·보안 사고

다만 저작권자의 고의 또는 중대한 과실로 생긴 사고와 법령상 배제할 수 없는 책임은 제외해요(2조).

#### 3.4 플러그인과 가져온 파일

- 설치형 플러그인은 저작권자가 만들거나 검증한 것이 아니에요(앱에 들어 있는 내장 기능은 제외).
- 플러그인을 격리하고, 하는 일에 동의를 받고, 네트워크를 막는 장치는 **위험을 줄이는 장치일 뿐 안전을 보증하지 않아요.**
- 캐릭터·플러그인 zip은 가져올 때 형식과 파일 종류를 검사하지만, **내용이 안전하다는 것은 보증하지 않아요.**
- **믿을 수 있는 곳의 것만** 설치하고, 동의 창에 나온 "할 수 있는 일"을 읽고, 이상하면 바로 끄고 지우세요.

#### 3.5 이렇게 하시길 권해요

- API 키는 **사용 한도와 최소 권한**을 걸고, 정기적으로 바꾸고, 유출이 의심되면 **바로 폐기**하세요.
- 데이터 폴더를 남과 공유하거나 온라인에 올리지 마세요(키·사용 기록이 들어 있어요).
- 믿을 수 없는 zip·플러그인은 가져오지 마세요.
- 사고가 의심되면: 앱 종료 → 키 폐기와 재발급 → 계정 비밀번호 변경 → 데이터 폴더의 `logs` 확인 순서로 하세요.

#### 3.6 보안 문제를 알려 주세요

취약점을 발견하면 **공개 이슈에 자세히 쓰지 말고**, 소개 페이지 저장소(`claude-tool-page`)의 **Security 탭 → "Report a vulnerability"(비공개 취약점 보고)** 로 알려 주세요. 최선을 다해 살펴보지만, 처리 시점과 결과를 약속하지는 않아요.

### 4. 제3자 서비스

Anthropic의 API·Claude Code·구독 같은 **제3자 서비스**의 약관·요금·사용 한도·중단·계정 제재·응답 오류는 그 서비스 제공자와 사용자 사이의 일이며, 저작권자는 관여하지 않고 책임지지 않아요. "Claude", "Anthropic"은 Anthropic PBC의 상표이고, 이 프로젝트는 그와 제휴·후원·승인 관계가 없는 **개인 프로젝트**예요.

### 5. 사용량·비용 표시는 참고용이에요

소프트웨어가 보여 주는 사용량·한도·비용은 추정치이고, 실제 청구·한도와 다를 수 있어요. 요금과 한도의 기준은 항상 서비스 제공자가 알려 주는 값이에요.

### 6. AI가 만든 답

Claude가 만든 답의 정확성·완전성·적합성은 보증하지 않아요. 의료·법률·재정·안전에 관한 중요한 결정에 쓰지 마세요.

### 7. 데이터와 백업

소프트웨어의 오류·업데이트·삭제로 설정·캐릭터·사용 기록이 사라질 수 있어요. 중요한 것은 직접 백업하세요.

### 8. 법령상 권리

이 면책조항은 법령이 정한 소비자의 권리를 없애지 않아요. 법령이 허락하지 않는 범위에서는 이 조항의 해당 부분이 적용되지 않고, 나머지는 그대로 유효해요.

### 9. 변경과 효력

저작권자는 이 문서를 바꿀 수 있고, 새 판은 저장소에 올린 때부터 그 뒤에 받거나 갱신하는 소프트웨어에 적용돼요. 소프트웨어를 설치하거나 쓰면 이 문서에 동의한 것으로 봐요.

---

## English

*A courtesy translation. If it differs from the Korean version, the Korean version prevails.*

### 1. Provided "AS IS" (no warranty)

ClaudeTool (the "Software") is provided free of charge to personal users **"AS IS"**. To the fullest extent permitted by law, the Licensor gives no warranty of any kind, express or implied, including that it is error-free or uninterrupted, works in every environment, is merchantable or fit for a particular purpose, does not infringe third-party rights, or that the information it shows (usage, limits, costs, answers) is accurate or complete.

### 2. Limitation of liability

To the fullest extent permitted by law, the Licensor is not liable for any **direct, indirect, special or consequential damages** (data loss, lost profits, business interruption, account suspension, unexpected charges, device failure, etc.) arising from the use of, or inability to use, the Software. Because the Software is free, any liability that is found to exist is limited to the amount you paid the Licensor (zero). This does not exclude damage caused by the Licensor's **intent or gross negligence**, or liability that cannot be excluded by law (such as consumer-protection law).

### 3. Security incident disclaimer

**3.1 What the Software does.** It reads the Claude Code log files on this PC (`.claude\projects`) only to compute usage (model name, time, token counts — not the content of questions and answers); it edits the Claude Code settings file only when you press "Connect"/"Disconnect" (with a backup); it stores API/Admin keys encrypted with Windows DPAPI in `secrets.bin` — **other programs running under the same Windows account, including malware, may be able to obtain the keys**; questions are sent **to Anthropic** through the Anthropic API or your Claude Code — do not enter passwords, keys, personal data or confidential information; plugins and imported zips may have been made by other people; any network feature opens a door that other programs (and, depending on your firewall, other devices) may reach once turned on.

**3.2 Your responsibility.** Security of your PC and Windows account, updates, antivirus and firewall, management and protection of your API/Admin keys, Claude account and subscription, access control and backup of the data folder, what you type and send, and not using the Software on shared PCs.

**3.3 What the Licensor is not responsible for.** To the fullest extent permitted by law, the Licensor is not responsible for any security incident (leak of keys, tokens, passwords or personal data; unauthorized access or use; unexpected charges; malware or ransomware; deletion, tampering or leakage of data; account suspension) regardless of whether it arises from (1) errors or unknown vulnerabilities in the Software, (2) plugins, imported zips or other people's content, (3) vulnerabilities in components such as Electron, Chromium, Node.js or Windows, (4) your settings, environment or carelessness, (5) attacks by third parties, or (6) outages, policy changes or security incidents of third-party services such as Anthropic. Incidents caused by the Licensor's intent or gross negligence, and liability that cannot be excluded by law, are not excluded.

**3.4 Plugins and imported files.** Installable plugins are not made or verified by the Licensor (built-in features excluded). Isolation, permission consent and network blocking only reduce risk; they do not guarantee safety. Imported zips are checked for format and file types, not for safety of content. Install only from sources you trust, read the "what it can do" list in the consent window, and turn off and delete anything suspicious.

**3.5 Recommendations.** Set usage limits and least privilege on API keys, rotate them, and revoke immediately if leakage is suspected. Do not share or upload the data folder. Do not import untrusted zips or plugins. If you suspect an incident: quit the app → revoke and reissue keys → change account passwords → check the `logs` folder.

**3.6 Reporting a security problem.** Do not post vulnerability details in a public issue. Use the **Security tab → "Report a vulnerability"** (private vulnerability reporting) of the introduction-page repository (`claude-tool-page`). The Licensor will do his best but does not promise a response time or outcome.

### 4. Third-party services

Terms, prices, usage limits, outages, account sanctions and response errors of third-party services such as Anthropic's API, Claude Code and subscriptions are matters between you and the service provider; the Licensor is not involved and not responsible. "Claude" and "Anthropic" are trademarks of Anthropic PBC; this is a personal project not affiliated with, sponsored by or approved by Anthropic.

### 5. Usage and cost figures are for reference only

They are estimates and may differ from actual billing or limits. The service provider's figures are always authoritative.

### 6. AI-generated answers

The accuracy, completeness and suitability of Claude's answers are not guaranteed. Do not rely on them for important medical, legal, financial or safety decisions.

### 7. Data and backups

Settings, characters and usage history may be lost due to bugs, updates or deletion. Back up what matters.

### 8. Statutory rights

This disclaimer does not remove consumer rights granted by law. To the extent a part is not permitted by law it does not apply, and the rest remains in force.

### 9. Changes and effect

The Licensor may change this document; a new version applies from the time it is posted to Software received or updated after that time. Installing or using the Software means you accept this document.
