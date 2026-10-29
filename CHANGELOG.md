[한국어](#한국어) · [English](#english)

<a id="한국어"></a>

# 변경 이력

Coffee Brewing Control의 주요 변경 사항을 기록합니다.

첫 GitHub 공개 전에도 반복적으로 개발했습니다. 초기 이력은 중간 테스트·디버깅의 모든 변경이 아니라 주요 사용자 기능과 구조적 이정표 위주로 요약했습니다.

## [4.6.0] — 2026-10-30

### 추가·변경
- 한국어/영어 UI와 별도 저장되는 표시 언어 선택을 추가했습니다. 사용자 기록·이름·초안·측정 입력 소유권은 보존합니다.
- 측정기·저장 실패·Import/복구 및 조건부 안내를 번역했습니다.
- About·변경 이력·개인정보 안내를 현재 언어로 제공하며 Privacy와 Copyright를 앱 내부 창으로 옮기고 상단 이전으로 버튼을 추가했습니다. 문서는 한국어/영어 블록으로 제공합니다.
- 기본 이름 표시 경로와 긴 차트 안내를 정리하고, PNG 제목·범례·타겟을 생성 시작 시점의 언어/데이터에 고정했습니다.

### 호환성
- schema v7, 기존 계산·기록 해석·측정기 프로토콜을 유지합니다. 언어 선호는 추출 백업에 포함하지 않습니다.
- 앱이 생성한 이름을 구별하는 선택적 출처 정보를 백업에 보존합니다. 구버전 앱에서 재저장하면 이 정보가 제거될 수 있으며, 출처가 불명확한 과거 이름을 임의로 번역하지 않습니다.
- 많은 수강생의 PNG 범례가 잘리지 않도록 필요한 경우에만 이미지 하단을 확장합니다.

## [4.5.3] - 2026-10-27

### 추가
- 한국어·영어 검색 메타데이터, 표준 URL, Open Graph 카드 및 앱 차트 기반의 고유 대표 이미지를 추가했습니다.
- 사용자가 발급한 Google Search Console 인증 태그와 단일 URL 사이트맵을 추가했습니다.
- 공식 HTTPS 앱 진입 경로에서만 실행하고 SPA 추적은 끈 독립적인 Cloudflare Web Analytics 로더를 추가했습니다.
- 같은 Markdown 원본에서 생성하는 읽기용 로컬 HTML 페이지를 포함하여 개인정보 및 데이터 처리 안내를 추가했습니다.

### 변경
- README를 첫 사용·추출 흐름·타겟·표시 옵션·측정기·데이터·운영 순서로 재구성하고, 오래된 현행 버전 및 R2 호환성 설명을 수정했습니다.
- About·README·개인정보 안내를 사용자 지정 추출 목표와 로컬 추출 기록/공식 사이트 방문 분석의 구분에 맞췄습니다.

### 호환성
- schema v7, 저장 키, 백업 형식, 추출 계산, 표시 설정, 측정기 프로토콜 및 차트 이미지 출력을 유지했습니다.
- 로컬·비공식 주소의 원본 앱은 분석 스크립트를 요청하지 않으며 분석은 핵심 기능의 전제조건이 아닙니다.

## [4.5.2] - 2026-10-26

### 추가
- 분리·통합 모드 모두에서 한눈에 보기(기본)와 세로 스크롤을 허용하는 크게 보기 중 선택하고 저장할 수 있게 했습니다. 이미지 출력과는 독립적입니다.
- Quick·Class 입력과 해당 차트를 나란히 보여주는 통합 모드 및 공통 입력:차트 비율 35:65·40:60·45:55를 추가했습니다.
- 충분히 넓고 정밀 포인터를 사용하는 화면에서 기본/작게 입력 크기를 선택하게 했습니다. 터치·좁은 화면에서는 저장된 선호를 유지한 채 기본 크기를 사용합니다.
- 차트 도구에 차트/타겟 설정 바로가기를 추가했습니다. 해당 설정 위치로 이동하되 자동으로 펼치지 않습니다.

### 변경
- 차트 도구와 Class 관리를 헤더 글씨·빈 공간 클릭으로 열고 닫으며 박스 없는 +/-를 표시합니다. 헤더 안의 버튼은 고유 동작을 유지하고 기본 키보드 조작도 지원합니다.
- 기본값은 분리 모드입니다. Quick·Class에서 각각 해당 차트(빈 Class 포함)를 열고 차트에서 해당 입력으로 돌아갑니다.
- 가이드·목표점·수강생/회차 선택·이미지 복사/PNG/공유를 차트 도구에 모았습니다. 접으면 조작은 숨기되 요약과 범위 밖 경고 전문은 유지합니다.
- 화면 차트의 여백을 줄이고 가독성 하한을 유지하며 사용 가능한 높이를 활용합니다. 낮은 화면이나 펼친 조작부에서는 스크롤이 필요할 수 있습니다.
- 반·수강생·실습 관리를 요약과 펼침 탭이 있는 Class 패널로 옮겼습니다. 실습 선택·생성은 실습 탭에 있습니다.
- Settings 폭·스크롤·모드 선택 공간과 Quick/Class 전환을 안정화했습니다. 선택한 표시 모드는 Settings에서 나갈 때 적용됩니다.
- 측정기 헤더 공간·모바일 선택 버블 크기를 통일하고 수강생 추가 버튼 줄바꿈을 막았습니다. 저장/표시 안내를 명확히 하고 HTML/CSS/JavaScript를 LF로 정돈했습니다.

### 수정
- 차트/타겟 설정 바로가기 이후 기본 키보드 초점과 Tab 순서를 보존했습니다. 타겟·차트 설정은 Enter·Space로 조작할 수 있습니다.

### 호환성
- schema v7을 유지합니다. 표시 모드·입력:차트 비율·입력 크기·차트 크기를 저장·백업하며 구버전 백업에는 기본값을 부여합니다. 이전 앱은 이 선호를 버릴 수 있습니다.
- 계산·기록 해석·측정기 프로토콜·입력 소유권·이미지 출력을 유지했습니다. 화면 배치가 출력 차트의 기하 구성을 바꾸지 않습니다.
- 새 통합 모드 선택에는 뷰포트 1280 CSS px·작업 영역 1200px 이상이 필요합니다. 창 크기가 바뀌어도 저장된 통합 모드를 유지하고 좁은 화면 경고와 명시적 분리 모드 전환을 제공합니다.
- 별도 공개하지 않은 v4.5.1 내부 이동 기능 기준점을 포함합니다. 업데이트 전에 백업하고 구버전 탭을 닫으세요.

## [4.5.0] - 2026-10-25

### 추가
- HM Digital과 함께 선택할 수 있는 Web Bluetooth 기반 DiFluid R2 Device Profile을 추가했습니다.
- PC 요청·기기 시작 Single/Average, Auto Single→Loop 처리 및 기록 자동 저장 없는 Quick/Class 최종 TDS 반영을 추가했습니다.
- 헤더 연결 표시에서 장치 확인 Auto/Count·모델/펌웨어를 보는 R2 설정창과 접근 가능한 설정 아이콘을 추가했습니다.
- 기존 HM Digital 도움말을 유지하며 R2용 Windows/Android 연결·권한 경로·복구 안내를 추가했습니다.

### 수정
- Average 완료에 최종 종합값과 전체 진행 확인을 요구합니다. 누락·손상·검출 가능한 모순이 있는 최종 데이터에 앞선 평균을 재사용하지 않습니다.
- Quick/Class·학생·실습·편집 대상 변경이나 TDS 직접 수정은 반영을 취소합니다. 이미 보낸 측정은 종료·명시적 복구까지 잠기고 지연 결과는 새 대상을 덮어쓰지 않습니다.
- 측정 시작에는 일치하는 모드/상태 쌍을 요구하며 PC 명령 직전에 최근 확인 Count를 검사합니다.
- 지연·불완전 측정은 기존 TDS를 보존하고 자동 재측정 없이 명시적 재연결을 제공합니다.

### 변경
- 장치와 PC 측정 Count를 통일했습니다. 연결 시 기존 설정을 읽으며 Auto/Count 쓰기는 사용자의 명시적 변경에만 발생합니다.
- 장치 시작 Auto 다회 Single→Loop는 마지막 N개 Loop 값을 평균하며 부족하면 마지막 값을 사용합니다. 장치 Average는 자체 최종값 정책을 유지합니다.
- R2 헤더와 측정 피드백은 가용 폭에 맞추고 진행·복구 안내는 간결하게 유지하며 추가 설명은 기존 설정창에서 제공합니다.
- 계산 범위 밖의 유효한 숫자 측정값도 TDS 칸에 입력할 수 있습니다. 계산과 기록 저장 검사는 별개로 유지합니다.

### 호환성
- schema v7, 기존 저장 키·백업 식별자·Import 자원 한도와 schema v1~v7 이관을 유지합니다.
- 기존 계산·저장 기록 해석·차트/PNG·HM Digital 어댑터를 유지합니다. 실시간 R2 연결·Auto/Count·보조 측정값은 기록·백업에 넣지 않습니다.
- R2는 Web Bluetooth 지원 브라우저가 필요합니다. 업데이트 전에 백업하고 구버전 탭을 닫으며 롤백용 이전 앱과 업그레이드 전 백업을 보관하세요.

## [4.4.5] - 2026-10-23

### 추가
- Import 자원 보호를 추가했습니다. 32 MiB 초과 파일은 읽기 전에, 과도한 텍스트·목록·전체 구조·중첩은 파싱 뒤에 백업을 자르지 않고 거부합니다.

### 수정
- 프로필 선택이 복원·전체 초기화·새 선택과 겹쳐도 대체된 비동기 결과를 무시해 런타임과 저장 프로필을 일치시킵니다.
- 기록 정규화·검증에서 데이터 크기에 비례하는 함수 호출 spread를 제거해 대량 회차가 JavaScript 인자 수 제한으로 실패하지 않게 했습니다.
- 프로필 변경 후 새로고침 없이 Quick/Class 측정 버튼이 즉시 갱신됩니다. 기존 연결·측정 계약을 유지합니다.

### 변경
- 알려진 Settings와 Quick 초안 필드만 정규화하고 알 수 없는 속성은 버립니다. 기존 피드백 이관과 명시된 유효 값은 보존합니다.
- 저장 기록 순회·측정 버튼 갱신을 공유하고 일부 지역 변수 이름을 명확히 했습니다. 미사용 상태 읽기를 없애고 질량수지 단위·보유계수 소유권·HM Digital 통신 계약을 주석으로 남겼습니다.

### 호환성
- schema **v7**을 유지합니다. 자원 한도 안의 v1~v7 백업을 가져올 수 있으며 측정값·노트·피드백·확인 상태·입력 모드·보유계수의 해석을 유지합니다.
- Import 검증은 브라우저 저장 용량과 별개입니다. 저장 실패·복구·충돌·오래된 탭 처리를 유지합니다.
- 계산·분류·차트/PNG 배치·저장 키·백업 식별자·HM Digital 프로토콜을 유지하며 R2 연동이나 런타임 의존성을 추가하지 않았습니다.

## [4.4.4] - 2026-10-22

### 변경
- v4.4.5 안정화 전 내부 유지보수 기준점으로 인라인 JavaScript를 정돈했습니다. 구조적 동등성과 기존 회귀검증은 별도로 확인했습니다.
- 실행 동작·문자열/템플릿 내용·주석·HTML/CSS·단일 파일 배포를 보존했습니다. 별도 공개 릴리즈는 하지 않았습니다.

## [4.4.3] - 2026-09-25

### 추가
- Quick/Class 공통 이상 입력 검토를 추가했습니다. 계산 가능하지만 특이한 기록은 값·타겟 분류·방향 피드백을 유지하고 입력 확인 경고를 표시합니다.
- 의도한 이상값을 기록별로 확인 표시할 수 있습니다. 저장 기록에 `확인됨`을 표시하고 추출 데이터 변경은 해제하지만 노트·강사 피드백 변경은 유지합니다.
- 제외 수강생 영구 삭제를 추가했습니다. 확인 후 제외 명단·전체 실습 기록·저장 이름·강사 피드백·차트/편집 참조를 함께 제거합니다.
- Settings에 2단계 전체 초기화를 추가했습니다. 영구 사용자 상태와 측정기 선택/표시를 기본값으로 돌리고 연결을 해제하지만 내장 프로필과 측정 기능은 유지합니다.
- Quick/Class TDS 옆 범위 안내와 접근 가능한 유효하지 않음 표시를 추가했습니다.

### 수정
- 초기화 세대 조정으로 오래된 탭·대기 쓰기·복구·주/복구 사본·생명주기 저장이 초기화 전 데이터를 되살리지 못하게 했습니다. 이미 오래된 탭은 새 초기화나 영구 변경을 시작할 수 없습니다.
- `excludedStudents`가 없는 초기 schema v2도 이관합니다. 잘못된 v2 값은 거부하고 v3 이상은 엄격한 검증을 유지합니다.
- 복원 시 열린 Quick 공통 노트 편집기를 먼저 닫아 오래된 초안이 복원 데이터를 덮어쓰지 않게 했습니다.
- 보유계수 변경 후 Class 자동 추정 안내를 즉시 갱신하고 저장 기록 수정은 보존된 계수를 사용합니다.
- 검증기가 허용하는 최대 밀도에서도 차트 보조 격자를 모두 그립니다.
- 백업 파일명은 Asia/Seoul 날짜를 사용하고 JSON `exportedAt`은 UTC ISO를 유지합니다.
- 계산·이상 입력·TDS 범위·자동 추정 안내 전환 시 Quick과 좁은 2열 Class의 흔들림을 줄였습니다.

### 변경
- 유효 TDS를 **0 < TDS < 100%**로 한정했습니다. 범위 밖 신규/수정 저장은 막고, 기존 Import 원값은 보존하되 EY·용해 고형분·분류·피드백·차트 점을 만들지 않습니다. 독립 계산 가능한 비율은 표시할 수 있습니다.
- 이상 입력 검토는 계산 유효성과 별개입니다. 계산 가능한 이상값은 저장·차트 표시가 가능하고 확인 여부만 저장하며 파생 사유는 저장하지 않습니다.
- 보호된 일반 대기 쓰기는 경고 없이 완료하고 실패·충돌·오래된 탭·손상/신규 버전 데이터는 계속 알립니다.
- Settings는 접혀 시작하고 Class 동작 버튼은 이상 입력 안내보다 앞에 배치했습니다. 사용자 타겟/차트 프리셋 이름의 추가 사용자 접미사를 제거했습니다.

### 호환성
- schema를 **v7**로 올렸습니다. 모든 Quick/Class 저장 기록에 엄격한 boolean `sanityAcknowledged`를 두며 `needsReview`와 사유는 파생하여 저장하지 않습니다.
- v1~v6을 가져올 수 있으며 측정값·출처·노트·피드백·보유계수·측정기 상태를 바꾸지 않고 `sanityAcknowledged: false`를 부여합니다.
- v7 표현은 엄격히 검증합니다. 확인 필드 누락·비boolean을 조용히 보정하지 않고 거부합니다.
- 저장 키 `coffeeBrewControlClassroomV2`와 백업 식별자 `coffee-brew-control-backup`을 유지합니다. 업데이트 전에 백업하고 구버전 탭을 닫으세요. v7 백업은 구버전용이 아닙니다.

## [4.4.2] - 2026-09-22

### 추가
- 물양이 비어 있고 원두량·추출액·TDS가 있으면 Quick/Class 물양을 역산하고 비율을 추정으로 표시합니다.
- Class 강사 피드백과 같은 저장 카드 편집 방식으로 Quick 회차 노트를 추가했습니다. 저장/취소 및 Ctrl/⌘+Enter·Esc를 지원합니다.
- 호스팅 앱·저작권자가 배포한 수정 없는 로컬 앱의 무료 사용, 사용자 기록/JSON/차트의 사용·내보내기·공유, 프로젝트 자료 재사용 제한, 원리·제3자 자료의 권리 제외를 명확히 하는 저작권/사용 조건을 추가했습니다.

### 수정
- Quick 개별 삭제도 Class처럼 확인 후 제거합니다.

### 변경
- 기록·차트 상세에 추출액/물양 추정 여부와 사용 계수를 표시합니다. Quick 노트는 툴팁·상세에도 표시합니다.
- 기존 단일 파일에서 원시 입력 읽기·양방향 질량 계산·계산 출처 표시를 공유합니다. Quick 입력 폼에는 노트 칸을 추가하지 않았습니다.
- 기존 추출액 추정식·기본 계수 2.1·직접 입력 정책·범위 밖 안내·측정기 통신·PNG 배치를 유지했습니다.

### 호환성
- 물양 입력 모드와 Quick 회차 노트를 보존하도록 schema v6으로 올렸습니다. v5 이하를 가져오고 기존 물양 해석·보유계수를 유지합니다.
- 자동 추정은 파생값입니다. 빈 원시 입력과 보존 계수는 편집·JSON 백업/복원에도 유지합니다.
- 저장 키·백업 식별자를 유지합니다. 업데이트 전에 백업하고 구버전 탭을 닫으세요. v6 백업은 구버전용이 아닙니다.

## [4.4.1] - 2026-09-20

### 추가
- 기존 입력 폼에서 저장된 **Quick** 회차를 수정합니다. ID·순서·계수를 보존하고 저장/취소 후 편집 전 LIVE로 돌아갑니다.
- 이후 계산 설정이 저장된 추출액 추정값을 바꾸지 않도록 Quick/Class 기록별 **액체 보유계수 사본**을 추가했습니다.

### 수정
- 읽을 수 없는 데이터를 조용히 기본값으로 덮지 않고 후보를 검증해 정상 사본으로 복구합니다. 이전 확정 사본을 보존하며 손상/신규 schema는 자동 쓰기를 중단합니다.
- 오래된 탭 쓰기 감지 및 지원 환경의 Web Locks 동일 출처 직렬화를 추가했습니다. 충돌 탭은 다른 탭을 덮지 않고 메모리 내용을 JSON으로 내보낼 수 있습니다.
- Class 입력 소유권은 학생·반·실습·편집·복원을 따릅니다. 편집 중 기록 삭제는 오래된 입력을 지웁니다.
- 소유자 변경·입력 초기화·이후 TDS 직접 수정 뒤 지연 측정이 덮어쓰지 않습니다. 같은 학생으로 돌아와도 과거 측정은 다시 유효해지지 않습니다.
- 미저장 강사 피드백은 같은 맥락 재렌더링에 보존되고 기존 Class 수정은 차트 선택을 유지합니다.
- Import는 알려진 구조·ID·차트/프리셋 설정을 검사하고 기존 이관·과거 명단 기록을 보존합니다. 가져온 ID는 HTML 속성 삽입 대신 DOM 속성으로 지정합니다.
- 파일 저장·JSON 복사는 시작 시 새 사본을 만들며 복원은 이전 입력·편집·측정 대기 맥락도 정리합니다.

### 변경
- 입력 갱신·저장과 렌더링을 분리하고 설정을 명시하는 계산 함수를 추출했습니다. Quick 입력 때 전체 저장 목록을 다시 만들지 않습니다.
- 측정 버튼을 공유하고 Settings/Chart 역할을 분리했습니다. 미적용 계산·타겟·차트 입력은 관련 없는 갱신에 보존합니다.
- Quick 차트 요청을 모아 처리하고 PNG 전에 대기 렌더를 완료합니다. 기존 배치 유지와 함께 숫자 필드 라벨 연결·차트 설명을 추가했습니다.
- 추출액 추정식·기본 계수 **2.1**·직접 입력 정책·범위 경고·측정 통신·PNG를 유지했습니다.

### 호환성
- schema **v5**로 올렸습니다. v4 이하를 가져오며 과거 기록에는 이관 당시 데이터셋 계수를 부여해 직전 결과를 보존합니다. 알 수 없는 과거 계수를 복원하지 않습니다.
- 저장 키 **coffeeBrewControlClassroomV2**, 백업 식별자 **coffee-brew-control-backup**, local/session 저장 및 메모리 대체 경로를 유지합니다.
- Web Locks는 참여하는 v4.4.1 탭을 조정합니다. 미지원 환경은 변경 감지만 제공하고 동시 쓰기 보호를 보장하지 않습니다. 구버전 탭은 조정에 참여하지 않습니다.
- 같은 저장소 업데이트 전 백업하고 구버전 탭을 닫으세요. v5 백업은 구버전용이 아니므로 롤백용 업그레이드 전 백업을 보관하세요.

## [4.4.0] - 2026-09-19

### 추가
- 프로필은 저장하고 연결/측정은 런타임에만 두는 재사용 가능한 **측정기** 계층을 추가했습니다.
- Web Serial·Bluetooth Classic SPP로 HM Digital **BTR-1000 / RCM-1000BT**를 직접 지원합니다.
- Quick/Class **Measure TDS**를 추가했습니다. 성공값은 기존 입력 경로를 사용하며 기록을 자동 저장하지 않습니다.
- 연결 상태·재연결용 공통 헤더 및 측정 명령 없이 연결만 여는 Settings 연결 테스트를 추가했습니다.
- Windows Bluetooth 페어링과 Android Chrome **근처 기기** 권한 안내를 추가했습니다.
- 향후 장치별 기능을 위해 TDS·Brix·섭씨/화씨·굴절률·원시 응답을 표준 런타임 결과로 다룹니다.

### 변경
- 대기 중 기존 TDS를 유지하고 성공한 새 TDS로만 교체합니다.
- Air·Unstable·Hi Range·시간 초과·알 수 없는 응답·연결 끊김은 기존 TDS를 보존합니다.
- 새 측정이 이전 메시지를 대체하고 연결 끊김이 우선하며 확인된 재연결은 대기로 돌아가는 측정/연결 생명주기를 따릅니다.
- 연결과 측정을 별개로 처리하며 안전한 정리·중복 방지·오래된 포트 복구·지연 결과 거부·절전/연결 손실 뒤 재연결을 지원합니다.
- 브라우저가 실제 장치명을 제공하지 못하면 프로필 이름을 쓰며 장치가 제공하는 이름도 내부 모델에서 수용합니다.

### 호환성
- schema **v4**로 올렸습니다.
- v3 데이터·백업을 가져오며 측정기 기본값은 **없음+컨트롤 숨김**입니다.
- 프로필·표시는 저장·백업하고 실시간 포트 객체·측정 결과는 저장하지 않습니다.
- 저장 키 `coffeeBrewControlClassroomV2`와 백업 식별자 `coffee-brew-control-backup`을 유지합니다.
- Windows Chrome·Bluetooth 동글 PC·Android Chrome으로 검증했습니다. Windows는 사전 페어링, Android는 **근처 기기** 권한이 필요할 수 있습니다.

## [4.3.6] - 2026-09-18

### 추가
- 전역 보유계수·추출액 질량수지식·적용 범위를 설명하는 독립 **계산 설정**을 추가했습니다.
- 통합 Brewing Profile을 **Target Profiles**와 **Chart View Presets**로 나누고 내장값·불러오기·펼침 저장/덮어쓰기/삭제를 제공합니다.
- Class 필터에 학생별 전체 선택을 추가하고 이름 열·회차 체크를 정렬하며 일부 선택 상태도 유지합니다.
- **Coffee Brewing Control** 헤더 제목은 홈 동작으로 Quick에 돌아갑니다.

### 변경
- Quick 결과에 타겟 범위와 목표점을 별도 참고 행으로 표시하고 본문에서 목표 좌표 중복을 없앴습니다.
- 목표점까지 남은 ΔEY/ΔTDS와 조정 권고를 분리했습니다.
- 목표점 생성/제거와 범위 경고 주변의 세로 흔들림을 줄였습니다.
- 긴 실험/반/실습 이름을 개선하고 기존 위치에서 모바일 네비게이션을 내용 폭으로 제한했습니다.
- UI의 **absorption coefficient**를 **Liquid retention** 용어로 바꾸되 계산 역할을 유지했습니다.

### 호환성
- schema **v3**로 올렸습니다.
- v2 데이터를 가져오고 사용자 Brewing Profiles는 같은 이름의 타겟/차트 프리셋으로 이관합니다.
- 이관 시 적용 계수를 전역 계산 설정으로 보존하고 프리셋별 저장에서 제외합니다.
- 기존 저장 키 `coffeeBrewControlClassroomV2`·백업 식별자 `coffee-brew-control-backup`을 유지합니다.

### 보류/향후 검토 — v4.3.6 미구현
- 장기 수업 데이터에 유용해지면 Settings에 저장 크기·기록 수 요약을 추가합니다.
- 실사용 데이터가 localStorage 한계에 접근하면 StorageAdapter를 IndexedDB로 옮기는 것을 검토합니다. 향후 네이티브 앱은 SQLite 등 적절한 저장소를 사용할 수 있습니다.

## [4.3.5] - 2026-09-17

### 변경
- 사용자 표기를 **Coffee Brew Control**에서 **Coffee Brewing Control**로 변경했습니다.
- 차트 제목을 **Brew Control Chart**에서 **Brewing Control Chart**로 변경했습니다.
- **Strong/Weak**, **Under/Over** 겹침 띠를 사용하며 모서리는 두 의미를 함께 갖습니다.
- 타겟의 낮은 채도 세이지색과 비율선의 스모키 플럼색을 유지해 공개 SCA 원화와 구분했습니다.
- 추출액 자동 추정과 비율선을 전체 질량수지로 수정하고 Classic Filter 기본 계수를 2.0에서 2.1로 변경했습니다.
- 보이는 HTML 문서 버전을 바로잡았습니다.

### 추가
- 앱 안 **About & References** 창을 추가했습니다.
- 앱 안 **Changelog** 창을 추가했습니다.
- Settings에 앱 버전을 표시합니다.
- 교육/반복 테스트 목적·변경 가능한 범위·추정·로컬 저장·참고자료·SCA 비제휴를 설명했습니다.

### 호환성
- 기존 브라우저 데이터는 `coffeeBrewControlClassroomV2` 키를 계속 사용합니다.
- `coffee-brew-control-backup` 식별자를 유지하므로 기존 백업을 가져올 수 있습니다.

## [4.3.4.1]

### 추가
- Class 필터에 현재 반·실습·선택 기록 수를 표시합니다.
- 제외 명단과 복원 동작으로 되돌릴 수 있는 명단 제외를 제공합니다.

### 유지
- 제외·복원해도 과거 기록·강사 피드백은 같은 학생 ID에 연결됩니다.

## [4.3.4]

### 추가
- 재사용 가능한 Class 실습을 추가했습니다.
- 실습 생성·전환·이름 변경·삭제 흐름을 추가했습니다.
- 실습마다 학생 회차가 1차부터 시작합니다.
- Class 차트·이미지 제목이 실습을 반영합니다.
- schema v2 반/실습 구조와 이전 v4.3.x 기록 자동 이관을 추가했습니다.

### 변경
- Class 기록 비우기는 현재 실습에만 적용합니다.
- 명단 삭제를 비파괴적 제외로 바꾸어 과거 기록을 유지합니다.

## [4.3.3]

### 추가
- Quick 실험 이름·공통 노트를 추가했습니다.
- Quick/Class 툴팁의 ΔEY/ΔTDS 비교를 추가했습니다.
- 데스크톱 Quick 목표점 좌표 미리보기를 추가했습니다.
- 모바일 점·목표점 탭 동작을 추가했습니다.
- PNG 생성·복사·저장·공유·앱 안 미리보기 대체 경로를 추가했습니다.

### 변경
- 출력에 저장 경로·현재점·목표점·가이드·범례를 포함하고 일시적 hover/선택 UI는 제외합니다.

## [4.3.2]

### 변경
- 차트에서 현재 Quick 입력과 확정 저장 회차를 분리했습니다.
- 별도 현재점과 저장→현재 미리보기 경로를 추가했습니다.
- Quick 주요 피드백은 현재 입력을 따릅니다.
- 저장 회차는 별도로 동적 타겟 피드백을 받습니다.
- 가이드는 유효한 현재점을 우선하고 없으면 최근 저장점을 사용합니다.

## [4.3.1]

### 변경
- 제한된 브라우저의 전체 데이터 내보내기를 강화했습니다.
- JSON 미리보기·클립보드 대체 경로를 추가했습니다.
- 지원 시 File System Access API의 OS 저장창을 사용합니다.
- 다운로드가 차단될 수 있을 때 성공으로 단정하지 않습니다.

## [4.3]

### 추가
- 반·학생·기록·강사 피드백·Quick·프로필·차트 설정 전체 JSON 내보내기/가져오기를 추가했습니다.
- 저장 데이터 `schemaVersion`을 추가했습니다.
- 저장을 계산·UI에서 분리하는 어댑터를 추가했습니다.

### 변경
- 반 관리를 Settings로 이동했습니다.
- 브라우저 `prompt()`/`confirm()` 대신 앱 대화상자를 사용합니다.
- 이전 v4.x 데이터 이관을 유지했습니다.

## [4.2]

### 추가
- 자동 번호·연결 경로가 있는 Quick 저장 회차를 추가했습니다.
- 대화형 Quick 목표점·상대 가이드를 추가했습니다.
- Quick/Class 자동 피드백을 별도로 조절합니다.
- 명단·기록·노트·강사 피드백이 독립된 여러 반을 지원합니다.
- 이전 단일 반 구조를 이관합니다.

## [4]

### 추가
- Class 저장 기록의 동적 타겟 분류 배지를 추가했습니다.
- 추출 노트·강사 피드백을 분리했습니다.
- Class 연속 회차 사이 방향 화살표를 추가했습니다.
- EY/TDS 차트 경계·눈금 간격을 변경합니다.
- 비율선 범위·간격을 변경합니다.
- 내장 **Classic Filter**와 사용자 브루잉 프로필을 추가했습니다.

### 변경
- Settings를 접을 수 있는 구획으로 정리했습니다.
- 타겟이 바뀌면 저장 기록을 동적으로 재해석합니다.

## [3]

### 추가
- 타겟 상대 **STRONG/WEAK/UNDER/OVER** 영역과 결합 모서리 영역을 추가했습니다.
- 기존 클릭 상세와 함께 점 hover 상세를 추가했습니다.

### 변경
- **Golden Cup** 대신 중립적인 **TARGET**을 표시하며 타겟 범위 변경을 유지합니다.

## [2]

### 추가
- **Quick**과 **Class** 흐름을 분리했습니다.
- 학생 명단·학생별 연속 추출 기록을 추가했습니다.
- 추출 노트·간단한 타겟 방향 피드백을 추가했습니다.
- Class 필터·회차 연결 경로를 추가했습니다.
- 브라우저 로컬 저장을 추가했습니다.

## 초기 시제품

### 추가
- 원두량·물양·추출액·TDS·수율·용해 고형분·비율을 계산하는 단일 파일 브라우저 계산기를 만들었습니다.
- 추출액을 비우면 변경 가능한 액체 보유값으로 자동 추정합니다.
- X축 수율·Y축 TDS·기본 참고 영역·비율선이 있는 실시간 차트를 만들었습니다.

---

<a id="english"></a>

# Changelog

All notable changes to Coffee Brewing Control are documented here.

The project was developed iteratively before its first public GitHub release. Earlier entries are intentionally condensed to major user-facing and architectural milestones rather than every intermediate test or debugging change.

## [4.6.0] — 2026-10-30

### Added and changed
- Added Korean/English UI and a separately stored display-language preference, preserving user records, names, drafts, and measurement ownership.
- Localized device, storage-failure, Import/recovery, and conditional guidance.
- About, Changelog, and Privacy follow the selected language; Privacy and Copyright open inside the app with a top Back button. Documents provide complete Korean and English sections.
- Unified default-name display and long chart guidance, and captured PNG titles, legends, and targets in the generation-start language/data snapshot.

### Compatibility
- Retained schema v7, existing calculations, record interpretation, and device protocols. Language preference is not included in brewing backups.
- Backups retain optional origin metadata for app-generated names. An older app may remove it when saving again; historical names of unknown origin are never automatically reclassified.
- PNG exports extend the bottom only when needed to retain all student legend entries.

## [4.5.3] - 2026-10-27

### Added
- Added Korean / English search metadata, a canonical URL, Open Graph cards, and an original social-preview image based on the app chart.
- Added the user-issued Google Search Console verification tag and a single-URL sitemap.
- Added an independent Cloudflare Web Analytics loader restricted to the official HTTPS app entry paths, with SPA tracking disabled.
- Added Privacy & Data Handling, including a readable local HTML page generated from the same Markdown source.

### Changed
- Reorganized README around first use, brewing workflows, targets, display options, devices, data, and operation; corrected outdated current-version and R2 compatibility wording.
- Aligned About, README, and privacy guidance with user-defined extraction goals and the distinction between local brew records and hosted visit analytics.

### Compatibility
- Schema v7, the storage key, backup format, brewing calculations, display preferences, device protocols, and chart-image export remain unchanged.
- Local and non-official app copies do not request the analytics script. Analytics is not a prerequisite for core app operation.

## [4.5.2] - 2026-10-26

### Added
- Added a saved chart-size choice: Fit to screen (default) or Large with vertical scrolling, in both split and integrated modes. Chart-image export is independent of this choice.
- Added an optional integrated layout showing Quick or Class inputs beside the corresponding chart, with shared 35:65, 40:60, and 45:55 input-to-chart ratios.
- Added Default / Compact input-area sizing for sufficiently wide screens with a fine pointer. Touch and narrow screens use the default size while retaining the saved preference.
- Added a Chart / Target Settings shortcut inside Chart Tools. It moves to the relevant Settings sections without opening them automatically.

### Changed
- Chart Tools and Class management now open or close by clicking their header text or empty space, with unboxed plus / minus indicators. Buttons inside the header retain their own actions and native keyboard controls remain available.
- Split mode remains the default. Quick and Class open their corresponding chart, including an empty Class; the chart can return to the corresponding input screen.
- Chart Tools groups guide, goal, student / attempt selection, and image copy / PNG / sharing controls. Collapsing it hides the controls while retaining the summary and full out-of-range warning.
- Reduced on-screen chart whitespace and used the available viewport height while retaining minimum readability. Short screens or expanded controls can still require scrolling.
- Moved class, student, and practice management into the Class context panel with a compact summary and expandable tabs; practice selection and creation are in the practice tab.
- Stabilized Settings width, scrolling, mode-selection spacing, and Quick / Class transitions. A selected display mode is applied when leaving Settings.
- Unified device-header space and mobile navigation-pill sizing, prevented the student Add button from wrapping, clarified storage and display guidance, and formatted HTML / CSS / JavaScript with LF line endings.

### Fixed
- Preserved native keyboard focus and Tab order after using the Chart / Target Settings shortcut; target and chart sections remain operable with Enter and Space.

### Compatibility
- Schema remains v7. Display mode, input-to-chart ratio, input size, and chart size are saved and backed up; older supported backups receive defaults. Earlier app versions may discard these new preferences.
- Brewing calculations, record interpretation, device protocols, measurement input ownership, and chart-image export remain unchanged. Screen layout changes do not change the exported chart geometry.
- A new integrated-mode selection requires at least a 1280 CSS-pixel viewport and 1200 pixels of workspace. A saved integrated mode is retained on resize, with a narrow-screen warning and an explicit return to split mode.
- This release includes the v4.5.1 internal navigation baseline, which was not published separately. Export a backup and close older app tabs before updating.

## [4.5.0] - 2026-10-25

### Added
- Added DiFluid R2 as an optional Web Bluetooth Device Profile alongside the existing HM Digital profile.
- Added PC-requested and device-initiated Single / Average measurement, Auto Single-to-Loop handling, and final TDS delivery to Quick or Class without automatically saving a record.
- Added an R2 settings popup from the header connection control, with device-confirmed Auto / Count, model / firmware information, and an accessible settings icon.
- Added R2-specific Windows / Android connection guidance, permission routes, and recovery steps while retaining the existing HM Digital help.

### Fixed
- Average completion now requires the final aggregate and complete progress; missing, damaged, or detectably inconsistent final data cannot reuse an earlier average.
- Changing Quick / Class, student, session, edit target, or manual TDS cancels result delivery. Sent measurements remain locked until device completion or explicit recovery; late results do not overwrite a new target.
- Measurement starts require matching mode / status pairs. The latest confirmed Count is checked immediately before PC command transmission.
- Delayed or incomplete measurements retain the previous TDS and offer explicit reconnection without automatic remeasurement.

### Changed
- R2 device Count and PC measurement Count are shared. Connection reads existing settings; Auto / Count writes occur only on an explicit user change.
- For device-origin Auto multi-measurement Single-to-Loop cycles, the app uses the last N received Loop readings, or the final Loop reading if fewer than N are available. Device Average results and other Single / Loop cycles retain their own final-result policies.
- R2 header and measurement feedback adapt to available width, keep progress and recovery guidance concise, and expose further detail through the existing settings popup.
- Valid numeric device readings can enter the TDS field outside the brewing-calculation interval. Existing calculation and saved-record checks remain separate.

### Compatibility
- The saved-data schema remains v7 with the existing storage key, backup identifier, Import resource budgets, and supported schema-v1 through schema-v7 migration.
- Existing brewing formulas, saved-record interpretation, chart / PNG behavior, and HM Digital adapter are retained. Live R2 connections, Auto / Count, and auxiliary readings are not added to brew records or backups.
- R2 requires a browser with Web Bluetooth support. Export a backup and close older app tabs before updating; retain the previous app and its pre-upgrade backup for rollback.

## [4.4.5] - 2026-10-23

### Added
- Added backup Import resource guards. Files larger than 32 MiB are rejected before reading; excessive text, collection size, total structure, or nesting is rejected after parsing without truncating the backup.

### Fixed
- Device Profile switches now ignore superseded asynchronous results, keeping runtime and saved profiles consistent when selection overlaps backup restoration, full reset, or a newer selection.
- Removed data-sized function-call spreads from record normalization and validation so large attempt collections do not fail at the JavaScript argument-count limit.
- Measurement controls now refresh immediately after a Device Profile change in Quick and Class, without requiring a reload. Existing connection and measurement contracts are retained.

### Changed
- Canonical normalization retains known Settings and Quick draft fields while discarding unrecognized properties. Existing legacy feedback migration and explicit known values are preserved.
- Shared saved-record iteration and measurement-control refresh, clarified selected local names, removed an unused state read, and documented mass-balance units, saved-retention ownership, and the existing HM Digital transport contract.

### Compatibility
- The saved-data schema remains **v7**. Supported schema-v1 through schema-v7 backups remain importable within the resource budgets; existing measurements, notes, feedback, acknowledgment, input modes, and retention snapshots retain their interpretation.
- Import validation is separate from browser storage capacity. Existing storage failure, recovery, conflict, and stale-tab handling remains in place.
- The calculation formulas, target classification, chart / PNG layout, browser storage key, backup format identifier, and HM Digital protocol remain unchanged. No R2 integration or runtime dependency is added.

## [4.4.4] - 2026-10-22

### Changed
- Reformatted inline JavaScript as an internal maintenance checkpoint before the v4.4.5 hardening changes. Structural equivalence and existing regression checks were verified separately.
- Preserved executable behavior, literal and template contents, comments, HTML / CSS, and the single-file distribution. This checkpoint was not published as a separate public release.

## [4.4.3] - 2026-09-25

### Added
- Added a shared brew-data sanity review for Quick and Class. Calculable but unusual records retain their existing values, target classification, and direction feedback while showing an input-review warning.
- Added record-level acknowledgment for intentionally entered outliers. Saved Quick and Class records can show `확인됨`; changes to brew data clear the acknowledgment, while note and instructor-feedback edits preserve it.
- Added permanent deletion for excluded students. The action removes the student from the excluded roster together with all session records, saved names, instructor feedback, and related chart / editing references after confirmation.
- Added a two-stage full app-data reset in Settings. It returns persistent user state and Measurement Device selection / UI visibility to defaults and disconnects the runtime device while retaining the app's built-in device profiles and measurement functions.
- Added inline TDS range guidance and accessible invalid-state reporting to Quick and Class.

### Fixed
- Added reset-generation coordination so stale tabs, queued writes, pending recovery data, primary / recovery snapshots, and lifecycle saves cannot restore data from before a full reset. Already-stale tabs cannot start a new reset or mutate persistent state.
- Early schema-v2 backups without `excludedStudents` now migrate correctly. Malformed v2 values remain rejected, and schema-v3-or-newer data retain strict `excludedStudents` validation.
- Backup Restore now closes an open Quick common-note editor before restored state is rendered, preventing a stale draft from overwriting restored content.
- Class automatic-estimate hints now refresh immediately after the liquid-retention setting changes, while edits of saved records continue to use the record's retained coefficient.
- Chart minor grid lines now render completely at the validator's maximum density.
- Backup filenames now use the Asia/Seoul calendar date while the JSON `exportedAt` timestamp remains UTC ISO.
- Stabilized Quick and narrow two-column Class layouts when calculation, sanity, TDS-range, and automatic-estimate messages change.

### Changed
- Valid TDS for a calculated brew result is now strictly **0 < TDS < 100%**. New or edited records outside that interval cannot be saved. Existing imported records retain their raw TDS but do not produce EY, dissolved solids, classification, feedback, or chart points; independently calculable Brew Ratio may still be shown.
- Sanity review remains separate from calculation validity. Calculable outliers can still be saved and charted, and acknowledgment records the user's confirmation without storing derived review reasons.
- Ordinary protected pending writes complete without a storage warning. Actionable failures, conflicts, stale-tab states, and damaged or newer data remain visible.
- Settings sections start collapsed, Class form actions appear before the sanity message, and custom Target Profile / Chart View Preset names no longer receive an extra user suffix.

### Compatibility
- Advanced the saved-data schema to **v7**. Every saved Quick and Class record carries a strict boolean `sanityAcknowledged` field; `needsReview` and reason codes remain derived and are not stored.
- Supported schema-v1 through schema-v6 data remain importable and receive `sanityAcknowledged: false` without changing their historical measurements, record provenance, notes, feedback, retention value, or measurement-device state.
- Current schema-v7 representation is validated strictly. Missing or non-boolean acknowledgment fields are rejected rather than silently repaired.
- The legacy browser storage key `coffeeBrewControlClassroomV2` and backup format identifier `coffee-brew-control-backup` remain unchanged. Export a backup and close older app tabs before upgrading. Schema-v7 backups are not intended for older app versions.

## [4.4.2] - 2026-09-22

### Added
- Added automatic Brew water estimation in Quick and Class when Brew water is blank and Dose, Beverage mass, and TDS are provided. Estimated Brew Ratio is identified as an estimate.
- Added optional per-attempt Quick notes using the saved-card editor pattern from Class instructor feedback, with save / cancel and Ctrl/⌘+Enter / Esc shortcuts.
- Added Copyright & Usage terms clarifying free use of the hosted application and unmodified locally run copies distributed by the copyright holder, permitted use, export, and sharing of users’ own brewing records, backup JSON files, and chart images, restrictions on reuse of protected project materials, and the exclusion of brewing principles and third-party materials from ownership claims.

### Fixed
- Individual Quick attempt deletion now asks for confirmation before removing the record, matching Class record deletion.

### Changed
- Quick and Class records and chart details show whether Beverage or Brew water was estimated and the liquid-retention value used. Quick notes appear in chart tooltips and details.
- Shared raw-input reading, bidirectional mass calculation, and calculation-source presentation within the existing single-file app. The Quick measurement form does not add a note field.
- The forward automatic Beverage formula, default liquid retention of 2.1, existing manual-input policy, chart out-of-range notice, measurement transport, and PNG layout remain unchanged.

### Compatibility
- Advanced the saved-data schema to v6 to preserve each record’s Brew water input mode and Quick attempt note. Supported schema-v5 and earlier data remain importable; existing records retain their previous water-input interpretation and liquid-retention value.
- Automatic estimates remain derived values: blank raw inputs and the saved liquid-retention value are retained during editing and JSON backup / restore.
- The browser storage key and backup format identifier remain unchanged. Export a backup and close older app tabs before upgrading. Schema-v6 backups are not intended for older app versions.

## [4.4.1] - 2026-09-20

### Added
- Added editing for saved **Quick** attempts through the existing input form. Saving an edit preserves the attempt ID, order, and liquid-retention value; saving or cancelling restores the previous LIVE input.
- Added a per-record **liquid-retention snapshot** for Quick and Class so later Calculation Settings changes do not recalculate saved automatic Beverage values.

### Fixed
- Storage recovery now validates available candidates and falls back to a valid copy instead of silently replacing unreadable data with defaults. Recovery preserves the previous committed snapshot; unreadable or newer-schema data stops automatic writes.
- Added stale-tab write detection and serialized same-origin writes through Web Locks when available. Conflicting tabs keep their in-memory data available for JSON export instead of overwriting another tab.
- Class input ownership now follows student, class, practice-session, record-edit, and backup-restore transitions. Deleting the record being edited clears the obsolete form values.
- Delayed measurement results no longer replace input after its owner changes, an input reset, or a subsequent manual TDS edit. Returning to the same student does not reactivate an earlier measurement.
- Unsubmitted instructor feedback survives same-context Class re-rendering. Editing an existing Class record preserves chart-filter selections.
- Backup import now checks known data structures, record IDs, chart settings, and preset settings while retaining supported legacy migrations and historical roster records. Imported IDs are assigned through DOM properties rather than inserted into HTML attributes.
- File-save and JSON-copy actions now create a fresh export snapshot at the start of each operation. Backup restore also clears previous form, editing, and pending-measurement contexts.

### Changed
- Separated input updates and persistence from rendering, and extracted calculation functions with explicit settings. Quick input updates no longer rebuild the entire saved-attempt list.
- Shared Quick / Class measurement controls and separated Settings and Chart rendering responsibilities within the existing single-file app. Unapplied calculation, target, and chart fields survive unrelated Settings refreshes.
- Coalesced Quick input chart-render requests and flushes pending chart rendering before PNG generation. Added label associations for numeric fields and a chart description without changing the existing layout.
- The automatic Beverage formula, default liquid retention of **2.1**, manual-input policy, chart out-of-range notice, measurement transport, and PNG layout remain unchanged.

### Compatibility
- Advanced the saved-data schema to **v5**. Supported schema-v4 and earlier browser data / backups remain importable. Existing records receive the dataset's liquid-retention value during migration to preserve the results shown immediately before migration; this does not reconstruct an unknown historical coefficient.
- The legacy browser storage key **coffeeBrewControlClassroomV2** and backup format identifier **coffee-brew-control-backup** remain unchanged. Local / session storage and the memory fallback are retained.
- Web Locks strengthen coordination between participating v4.4.1 tabs. Environments without Web Locks retain change detection but do not guarantee protection against simultaneous writes. Older app tabs do not participate in the new coordination.
- Export a backup and close older app tabs before upgrading in the same browser storage context. Schema-v5 backups are not intended for older app versions; retain a pre-upgrade backup for rollback.

## [4.4.0] - 2026-09-19

### Added
- Added a reusable **Measurement Device** framework with persistent Device Profile settings and runtime-only connection / measurement state.
- Added direct HM Digital **BTR-1000 / RCM-1000BT** support through Web Serial and Bluetooth Classic SPP.
- Added **Measure TDS** actions to Quick and Class. Successful measurements enter TDS through the existing input path; measurements never auto-save a Quick attempt or Class record.
- Added a global header device control for connection state and reconnect, plus a Settings connection test that opens the device connection without sending a measurement command.
- Added platform-specific troubleshooting for Windows Bluetooth pairing and Android Chrome **Nearby devices** permission.
- Added normalized runtime measurement results for TDS, Brix, Celsius / Fahrenheit temperature, refractive index, and the original raw device response for future device-aware features.

### Changed
- Existing TDS remains visible while a measurement is pending and is replaced only after a successful new TDS result.
- Air, Unstable, Hi Range, timeout, unknown-response, and connection-loss cases preserve the previous TDS value.
- Measurement feedback now follows the current attempt and connection lifecycle: a new measurement replaces the previous result message, connection loss takes priority over an older measurement message, and a confirmed reconnect returns the measurement UI to standby.
- Connection and measurement state are handled independently, with guarded cleanup, duplicate-event protection, stale-port recovery, delayed-result rejection, and reconnect support after device sleep or link loss.
- Device Profile display names are used when a browser cannot expose the physical Bluetooth device name; the internal model can also accept a device-provided display name when available.

### Compatibility
- Advanced the saved-data schema to **v4**.
- Existing schema-v3 browser data and backups remain importable. Measurement-device settings default to **no device + controls hidden** for migrated data.
- The selected Device Profile and measurement-control visibility are included in normal app persistence and JSON backup; live serial-port objects and runtime measurement results are not persisted.
- The legacy browser storage key `coffeeBrewControlClassroomV2` and backup format identifier `coffee-brew-control-backup` remain unchanged.
- HM Digital device integration was validated with Chrome on Windows, a Windows PC using a Bluetooth dongle, and Android Chrome. Windows may require Bluetooth pairing before the device appears; Android Chrome may require **Nearby devices** permission.

## [4.3.6] - 2026-09-18

### Added
- Added an independent **Calculation Settings** section for the global liquid-retention coefficient, including the automatic Beverage mass-balance formula and an explanation of where the coefficient is applied.
- Split the former combined Brewing Profile into **Target Profiles** and **Chart View Presets**, each with built-in presets, load controls, and collapsible management for save / overwrite / delete.
- Added per-student master toggles to the Class chart filter, with aligned student-name columns and attempt checkboxes, so all attempts for one student can be selected or hidden at once while preserving mixed-selection state.
- Made the **Coffee Brewing Control** header title return to Quick as the app's home action.

### Changed
- Quick results now show the extraction target and Quick goal as separate reference lines; goal coordinates are no longer repeated inside the main feedback text.
- Quick goal feedback separates remaining ΔEY / ΔTDS from the adjustment recommendation for easier reading.
- Stabilized layout around Quick goal creation / removal and chart out-of-range warnings to reduce vertical shifts.
- Improved chart-header handling for long experiment / class / session names and constrained the mobile navigation pill to its content width while keeping its existing position.
- Renamed the UI setting from **absorption coefficient** to **Liquid retention** terminology while retaining the same calculation role.

### Compatibility
- Advanced the saved-data schema to **v3**.
- Existing schema-v2 browser data and backups remain importable. Legacy custom Brewing Profiles are migrated into same-named Target Profiles and Chart View Presets.
- During migration, the currently applied liquid-retention value is preserved as the global calculation setting; liquid retention is no longer stored per preset.
- The legacy browser storage key `coffeeBrewControlClassroomV2` and backup format identifier `coffee-brew-control-backup` remain unchanged for compatibility.

### Deferred / Future considerations — not implemented in v4.3.6
- Add stored-data size and record-count summaries in Settings if long-term classroom datasets make this useful.
- Move the `StorageAdapter` persistence backend from localStorage to IndexedDB if real-world data volume approaches localStorage limits; future native/app ports can use an appropriate backend such as SQLite.

## [4.3.5] - 2026-09-17

### Changed
- Renamed user-facing terminology from **Coffee Brew Control** to **Coffee Brewing Control**.
- Renamed the chart title from **Brew Control Chart** to **Brewing Control Chart**.
- Refined chart zoning into semantic **Strong / Weak** and **Under / Over** overlay bands; corner regions inherit both meanings.
- Kept the target area in muted sage and brew-ratio lines in smoky plum to further distinguish the visual design from published SCA chart artwork.
- Corrected automatic beverage-mass estimation and Brew Ratio guide lines to use the full mass-balance relationship, and updated the Classic Filter liquid-retention default from 2.0 to 2.1.
- Corrected the visible HTML document version.

### Added
- In-app **About & References** dialog.
- In-app **Changelog** dialog.
- Visible app version information in Settings.
- Public-facing explanation of the tool's educational / repeated-test purpose, configurable ranges, beverage-mass estimation, local storage, references, and non-affiliation with SCA.

### Compatibility
- Existing browser data continues to use the legacy storage key `coffeeBrewControlClassroomV2`.
- Existing backup files remain importable because the legacy backup format identifier `coffee-brew-control-backup` is retained.

## [4.3.4.1]

### Added
- Current class, practice session, and selected-record count in the Class chart filter context.
- Reversible roster exclusion with an excluded-student list and restore action.

### Preserved
- Historical records and instructor feedback remain linked to the same student ID when a student is excluded and later restored.

## [4.3.4]

### Added
- Reusable Class practice sessions.
- Session create, switch, rename, and delete workflow.
- Per-session student records starting again at attempt 1.
- Session-aware Class charts and image-export titles.
- Schema v2 class/session data structure and automatic migration from earlier v4.3.x records.

### Changed
- Class record clearing applies to the current practice session only.
- Roster removal became non-destructive exclusion so historical records remain available.

## [4.3.3]

### Added
- Quick experiment name and common note.
- ΔEY / ΔTDS comparison in Quick and Class tooltips.
- Desktop coordinate preview for Quick target placement.
- Mobile tap interaction for points and target points.
- PNG chart generation with copy, save, share, and in-app preview fallback.

### Changed
- Chart exports include saved paths, live point, target point, goal guide, and legend while excluding transient hover / selection UI.

## [4.3.2]

### Changed
- Separated the current Quick input from committed saved attempts on the chart.
- Added a distinct live point and saved-to-live preview path.
- Quick main feedback now follows the current live input.
- Saved attempts receive their own dynamically recalculated target feedback.
- Goal guidance uses the live point first, then the latest saved point when no valid live point exists.

## [4.3.1]

### Changed
- Strengthened full-data export for restricted browser environments.
- Added visible JSON backup preview and clipboard-copy fallback.
- Uses the File System Access API for OS-level save dialogs when available.
- Avoids claiming a download succeeded when the browser may have blocked it.

## [4.3]

### Added
- Full JSON export / import for classes, students, records, instructor feedback, Quick data, profiles, and chart settings.
- `schemaVersion` for saved data.
- Storage-adapter layer to isolate persistence from calculation and UI logic.

### Changed
- Moved class administration into Settings.
- Replaced browser `prompt()` / `confirm()` dependencies with in-app dialogs.
- Preserved migration from earlier v4.x browser data.

## [4.2]

### Added
- Saved Quick attempts with automatic numbering and connected chart paths.
- Interactive Quick target point and target-relative guidance.
- Independent Quick and Class automatic-feedback controls.
- Multiple classes with independent rosters, records, notes, and instructor feedback.
- Migration from the earlier single-class structure.

## [4]

### Added
- Dynamic target classification badges for saved Class records.
- Separate brew notes and instructor feedback.
- Direction arrows between sequential Class attempts.
- Configurable extraction-yield and TDS chart bounds and tick intervals.
- Configurable brew-ratio line range and interval.
- Built-in **Classic Filter** profile plus user-defined brewing profiles.

### Changed
- Reorganized Settings into collapsible sections.
- Saved records are reinterpreted dynamically when target settings change.

## [3]

### Added
- Target-relative **STRONG / WEAK / UNDER / OVER** chart regions and combined corner regions.
- Hover details for chart points while retaining click-based detail view.

### Changed
- Replaced the earlier **Golden Cup** chart label with the neutral **TARGET** label while keeping the target range configurable.

## [2]

### Added
- Separate **Quick** and **Class** workflows.
- Student roster management and sequential per-student brew records.
- Brew notes and simple target-direction feedback.
- Class chart filtering and connected attempt paths.
- Browser-local persistence.

## Initial prototype

### Added
- Single-file browser calculator for dose, brew water, beverage mass, TDS, extraction yield, dissolved solids, and brew ratio.
- Automatic beverage-mass estimation when beverage mass is left blank, using a configurable liquid-retention value.
- Live brewing-control chart with extraction yield on the X-axis, TDS on the Y-axis, a default reference area, and brew-ratio lines.
