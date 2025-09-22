# 김개발 포트폴리오 (Single Page)

이 저장소는 `index.html`, `style.css`, `script.js`로 구성된 정적 싱글 페이지 포트폴리오 사이트입니다. 반응형 UI, 스무스 스크롤, 섹션별 활성 내비게이션, 타이핑 효과, 스킬 바 애니메이션, 스크롤 인뷰 애니메이션, 간단한 폼 검증을 제공합니다.

## 데모 실행
- 방법 1: 파일 직접 열기
  - `index.html`을 브라우저로 열면 됩니다.
- 방법 2: 로컬 서버 권장
  - VS Code의 Live Server, `python -m http.server`, `npx serve` 등 임의의 정적 서버로 프로젝트 루트를 서빙하세요.

## 폴더 구조
```
/Users/muse/Documents/test/
├── index.html   # 마크업 구조 및 섹션 구성 (Home/About/Skills/Experience/Projects/Contact)
├── style.css    # 전체 스타일, 반응형 디자인, 애니메이션, 컴포넌트 스타일
└── script.js    # 내비 토글, 스무스 스크롤, 섹션 활성화, 타이핑/스킬바/스크롤 애니메이션, 폼 검증
```

## 주요 섹션 구성 (`index.html`)
- 헤더/내비게이션: 고정 헤더, 햄버거 메뉴(모바일), 앵커 스크롤
- 홈(Hero): 이름, 멀티 타이핑 텍스트(`.typing-text`), CTA 버튼
- 소개(About): 간단 소개 및 통계 카드
- 기술(Skills): 카테고리별 스킬 바(IntersectionObserver 기반 애니메이션)
- 경력(Experience): 타임라인 레이아웃
- 프로젝트(Projects): 카드형 프로젝트 목록
- 연락(Contact): 연락처 정보 + 폼(간단한 프론트 검증)
- 푸터(Footer)

## 상호작용/기능 (`script.js`)
- 모바일 메뉴 토글: `.hamburger` 클릭 시 `.nav-menu.active` 토글
- 스무스 스크롤: 내비 링크 클릭 시 헤더 높이를 고려한 스크롤 이동
- 헤더 스타일 변경: 스크롤 위치에 따라 배경/그림자 조정
- 섹션 활성화: 현재 뷰포트 섹션의 내비 링크에 `active` 클래스 적용
- 스킬 바 애니메이션: IntersectionObserver로 `data-width`를 읽어 점진적 채움
- 타이핑 효과:
  - 단일 텍스트: `typeWriter(element, text, speed)`
  - 멀티 텍스트: `multiTypeWriter(element, texts, typeSpeed, deleteSpeed, pauseTime)`
- 스크롤 인뷰 애니메이션: `.timeline-item`, `.project-card`, `.skill-category` 페이드/이동 효과
- 폼 검증: 이름/이메일/제목/메시지 필수, 이메일 정규식 체크 후 알림 및 초기화
- 접근성 보조: ESC로 모바일 메뉴 닫기, 외부 클릭/리사이즈 시 메뉴 닫기
- 성능: `debounce/throttle` 유틸과 초기 `body` 페이드인 처리

## 스타일 하이라이트 (`style.css`)
- 전역 리셋, 타이포그래피, 컨테이너 레이아웃
- 고정 헤더 + 글래스모피즘 느낌의 배경/블러
- 히어로 그라데이션, 이름 텍스트 그라데이션, 커서 깜박임
- 버튼 변형/호버 그림자, 카드 호버 상승 효과
- 타임라인 세로축과 마커, 짝/홀수 정렬 변경, 모바일 단일 컬럼
- 스킬 바 그라데이션 + `fillBar` 키프레임
- 반응형 브레이크포인트: 768px, 480px

## 커스터마이징 가이드
- 히어로 타이핑 문구: `index.html`의 `.typing-text`에 `data-texts` JSON 배열 수정
- 스킬 레벨: 각 `.skill-progress`의 `data-width` 값을 퍼센트로 조정
- 색상/테마: `style.css`에서 버튼/그라데이션/포인트 컬러(`#3498db`, `#2ecc71` 등) 변경
- 섹션 추가: `index.html`에 새 `section#id` 추가 후 내비에 앵커 링크 생성

## 개발 팁
- 고정 헤더 오프셋: 스크롤 위치 계산에서 `header.offsetHeight`를 고려합니다.
- 네이티브 스무스 스크롤: `html { scroll-behavior: smooth; }` + JS 보정
- IntersectionObserver 지원 범위를 고려해 매우 구형 브라우저는 폴리필이 필요할 수 있습니다.

## 브라우저 지원
- 최신 크롬/엣지/사파리/파이어폭스에서 정상 동작을 목표로 합니다.
- iOS/안드로이드 모바일 뷰를 위한 반응형 스타일 포함.

## 라이선스
- MIT. 필요 시 프로젝트 요구사항에 맞게 변경하세요.
