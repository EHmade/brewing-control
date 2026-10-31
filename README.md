[한국어](#한국어) · [English](#english)

<a id="한국어"></a>

# Coffee Brewing Control

**원하는 추출을 향해.** Coffee Brewing Control은 브라우저에서 측정·추출 기록·차트 해석·조정 가이드를 연결합니다. 개인 반복 테스트와 바리스타 실습에 사용할 수 있고 수강생 기록·강사 피드백을 지원합니다.

맛과 추출 의도를 바탕으로 무엇을 바꿀지 결정하세요. 타겟은 변경 가능한 참고 범위이며 맛이나 품질의 판정이 아닙니다. 노트는 선택 사항이고 앱이 맛을 자동 분석하지 않습니다.

[앱 열기](https://ehmade.github.io/brewing-control/) · [변경 이력](CHANGELOG.md) · [개인정보 및 데이터 처리](PRIVACY.md)

현재 버전: **v4.6.1 / schema v7**.

## 시작하기

측정기 연결은 기기별 브라우저·운영체제 지원에 따라 다릅니다. R2는 Windows Chromium·Android Chrome에서 통합 시험했고, HM Digital은 아래의 Web Serial·페어링 안내를 따릅니다. Safari와 일반적인 iOS 브라우저는 이 직접 연결 경로를 지원하지 않습니다. 측정기를 연결하지 않아도 TDS 수동 입력으로 사용할 수 있습니다.

1. 개인 반복 테스트는 **Quick**, 학생 실습 기록은 **Class**를 선택하세요. 직접 입력에는 설치나 측정기 연결이 필요하지 않습니다.
2. 원두량, 실제로 측정한 TDS, 물양/추출액 중 적어도 하나를 입력하세요. 다른 질량은 선택한 액체 보유 가정으로 추정할 수 있습니다. 지원 측정기 없이 앱 자체가 TDS를 측정하지는 않습니다.
3. 선택한 타겟에 상대적인 결과·차트를 보세요. 커피와 목적에 맞게 Settings에서 타겟을 바꾸고, 회차를 명시적으로 저장한 다음 조정에 따른 변화를 살펴보세요.
4. 기록은 중앙 계정이 아닌 이 브라우저에 있습니다. 보존·이동하려면 JSON 백업을 내보내세요.

측정기 접근과 이미지 복사·공유는 브라우저·운영체제·보안 연결 규칙에 의존합니다. 수동 계산에는 연결된 굴절계가 필요하지 않습니다.

## 기능과 사용 흐름

- **Quick:** 현재 입력과 저장 회차, 수정, 회차별 노트, 누락 질량 추정, 변화 비교, 목표점, PNG 출력을 제공합니다. 세션 이름·공통 노트와 회차별 노트는 별개입니다.
- **Class:** 반·수강생·재사용 실습과 학생별 회차·강사 피드백을 관리합니다. 접힌 헤더는 현재 반·인원·실습을 요약합니다. 펼친 반/수강생/실습 탭에서 관리하고 실습 탭에서 선택·생성합니다. 값 입력만으로 새 회차가 저장되지 않으며 저장 버튼으로 기록합니다.
- **Chart:** 변경 가능한 TDS/EY 범위·타겟·비율선·필터·회차 경로를 제공합니다. Quick은 현재 입력과 저장 회차를, Class는 선택한 저장 기록을 보여주며 빈 Class 차트도 열 수 있습니다.
- **측정기:** 지원 장치의 TDS를 현재 Quick/Class 입력에 넣습니다. 기존의 명시적 기록 저장 흐름을 유지합니다.
- **입력 검토:** 계산 불가능과 계산 가능하지만 특이한 데이터를 구분합니다. 특이한 기록도 원래 값·분류를 유지하며 사용자가 확인 표시할 수 있습니다.
- **프로필:** 타겟 이름·EY/TDS 범위는 Target Profile, 축·눈금·비율선은 Chart View Preset으로 저장합니다. 액체 보유계수는 별도 계산 설정입니다.
- **로컬 저장:** 전체 JSON 백업·복원을 제공합니다. 핵심 계산·기록·차트·측정은 index.html에서 프레임워크·외부 런타임 없이 실행합니다. 공식 호스팅 진입점만 선택적 Cloudflare 분석 스크립트를 요청하며 대표 이미지·문서는 별도 정적 자료입니다.

## 언어

처음에는 한국어를 표시합니다. **Settings → 언어 선택 · Languages**에서 한국어/English를 직접 선택합니다. 표시 언어는 이 브라우저에 별도 저장하며 추출 백업에는 넣지 않습니다. 백업 복원 후에도 선택을 유지하고 전체 초기화 시 한국어로 돌아갑니다. 다른 탭의 언어는 갑자기 바뀌지 않습니다.

사용자가 입력한 이름·노트·강사 피드백은 자동 번역하지 않습니다. 원래의 기본 반/실습과 새 반에서 자동 생성된 기본 실습은 표시 언어에 맞춰 보여주되 원본 저장 이름은 유지합니다. 이름이 비어 있어 앱이 보정한 반·실습·수강생·Target Profile·Chart Preset 이름과 이관 과정에서 만든 이름도 출처 정보가 있을 때만 번역합니다. 사용자가 직접 지정한 이름은 기본 이름과 같은 글자여도 그대로 표시하며, 출처를 알 수 없는 과거 이름은 추측해 바꾸지 않습니다. 이름 출처는 백업에 보존되지만 구버전 앱에서 다시 저장하면 이 부가 정보가 없어질 수 있습니다. 이름을 지정하지 않은 타겟은 회색 안내 및 화면 기본 이름을 언어에 맞춰 표시합니다. 과거 백업에 명시적으로 저장된 타겟 이름은 보존하며 이름을 지우고 적용하거나 기본 타겟을 불러오면 자동 표시 이름을 사용합니다.

언어 전환은 입력·노트 초안·차트 선택·장치 연결을 초기화하지 않습니다. About·변경 이력·개인정보·저작권 안내도 선택한 언어로 표시합니다. About에서 개인정보·전체 저작권 안내를 앱 내부로 열고 상단 이전으로 또는 하단 닫기로 돌아갑니다. PNG는 생성 시작 시점의 언어와 데이터를 사용합니다.

## 기본 참고 프로필과 계산

**Classic Filter**는 공개된 Specialty Coffee Association 자료를 참고한 **EY 18–22%, TDS 1.15–1.35%**로 시작합니다. 출발 참고값이며 보편적 관능 품질 기준·물리 한계가 아닙니다. 타겟·축·비율·액체 보유 가정은 변경할 수 있습니다.

추출액을 비우면 물양·원두량·TDS·계수로 추정하고, 물양을 비우면 추출액·원두량·TDS로 물양과 비율을 역산합니다. 둘 다 입력하면 둘 다 직접값을 사용하며 둘 다 없으면 추정하지 않습니다. 기본 계수 **2.1**은 계산 설정에서 별도 변경합니다. 질량 단위는 g, TDS 입력 단위는 %입니다.

```text
Beverage = (Brew water − Liquid retention × Dose) / (1 − TDS/100)
Brew water = Beverage × (1 − TDS/100) + Liquid retention × Dose
```

추정 물양·비율은 추정으로 표시하며 추출 중단 시 드리퍼에 남은 여분의 액체를 복원하지 않습니다. 기록·차트 상세는 계산 출처·사용 계수를 표시합니다. 결과는 사용자가 제공한 측정값·가정에 의존합니다.

Quick/Class 저장 기록은 사용 계수를 보존하고 수정 시에도 그 계수를 사용합니다. 현재 전역 계수는 새 LIVE·신규 저장·비율 참고선에 적용하며 기존 자동 추정 결과를 바꾸지 않습니다. 분류·피드백은 현재 타겟을 따릅니다. 추출액 직접 입력 EY에는 계수가 쓰이지 않지만 물양/비율 역산에는 쓰입니다. 추정값이 직접 측정값으로 오인되지 않도록 빈 원시 질량은 저장·백업에도 빈값으로 유지합니다.

schema v5 이전 기록에는 이관 당시 데이터셋 계수를 부여해 직전 표시 결과를 보존합니다. 기록별 원래의 알 수 없는 과거 계수를 복원한 것은 아닙니다.

## 입력 유효성과 확인 표시

계산 결과는 양수 원두량·물양·추출액, 유한한 파생값과 **0 < TDS < 100%**를 요구합니다. TDS 옆에 유효 범위를 표시합니다. 범위 밖 값은 칸에 남을 수 있지만 신규 저장을 막고 EY·용해 고형분·분류·방향 피드백·차트 점을 만들지 않습니다. 원두량/물양만으로 독립 계산 가능한 비율은 표시할 수 있습니다.

계산 가능한 기록에 대해 질량 관계·극단적 결과를 별도로 검토합니다. 특이한 값은 원래 값·타겟 분류·피드백을 유지하며 입력 확인 경고를 표시합니다. 저장 후 의도한 값임을 확인하면 확인됨으로 표시합니다. 원두량·물양·추출액·TDS·입력 모드·보존 계수를 바꾸면 확인을 해제하고 Quick 노트·강사 피드백 변경은 유지합니다. 확인 여부만 저장하고 검토 결과·사유는 매번 계산합니다.

## 저장 회차 수정

Quick은 기존 폼으로 수정하며 ID·순서·계수를 유지합니다. 저장/취소하면 편집 전 LIVE로 돌아갑니다. 물양을 비워 역산할 수 있고 저장 계수·직접값을 유지합니다. 미저장 수정은 확정 기록이 아니며 새로고침하면 보존된 LIVE로 돌아갑니다.

회차 노트는 폼과 별도로 카드에서 수정합니다. 버튼 또는 Ctrl/⌘+Enter로 저장하고 버튼 또는 Esc로 취소합니다. 같은 맥락 갱신에 초안은 남지만 새로고침으로 확정 저장되지는 않습니다. 저장 노트는 툴팁·상세·백업에 포함되고 세션 이름/공통 노트와 별개입니다. 개별 삭제는 확인을 요구합니다. Class 수정은 차트 필터를 보존하고 강사 피드백 초안은 같은 맥락 재렌더링에 남으며 저장·취소·맥락 변경 시 종료합니다.

## 화면 표시와 차트 도구

기본 **분리 모드**에서는 Quick/Class 입력과 해당 차트를 오가며 차트에서 입력으로 돌아갈 수 있습니다. **통합 모드**는 독립 스크롤되는 입력과 차트를 나란히 표시합니다. 비율은 35:65·40:60(기본)·45:55입니다. 새 선택에는 뷰포트 1280 CSS px·작업 폭 1200px 이상이 필요합니다. 창을 줄여도 저장 선호를 덮지 않고 가로 스크롤·좁은 화면 경고·명시적 분리 전환을 제공합니다. Settings에서 나갈 때 선택 모드가 적용됩니다.

**입력 영역 크기**의 기본/작게는 양쪽 모드에서 사용할 수 있습니다. 작게는 1024 CSS px 이상·hover 가능·정밀 포인터 환경에만 적용합니다. 터치/좁은 화면은 기본으로 표시하고 저장 선호를 지우지 않은 채 선택을 비활성화합니다. 헤더·차트는 줄이지 않습니다. 구버전 백업은 분리/40:60/기본으로 시작하며 구버전 앱이 새 선호를 버릴 수 있습니다.

**차트 크기**의 한눈에 보기(기본)는 가독성 하한 안에서 가용 높이를 활용합니다. 낮은 화면·펼친 조작은 스크롤이 필요할 수 있습니다. 크게 보기는 기존 최대 840px 차트 영역의 가용 너비를 활용하고 세로 스크롤을 허용합니다. 좁은 화면에서는 너비에 맞춰 표시하고 크기 선택은 비활성화합니다. 넓은 화면으로 돌아오면 저장된 선택을 다시 사용합니다. 가로 화면처럼 폭이 충분하면 터치 기기에서도 선택할 수 있습니다. 이 설정은 양쪽 모드에서 저장·백업하며 전체 초기화는 한눈에 보기로 돌아갑니다.

차트 도구는 가이드·목표점·수강생/회차 선택·이미지 복사·PNG·공유·차트/타겟 설정 이동을 묶습니다. 바로가기는 설정 위치로 이동하되 자동으로 펼치지 않습니다. 접으면 버튼은 숨기고 요약·범위 밖 경고는 남깁니다. 차트 도구·Class 관리는 헤더 글씨/빈 공간으로 열고 닫으며 박스 없는 +/-를 사용합니다. 다른 버튼은 자신의 동작을 유지하고 기본 키보드 조작을 지원합니다. 출력 기하 구성은 화면 크기 선택과 독립적이며 툴팁·좌표 미리보기를 제외합니다.

## 측정기 지원

Settings에서 Device Profile을 선택하면 측정 컨트롤이 표시됩니다.

- **HM Digital BTR-1000 / RCM-1000BT:** Web Serial·Bluetooth Classic SPP를 사용합니다. Windows 및 지원되는 Android Chrome 경로에서 사용하며 브라우저/OS의 직렬 접근·페어링 지원을 확인해야 합니다.
- **DiFluid R2:** Web Bluetooth(BLE)입니다. DFT-R102 펌웨어 V219, Windows Chromium·Android Chrome으로 통합 검증했습니다. 브라우저/OS 지원에 의존합니다.

헤더는 연결 상태, Quick/Class는 측정 버튼을 제공합니다. 완료값은 일반 TDS 입력 경로를 거치며 기록을 자동 저장하지 않습니다. 대기·실패·불완전 측정은 기존 TDS를 보존합니다.

### 연결과 권한

**HM Digital:** 전원을 켜고 Windows 목록에 없으면 설정 → Bluetooth 및 장치에서 **BTR1000(Coffee)_xxxx**를 먼저 페어링한 뒤 연결 테스트를 다시 실행합니다. Android 목록에 없으면 설정 → 애플리케이션 → Chrome → 권한 → **근처 기기**를 허용합니다. 변경 뒤 Chrome에 돌아와 재시도하고 다른 앱의 장치 연결을 종료하세요. Web Serial과 HTTPS 같은 보안 연결이 필요하며 절전·다른 앱의 포트 사용이 연결을 막을 수 있습니다.

**R2:** 전원·PC/휴대폰 Bluetooth를 켜고 Web Bluetooth 브라우저에서 연결 테스트 → 장치 선택창의 DiFluid R2를 선택합니다. HM Digital의 사전 페어링/포트 절차를 R2에 적용하지 않습니다. 다른 앱·탭의 R2 연결을 종료하세요. Android 목록에 없으면 설정 → 애플리케이션 → Chrome → 권한 → **근처 기기**를 확인합니다. OS/Chrome에 따라 위치 권한·위치 기능이 필요할 수 있으며 요청되면 같은 권한의 위치 및 휴대폰 위치 설정을 확인합니다. 메뉴 이름은 다를 수 있고 변경 후 재시도하세요.

Auto/횟수를 확인하지 못하면 위쪽 DiFluid R2 연결 표시의 설정창에서 **설정 다시 확인**을 누릅니다. 앱은 Disconnected인데 기기에 연결 아이콘이 남고 목록에도 없다면 선택창 닫기 → R2 완전히 끄기 → 앱 Disconnected 확인 → 다시 켜기 → 연결 순서로 시도합니다. 계속 안 되면 다른 앱·탭을 확인하세요. 이는 복구 절차이며 드문 불일치의 원인은 확정되지 않았습니다.

보조값·실시간 연결은 기록/백업에 넣지 않습니다. 프로필·컨트롤 표시는 저장하지만 장치 Auto/Count는 앱 백업 설정이 아닙니다.

### 측정 완료·입력 보호·복구

결과는 원래 입력 대상이 유효할 때만 적용됩니다. Quick/Class·학생·실습·편집 전환, 폼 초기화, 복원, TDS 직접 수정은 과거 반영을 취소합니다. 같은 화면으로 돌아와도 되살리지 않습니다. 이미 보낸 R2 측정은 종료 또는 명시적 재연결까지 추적하고 새 PC 명령을 막습니다. 반영 취소가 물리 측정을 멈춘다는 뜻은 아닙니다. 단순 화면 갱신·잠금/복귀는 입력 대상을 바꾸지 않습니다.

숫자 측정값은 계산 범위 밖이어도 입력에 보존합니다. 이는 전송된 측정값 반영이지 물리적 정확성·계산 적합성을 보장하지 않으며 **0 < TDS < 100%** 계산/저장 규칙은 유지합니다.

연결된 헤더/설정 아이콘에서 모델·펌웨어·확인된 Auto/Count를 봅니다. 연결은 설정을 덮지 않고 읽으며 명시적 변경은 장치 확인·재읽기를 거칩니다. 측정 중 잠기고 보정·펌웨어 갱신은 구현하지 않습니다. 장치·PC Count를 통일하며 1은 Single, 2~10은 같은 횟수 Average를 요청합니다. 본체·자동 측정도 현재 입력을 채울 수 있고 진행값은 미리보기이며 최종 반영은 한 번입니다.

- **장치 Average:** 전체 진행·완료가 확인된 최종 평균을 사용합니다.
- **Single 및 온도 안정화 Loop:** 최종값을 사용합니다.
- **장치 시작 Auto ON·Count>1·Single→Loop:** 캡처한 Count인 N의 마지막 수신 Loop 값을 평균하고 부족하면 마지막 값을 사용합니다. PC/버튼 Average·일반 Single 안정화에는 적용하지 않으며 장치 Average가 오면 자체 최종값을 우선합니다.

Average 최종값 누락 시 앞선 평균을 재사용하지 않습니다. 완료 상태 뒤 부족한 최종 데이터에 1.5초 추가 대기를 주고 미해결·검출 가능한 모순이면 기존 TDS를 보존하며 명시적 재연결이 필요합니다. 앱 정책이며 장치 지연의 최대 보장이 아닙니다.

시작 지연 20초·유효 활동 뒤 무응답 60초·실제 Start 뒤 장시간 120초에 안내합니다. 완료로 판정하거나 새 PC 측정을 풀거나 자동 재시도하지 않습니다. 상태의 **자세히**와 설정창의 **다시 연결**에서 복구합니다. 복구는 과거 반영·연결을 정리하고 재연결·설정 읽기를 하되 자동 측정하지 않습니다.

## 데이터와 개인정보

기록·이름·노트·피드백·프로필·설정은 브라우저에 저장하며 앱 서버 자동 업로드·분석 이벤트 전송을 하지 않습니다. 측정기는 직접 연결하고 연결·보조값은 런타임 전용입니다. 사용자가 실행한 내보내기·복사·공유는 선택한 기기/서비스를 사용합니다.

공식 HTTPS 진입점은 **Cloudflare Web Analytics**로 방문·성능을 분석하며 추출 기록과 구분합니다. 원본 앱은 로컬·localhost·다른 출처/프로젝트 경로에서 요청하지 않으며 차단/실패가 핵심 앱을 막지 않습니다. Cloudflare는 브라우저 저장소에 접근하지 않는다고 설명하지만 외부 스크립트 로드는 공급자 신뢰 경계이며 브라우저 격리는 아닙니다.

Search Console은 검색/소유권 메타 태그를 사용하고 Google Analytics·Tag Manager를 추가하지 않습니다. 호스팅·분석사는 일반 웹 요청 정보를 처리할 수 있습니다. [PRIVACY.md](PRIVACY.md) 및 앱 About의 내부 안내에서 처리·보관·내보내기·선택·공개 문의를 확인하세요.

## 백업·버전 호환성

v4.6.1는 v4.4.3 도입 **schema v7**과 기존 저장 키·백업 식별자를 유지합니다. v1~v6도 가져옵니다. v7은 Quick/Class 저장 기록별 boolean 확인 필드를 엄격히 요구합니다. 과거 기록은 측정값·물양 해석·노트·피드백·측정기 설정·보유계수를 바꾸지 않고 미확인으로 이관합니다.

v4.5.0 이전은 같은 schema라도 R2를 지원하지 않고 v4.5.2 이전은 새 표시 선호를 버릴 수 있습니다. 이전 앱과 업그레이드 전 백업을 보관하세요. 현재 표현은 엄격히 검증하고 과거 표현은 해당 이관 계약을 따릅니다. 초기 v2 `excludedStudents` 누락은 허용하되 잘못된 값은 거부하며 v3 이상은 엄격합니다. 범위 밖 TDS의 기존 기록은 원값을 유지하되 정상값으로 수정하기 전 계산·차트에 쓰지 않습니다.

Import 한도는 읽기 전 파일 **32 MiB(33,554,432 bytes)**, 파싱 후 문자열/키당 **65,536 UTF-16 단위**, 텍스트 합계 **16,777,216 단위**, 목록당 **250,000 항목**, 구조 **3,000,000 값**, 중첩 **64단계**입니다. 초과를 잘라내지 않고 거부합니다. 수업 권장 크기나 저장 가능 용량 보장이 아닙니다. 복구·대기 사본도 공간을 사용하므로 특히 큰 데이터는 외부 백업하세요.

정규화는 알려진 Settings/Quick 필드만 남기고 알 수 없는 필드를 제거합니다. 기록·노트·피드백·계수·확인은 기존 계약을 따르며 거부된 파일 원본은 바꾸지 않습니다. 저장 후보 검증·이전 확정 복구 사본을 사용하고, 유효 사본이 없거나 더 새로운 schema면 자동 쓰기를 중단합니다. 이때 원시 후보를 내보내는 복구 전용 묶음은 점검용이며 정상 앱 백업처럼 Import하는 용도가 아닙니다.

충돌·오래된 탭은 영구 변경을 멈추되 메모리 내용을 내보낼 수 있습니다. 전체 초기화 세대는 참여 탭의 과거 대기/주/복구 사본 부활을 막습니다. 지원 환경은 Web Locks로 쓰기·세대를 직렬화하고 미지원은 변경 감지만으로 동시성을 완전 조정하지 못합니다. 세션 전용 저장은 탭을 닫기 전 백업하세요.

업그레이드 전에 백업하고 같은 저장소의 구버전 탭을 닫으세요. v4.4.3 이전은 초기화 세대 보호에 참여하지 않으므로 이관 데이터에 열지 마세요. v7 백업은 이전 schema 앱용이 아닙니다.

## 로컬 실행·배포

최신 브라우저로 `index.html`을 여세요. 로컬 URI의 이미지 클립보드·측정기 접근은 보안 정책으로 제한될 수 있어 모바일 측정기 사용은 GitHub Pages 같은 HTTPS를 권합니다. 원본 로컬 앱은 분석을 요청하지 않으며 대표 이미지·개인정보 문서·사이트맵은 계산기 실행에 필요하지 않습니다. 로컬 문서 링크를 쓰려면 파일을 함께 보관하세요.

공식 주소는 https://ehmade.github.io/brewing-control/ 입니다. 배포 파일은 다음과 같습니다.

```text
index.html
README.md
CHANGELOG.md
COPYRIGHT.md
PRIVACY.md
social-preview.png
sitemap.xml
```

Privacy는 앱 내부 창과 Markdown 문서로 제공합니다. 검색 메타데이터·사이트맵은 한국어와 영어 진입 주소를 제공합니다. 영어 검색·공유 진입 주소는 /en/이며 앱 내부 언어 변경은 주소를 이동하지 않습니다. 프로젝트 robots.txt·백엔드·계정·호스팅 이전은 추가하지 않습니다.

Google 인증 태그는 유지합니다. Cloudflare 토큰은 공개 사이트 식별자이지 API 비밀키가 아닙니다. 독립 로더는 정확한 공식 HTTPS 루트/index 경로만 허용하고 자동 SPA 추적을 끕니다. 앱 상태·맞춤 이벤트를 읽거나 보내지 않으며 다른 프로젝트에 같은 토큰을 붙이지 마세요.

공개 갱신 뒤 소유권·사이트맵·분석 수신·공개 이미지/메타 응답을 확인해야 합니다. 검색 색인·검색 결과 문구·캐시된 공유 카드는 각 서비스가 결정합니다. 내부 테스트 세부는 검증 패키지에서 관리합니다.

## 참고자료·사용 조건

- E. E. Lockhart. *The Soluble Solids in Beverage Coffee as an Index to Cup Quality.* Coffee Brewing Institute, 1957.
- Specialty Coffee Association. *Coffee Brewing Control Chart*, Version 3, revised March 2019.
- J.-X. Guinard et al. *A new Coffee Brewing Control Chart relating sensory properties and consumer liking to brew strength, extraction yield, and brew ratio.* Journal of Food Science 88(5), 2023. DOI 10.1111/1750-3841.16531.

독립 프로젝트로 **SCA와 제휴하거나 승인을 받지 않았으며** SCA 로고·차트 원화를 포함하지 않습니다.

© 2026 Taehee Yoon. All Rights Reserved. 호스팅 앱과 저작권자가 배포한 수정 없는 원본은 개인·교육·연구·업무 목적(카페·유료 교육 포함)으로 무료 사용 가능합니다. 자신의 기록·JSON·차트는 저장·사용·내보내기·공유할 수 있습니다. 앱 사용이 관련 법률·플랫폼 약관 외에 보호된 코드·인터페이스·문서 재사용/수정/재배포 권한을 주지는 않습니다. 원리·공식·개념·기능 아이디어에 독점 권리를 주장하지 않고 제3자 권리·라이선스는 유지합니다. 전체 조건은 [COPYRIGHT.md](COPYRIGHT.md)를 보세요.

---

<a id="english"></a>

# Coffee Brewing Control

**Work toward the extraction targets you choose.** Coffee Brewing Control brings measurement, brew records, chart interpretation, and adjustment guidance together in a browser. It supports repeated personal testing and barista practice sessions, including student records and instructor feedback.

Use tasting and your own brewing goals to decide what to change. Target ranges are configurable references, not a verdict on flavor or quality. Notes are optional; the app does not automatically interpret tasting notes.

[Open Coffee Brewing Control](https://ehmade.github.io/brewing-control/) · [Changelog](CHANGELOG.md) · [Privacy & Data Handling](PRIVACY.md)

Current release: **v4.6.1 / schema v7**.

## Language

The first visit uses the entry URL language; a saved language preference takes priority on either URL. Open **Settings → 언어 선택 · Languages** and choose 한국어 or English. The choice is stored separately in this browser, is not part of brewing backups, stays selected after Restore, and is cleared by full app-data reset. Other tabs do not abruptly change language.

User-authored names, notes, and feedback are not translated. The original built-in class/session names and automatically created default sessions use localized display names without changing their raw saved names. Class, session, student, Target Profile, and Chart Preset names filled in for blank values, and names generated by migration, are localized only when their automatic origin is known. Explicit user names remain verbatim even when they match a default name; unmarked historical names are never guessed. Name-origin metadata is retained in backups, but an older app may remove it when saving again. An unassigned extraction target uses a localized placeholder/display name. Explicit historical target names are preserved; clear the name and Apply, or load the default target, to use automatic naming.

Changing language preserves live inputs, drafts, chart selections, and the device connection. About, Changelog, Privacy, and Copyright show the selected language. PNG exports use the language and data captured when generation starts.

## Getting started

Direct refractometer connections depend on the device, browser, and operating system. R2 was integration-tested on Windows Chromium and Android Chrome; HM Digital follows the Web Serial and pairing guidance below. Safari and standard iOS browsers do not support these direct connection workflows. Manual TDS entry is available without a device connection.

1. Open the page in a modern browser and choose **Quick** for repeated personal tests or **Class** for student practice records. No app installation or measurement-device connection is required for manual entry.
2. Enter dose, measured TDS, and at least one of brew water or beverage mass. The other mass can be estimated using the selected liquid-retention assumption. TDS must come from an actual measurement; the app does not measure it without a supported connected device.
3. Read the calculated result and chart relative to your selected target. Change the target in Settings when appropriate for your coffee and purpose. Save an attempt explicitly, make the next adjustment, and examine the change across records.
4. Export a JSON backup when you want to preserve or transfer records. They are stored in this browser, not a central user account.

Supported device access and image copy / sharing depend on the browser, operating system, and secure-context rules. Ordinary manual calculation does not require a connected refractometer.

## Features

- **Quick** — enter brew measurements, save and edit repeated attempts and per-attempt notes, estimate either missing brew mass, compare changes, set a target point, and export the current chart as PNG.
- **Class** — manage classes, students, and reusable practice sessions; keep per-student attempts and instructor feedback.
- **Chart** — interactive TDS / extraction-yield chart with configurable target range, chart scale, brew-ratio lines, filters, and comparison paths.
- **Measurement Device** — optionally connect a supported refractometer and insert measured TDS directly into Quick or Class without changing the existing save / record workflow.
- **Input review** — distinguish calculation validity from unusual but calculable brew data, retain the original result and classification, and acknowledge intentional outlier records.
- **Profiles & presets** — save extraction targets as Target Profiles and chart scales / brew-ratio guides as Chart View Presets; the liquid-retention coefficient is managed independently in Calculation Settings.
- **Local-first storage** — records are stored in the browser; full JSON backup and restore are available.
- **Independent core app** — the calculator, records, chart, and device logic run from index.html without a framework or external runtime library. Only the official hosted entry points request the optional Cloudflare analytics script. Social-preview and documentation assets are separate static files.

## Quick, Class, and Chart

**Quick** keeps a LIVE measurement form and saved attempts for repeated testing. Use a target point and chart paths to examine direction across attempts. The experiment name and common note are separate from per-attempt notes.

**Class** organizes classes, students, practice sessions, attempts, and instructor feedback. The collapsed context header identifies the current class, student count, and practice. Expand it to manage classes / students / sessions. Practice selection and creation live in the practice tab. The save button creates a record; simply entering values does not save a new attempt. Class charts show selected saved records, including an empty chart when no records have been added.

**Chart** brings TDS, extraction yield, brew-ratio reference lines, chosen targets, and record paths together. Chart Tools provides guide / goal controls, filters, and image export. Classification follows your current target settings rather than certifying flavor or quality. Display and chart-tool details are described below.

## Default reference profile

The built-in **Classic Filter** Target Profile starts with:

- Extraction yield: **18–22%**
- TDS: **1.15–1.35%**

These values are informed by published Specialty Coffee Association brewing materials and are provided as a starting reference only. Target ranges, chart scales, brew ratios, and liquid-retention assumptions are configurable and should not be interpreted as universal sensory-quality standards or physical limits.

When beverage mass is left blank, the application estimates beverage mass from brew water, dose, measured TDS, and the configured liquid-retention value. When brew water is left blank instead, it estimates brew water and Brew Ratio from directly entered beverage mass, dose, and TDS. If both masses are entered, both are used directly; if neither is entered, neither is estimated. The default liquid-retention coefficient is **2.1**, and it can be changed independently in Calculation Settings. Extraction-yield results therefore depend on the measurements and assumptions supplied by the user.

The two directions use the same mass-balance relationship, with masses in grams and TDS entered as a percentage:

    Beverage = (Brew water − Liquid retention × Dose) / (1 − TDS/100)
    Brew water = Beverage × (1 − TDS/100) + Liquid retention × Dose

Estimated brew water and its Ratio are marked as estimates. They provide a reference under the configured retention assumption rather than reconstructing extra liquid left in the dripper when brewing is stopped. Record cards and chart details identify the calculation source and the retention value used.

New Quick and Class records store the liquid-retention value used when they are saved. Editing a saved record continues to use that value, including a switch from manual to automatic Beverage. The global setting applies to new LIVE calculations, new records, and chart Brew Ratio guides; it does not change saved automatic-Beverage or automatic-Brew-water results. Target classification and feedback still follow the current target settings. EY calculated from directly entered Beverage does not use the retention coefficient; automatic Brew water and Ratio estimation still use it. Blank raw mass inputs remain blank in saved records and backups so an estimate is not mistaken for a direct input.

Records from before schema v5 receive the dataset's configured retention value during migration, preserving their immediately preceding displayed results. This is a migration assumption, not a reconstruction of the coefficient originally used for each historical brew.

## Input validity and review

A calculated brew result requires positive dose, brew-water and beverage values, finite derived values, and TDS strictly inside **0 < TDS < 100%**. Quick and Class show the accepted TDS interval beside the input. Values outside that interval can remain visible in the input field, but new records cannot be saved from them and they do not produce extraction yield, dissolved solids, classification, direction feedback, or chart points. Brew Ratio may still be shown when it can be calculated independently from dose and brew water.

Separately, the app evaluates calculable records for unusual mass relationships and extreme derived results. These records keep their existing values, target classification, and direction feedback while showing **Review inputs**. After saving, the user can acknowledge that the record was entered intentionally; the record then shows **Reviewed**. Changing dose, brew water, beverage, TDS, the input mode, or the retained coefficient clears that acknowledgment, while changing a Quick note or instructor feedback does not.

The acknowledgment is stored with the record. The review result and its internal reason codes are recalculated from the current evaluator rather than stored in the backup.

## Editing saved attempts

Quick history supports editing through the existing measurement form. An edit keeps the original attempt ID, position, and liquid-retention value. Saving or cancelling returns to the LIVE input that was present before editing. Brew water may remain blank for inverse estimation; editing keeps the saved liquid-retention value and preserves directly entered values. Unsaved edits are not committed records; reloading the page returns to the preserved LIVE input.

Each saved Quick attempt has an optional note edited directly on its card, independently of the measurement form. Click the note to edit it; save with the button or Ctrl/⌘+Enter, and cancel with the button or Esc. Unsaved notes survive same-context refreshes but are not committed by reloading the page. Saved notes appear in chart tooltips and details and are included in JSON backups. The experiment name and common Quick note remain separate. Individual Quick record deletion asks for confirmation.

Class record edits preserve chart-filter selections. Instructor-feedback drafts remain in place during same-context screen refreshes; saving, cancelling, or changing the editing context ends the draft.

## Display modes and chart tools

Separate views is the default: Quick and Class each open their corresponding chart, and the chart returns to the corresponding input screen. Empty Class charts are supported.

In Settings → Display layout, side-by-side view places Quick or Class inputs beside the chart with independent scrolling. The shared input-to-chart ratios are 35:65, 40:60 (default), and 45:55. A new side-by-side selection requires a viewport of at least 1280 CSS pixels and at least 1200 pixels of workspace. Resizing does not overwrite a saved side-by-side preference: narrow screens show a warning, allow horizontal scrolling, and offer an explicit switch to Separate views. A mode selected in Settings takes effect when leaving Settings.

Input area size offers Default and Compact, in either mode. Compact applies only at widths of at least 1024 CSS pixels with a hover-capable fine pointer. Touch and narrower screens use Default and disable the size controls without erasing the saved preference. The header and chart are not reduced by this option. Mode, ratio, and size are included in browser storage and JSON backups; older backups default to Separate views / 40:60 / Default. Older app versions may discard these new preferences when saving.

Chart size offers Fit to screen (default) and Large. Fit uses available height while preserving minimum readability; short screens or expanded controls may still require scrolling. Large uses available width up to the existing 840-pixel stage width and permits vertical scrolling. On narrow screens the chart uses the available width and the size controls are unavailable. Your saved choice resumes on wider screens; sufficiently wide touch or landscape views can still use both choices. This setting works in both modes, is saved in JSON backups, and returns to Fit after a full reset.

Chart Tools combines guide / target-point and student / attempt controls with image copy, PNG save, sharing, and a Chart / Target Settings shortcut. The shortcut scrolls to the relevant Settings sections without opening them. Collapsing Chart Tools hides its buttons, but keeps the summary and full out-of-range warning visible. Chart Tools and Class management can be toggled by clicking header text or empty space, with unboxed plus / minus indicators; other header buttons retain their own actions. Keyboard users can operate the native disclosure buttons. Image exports retain their existing geometry and exclude tooltips and coordinate previews, regardless of chart size.

## Measurement device support

Select a Device Profile in Settings to enable optional direct TDS measurement. Supported profiles are:

- **HM Digital BTR-1000 / RCM-1000BT** — Web Serial over Bluetooth Classic SPP; the existing Windows workflow and the supported Android Chrome workflow. Serial access / pairing support must be checked for the browser and OS.
- **DiFluid R2** — Web Bluetooth (BLE); tested with DFT-R102 firmware V219. Windows Chromium and Android Chrome were used for integration testing. Device access depends on browser and operating-system support.

The header shows connection state; Quick and Class expose the measurement button. A completed measurement fills the current TDS input through the normal input path. It does **not** automatically save a Quick attempt or create a Class record. Pending, failed, or incomplete measurements preserve the existing TDS.


### Connection setup

**HM Digital — Windows / Android**

1. Turn on the refractometer.
2. On Windows, if it does not appear in Chrome's device selection dialog, pair **BTR1000(Coffee)_xxxx** in **Windows Settings → Bluetooth & devices** first.
3. On Android, check **Android Settings → Apps → Chrome → Permissions → Nearby devices** if the device is missing.
4. Return to the app and connect from Settings or the header control. The operating system may take time to report a powered-off Bluetooth Classic device as disconnected.

**DiFluid R2 — Windows / Android**

1. Turn on R2 and the computer / phone's Bluetooth. Use a browser that supports Web Bluetooth; an HTTPS or localhost origin is recommended for device access.
2. Choose the R2 Device Profile and connect from the app's device chooser. If another app or browser tab is using R2, disconnect it there first.
3. On Android, if R2 is missing, check **Android Settings → Apps → Chrome → Permissions → Nearby devices**. Depending on Android / Chrome version, location permission or the system location setting may also be required. Menu names vary; return to Chrome and retry after changing permissions.
4. If Auto / Count cannot be confirmed, open the R2 connection control at the top of the page and select **Refresh settings**.
5. If the app shows Disconnected while the device still shows a connection icon and R2 is absent from the chooser, close the chooser, power R2 fully off, wait for Disconnected in the app, power it on, and connect again. Check other apps / tabs if it remains unavailable. This is a recovery procedure; the rare mismatch's cause has not been established.

Successful auxiliary device readings remain runtime-only. They are not added to brew records or backups. The R2 profile selection and measurement-control visibility are saved; live connections and device Auto / Count are not app backup settings.

<details>
<summary>Detailed measurement behavior, input protection, and recovery</summary>

Results apply only while their original input context remains current. Switching Quick / Class, students, sessions, or edit targets, resetting the form, restoring a backup, or manually changing TDS cancels the earlier delivery. Returning to the same screen does not restore that permission. An already sent R2 measurement remains tracked and blocks another PC command until its lifecycle ends or the user explicitly reconnects. Cancelling delivery does not claim to stop the physical device. Simply repainting the screen or locking and unlocking it does not change the input target.

Normal numeric readings are preserved in the input, including values outside the brewing-calculation interval. This confirms delivery of the device-reported value, not its physical accuracy or suitability for brewing calculations. The existing **0 < TDS < 100%** calculation / record-saving rules still apply.

### DiFluid R2 settings and measurement

Click the connected R2 control or its settings icon in the header to open the existing settings popup. It shows confirmed model / firmware information and Auto / measurement Count. Connection reads the device settings without overwriting them; explicit user changes use device acknowledgment and readback. Auto / Count are locked while measuring. The app does not implement device calibration or firmware updates.

Device Count and PC measurement Count are shared: Count 1 requests Single, and Count 2–10 requests Average with that same Count. Device-button and Auto-initiated measurements can also fill the current Quick / Class input. Progress values remain previews; the app commits a final result once.

- **Device Average:** use the device's confirmed final average with complete progress and completion status.
- **Single, including temperature-stabilization Loop:** use the final reading.
- **Device-origin Auto ON, Count greater than 1, Single-to-Loop:** use the last N received Loop readings, where N is the captured device Count. If fewer than N are available, use the final Loop reading. This app-side averaging is not applied to PC / button Average or ordinary Single stabilization. If the device reports Average, its final average takes precedence.

Average completion cannot reuse an earlier running average when final data is missing. After completion status, insufficient final data receives a bounded 1.5-second additional wait; unresolved or detectably inconsistent data preserves the previous TDS and requires explicit reconnection. This interval is an application policy, not a guaranteed maximum device delay.

Start delay (20 seconds), silence after valid measurement activity (60 seconds), and a long measurement after actual Start (120 seconds) produce guidance. They do not declare completion, unlock a new PC measurement, or automatically retry. The nearby status offers **Details** when appropriate; the existing popup offers **Reconnect**. Recovery first cancels old delivery and cleans up the connection, then reconnects and reads settings without automatically measuring.


</details>

## Data and privacy

Brew and class records, names, notes, feedback, profiles, and settings are stored locally in this browser. The app does not automatically upload them to an application backend or send them as analytics events. Device communication is direct through browser APIs; connections and auxiliary readings are runtime-only. User-requested export, copy, and sharing use the selected device or service.

The official HTTPS app entry points use **Cloudflare Web Analytics** for visits and page performance. This is separate from brewing records. The original app does not request that script on local files, localhost, other origins, or other project paths. Blocking or failing analytics must not prevent use of the core app. Cloudflare describes its beacon as not accessing browser storage; loading a third-party script is nevertheless a supplier-trust boundary, not a browser sandbox.

Google Search Console uses a verification meta tag for search / ownership management; no Google Analytics or Tag Manager script is added. Hosting and analytics providers may receive ordinary web-request information. See [Privacy & Data Handling](PRIVACY.md), also available inside the app from About, for processing, retention, exports, choices, and public-contact guidance.

## Backup and version compatibility

Version 4.6.1 continues to use **schema v7**, introduced in v4.4.3, with the existing browser storage key and JSON backup format identifier. Supported schema-v1 through schema-v6 data remain importable. Schema v7 includes a strict boolean review-acknowledgment field on every saved Quick and Class record. Earlier records receive an unacknowledged state during migration without changing their stored brew measurements, water-input interpretation, notes, feedback, measurement-device settings, or retained liquid-retention value.

Application versions before v4.5.0 do not support the R2 profile even when they use schema v7. Versions before v4.5.2 may discard the newer display preferences. Keep a pre-upgrade backup and the previous application for rollback.


<details>
<summary>Detailed Import validation and resource limits</summary>

Current-schema representation is validated strictly, while supported historical shapes are handled by their migration contracts. In particular, early schema-v2 data may omit `excludedStudents`; malformed values remain rejected, and schema-v3-or-newer data retain their stricter requirement. Existing imported records with TDS outside the current calculated-result interval retain the original raw value but do not generate calculated brew results or chart points until edited to a valid TDS.

Backups are checked against Import resource budgets before they are applied. The file limit is **32 MiB** (33,554,432 bytes), checked before reading. After JSON parsing, the limits are **65,536 UTF-16 code units per string or object key**, **16,777,216 code units of combined text**, **250,000 entries per collection**, **3,000,000 structural values**, and **64 levels of nesting**. Excess data is rejected with an explanation rather than truncated. These are workload limits, not recommended classroom sizes or a promise that the browser can store the data. Recovery and pending snapshots also consume storage space; retain an external JSON backup, especially for large datasets.

Normalization keeps known Settings and Quick draft fields and discards unrecognized properties. Existing record values, notes, feedback, saved retention, and review acknowledgment remain subject to their existing compatibility contracts. The selected backup file remains unchanged if Import is rejected.


</details>

The app checks stored candidates before loading and preserves the previous committed snapshot as a recovery copy. If no valid copy can be read, or a newer schema is found, automatic writes stop to protect the stored data. In that condition, JSON export can preserve the raw candidates as a recovery-only bundle; this bundle is for inspection and is not a normal importable app backup.

Conflicting or stale tabs stop persistent mutations and retain their current in-memory content for read-only export. Full app-data reset uses a shared reset generation so participating tabs cannot restore queued, pending, primary, or recovery data from before the reset. Web Locks serialize participating tabs' writes and reset-generation changes where supported. Without that API, change detection remains available, but simultaneous operations cannot be fully coordinated. Session-only storage is temporary and should be backed up before closing the tab.

Before upgrading, export a JSON backup and close older app tabs that use the same browser storage. Versions before v4.4.3 do not participate in the reset-generation protection and should not be opened against migrated data. Keep the old application and its pre-upgrade backup if rollback is needed; schema-v7 backups are not intended for versions that use an older schema.

## Running locally

Open `index.html` in a modern browser.

Some browser features, especially direct clipboard image writing or device access on mobile local-file URIs, can be restricted by browser security rules. For mobile measurement-device use, serving the app over HTTPS such as GitHub Pages is recommended.

The original local app does not request Cloudflare analytics. The provided social-preview image, Privacy document, and sitemap are not required by the core calculator. Keep the documentation files together to use their local links.

## Deployment and public-site files

The official app uses GitHub Pages at https://ehmade.github.io/brewing-control/. The static site files are:

```text
index.html
README.md
CHANGELOG.md
COPYRIGHT.md
PRIVACY.md
social-preview.png    # original 1200 × 630 link-card image
sitemap.xml
```

Search metadata and the sitemap identify Korean and English entry URLs, each with its own canonical URL and reciprocal language alternatives. In-app language switching does not navigate away. No project-level robots.txt, application backend, account system, or hosting migration is added.

The issued Google verification meta tag stays in the head after verification. The Cloudflare client token is a public site identifier, not an API secret. The independent loader uses only the exact official HTTPS root / index.html paths and disables automatic SPA tracking; it does not read app state or emit custom events. Do not put the same token on unrelated projects.

Google ownership and sitemap submission, actual Cloudflare dashboard receipt, and public image / metadata responses must be checked after an authorized public update. Search indexing and the wording shown in search results or cached social cards are controlled by the respective services. Internal test details belong in the verification package, not this user guide.

## References

- E. E. Lockhart. *The Soluble Solids in Beverage Coffee as an Index to Cup Quality.* Coffee Brewing Institute, 1957.
- Specialty Coffee Association. *Coffee Brewing Control Chart*, Version 3, revised March 2019.

This project is independently developed and is **not affiliated with or endorsed by the Specialty Coffee Association**. No SCA logo or SCA chart artwork is included.

- J.-X. Guinard et al. *A new Coffee Brewing Control Chart relating sensory properties and consumer liking to brew strength, extraction yield, and brew ratio.* Journal of Food Science 88(5), 2023. DOI 10.1111/1750-3841.16531.

## Copyright & Usage

© 2026 Taehee Yoon. All Rights Reserved.

The hosted Coffee Brewing Control application may be used free of charge for personal, educational, research, and professional purposes, including use in cafés and paid instruction. An unmodified copy distributed by the copyright holder may also be run locally for the same permitted purposes.

Users may save, use, export, and share their own brewing records, backup JSON files, and chart images produced through the application's provided features.

Permission to use the application does not grant permission to reuse, modify, or redistribute its protected source code, interface implementation, documentation, or other protected project materials, except as permitted by applicable law or platform terms.

No exclusive rights are claimed over brewing principles, formulas, scientific concepts, or functional ideas. Referenced third-party materials remain subject to their respective rights. Third-party software, libraries, and other components used by this project remain subject to their respective licenses and terms.

See [COPYRIGHT.md](COPYRIGHT.md) for the full terms.

## 언어별 진입 · Language entry URLs

- 한국어 / Korean: https://ehmade.github.io/brewing-control/
- English: https://ehmade.github.io/brewing-control/en/

첫 방문은 진입 주소의 언어로 시작하며, 저장된 언어 선택이 있으면 두 주소 모두 그 선택을 사용합니다. 앱 안의 언어 전환은 페이지를 이동하지 않아 입력과 측정기 연결을 유지합니다.

Korean and English entry URLs are available. On a first visit, the entry URL determines the language; a saved language preference takes priority on both URLs. In-app language switching does not navigate away, preserving inputs and the device connection.
