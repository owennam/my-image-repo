---
type: documentation
category:
  - JSHA
  - newsletter
  - tech-spec
status:
  - active
tags:
  - "#JSHA"
  - "#newsletter"
  - "#technical"
  - "#documentation"
created: 2025-09-28
modified: 2025-09-28
authors: 남승균
CMDS: "[[📚 340 Newsletter]]"
중요도: "****"
---

# JSHA Newsletter 기술 명세서

## 📋 프로젝트 개요
- **프로젝트명**: JSHA 뉴스레터 자동 생성 시스템
- **주요 파일**:
  - `jsha-newsletter-agent.py` - 뉴스레터 생성 엔진
  - `create_rich_newsletter.py` - 풍부한 콘텐츠 생성기
- **파일 크기**: Python 스크립트 ~15KB, 생성된 HTML ~25KB
- **타입**: Newsletter Generation System
- **용도**: 의료진 대상 전문 뉴스레터 자동 생성

## 🛠 기술 스택

### 1. 백엔드 (Python 3.8+)
- **Python 표준 라이브러리**
  - `pathlib` - 크로스 플랫폼 파일 경로 처리
  - `datetime` - 날짜/시간 관리
  - `json` - 설정 데이터 처리
  - `importlib.util` - 동적 모듈 로딩
- **타입 힌팅**
  - `typing.Dict`, `typing.List`, `typing.Optional`
  - Python 3.8+ 호환성

### 2. 프론트엔드 (HTML5 + CSS3)
- **HTML5**
  - Semantic HTML 요소 사용
  - UTF-8 인코딩 지원
  - 반응형 뷰포트 메타 태그
  - 이메일 클라이언트 호환성 고려
- **CSS3**
  - Flexbox Layout
  - CSS Grid Layout
  - CSS Custom Properties (변수)
  - Media Queries (반응형 디자인)
  - Box Shadow, Border Radius
  - 이메일 클라이언트 제한 고려

### 3. 템플릿 시스템
- **Python String Formatting**
  - f-string 문법 활용
  - 템플릿 변수 치환
  - 조건부 섹션 렌더링

## 🎨 디자인 시스템

### 색상 팔레트
```css
/* JSHA 브랜드 컬러 */
--primary: #2c5aa0        /* JSHA 블루 */
--secondary: #666         /* 그레이 텍스트 */
--accent: #ffc107         /* 강조 노란색 */
--light: #f8f9fa          /* 배경 그레이 */
--dark: #333              /* 진한 텍스트 */
--warning: #fff3cd        /* 하이라이트 배경 */
--border: #eee            /* 보더 색상 */
```

### 타이포그래피
- **주 폰트**: Malgun Gothic (한글 최적화)
- **폴백 폰트**: Arial, sans-serif
- **폰트 크기**:
  - 제목: 2.5em, 1.8em
  - 본문: 1.1em
  - 캡션: 0.9em
- **줄 간격**: 1.6 (가독성 최적화)

### 레이아웃 시스템
- **Container 최대 너비**: 800px (이메일 표준)
- **Section 패딩**: 25px
- **카드 간격**: 40px
- **Border Radius**: 5px (모던한 느낌)

## ⚡ 구현된 기능

### 1. 뉴스레터 생성 엔진 (`JSHANewsletterAgent`)
- **이중 포맷 출력**: MD(아카이브용) + HTML(발행용)
- **모듈식 섹션 관리**: 의료 정보, 건강 팁, 공지사항, 케이스 스터디, 연구 자료
- **YAML 프론트매터 자동 생성**: Obsidian 호환
- **메타데이터 관리**: 작성자, 날짜, 태그, 중요도 등

### 2. 콘텐츠 관리 시스템
- **구조화된 입력**: 딕셔너리 기반 콘텐츠 입력
- **조건부 렌더링**: 비어있는 섹션 자동 제외
- **기여자 정보 관리**: 자료 제공자, 감수자, 참고문헌
- **템플릿 커스터마이징**: 쉬운 브랜딩 변경

### 3. 파일 관리
- **자동 디렉토리 생성**: 출력 폴더 자동 생성
- **UTF-8 인코딩**: 한글 완벽 지원
- **크로스 플랫폼**: Windows, macOS, Linux 지원

## 📱 반응형 디자인

### 이메일 클라이언트 최적화
- **Outlook 호환성**: 테이블 기반 레이아웃 고려
- **Gmail 최적화**: 인라인 스타일 사용
- **모바일 이메일**: 최소 글꼴 크기 준수
- **다크 모드 지원**: 배경색, 텍스트 색상 고려

### 반응형 breakpoints
- **모바일**: < 600px
- **태블릿**: 600px - 800px
- **데스크톱**: > 800px

## 🔧 브라우저 및 클라이언트 호환성

### 이메일 클라이언트 지원
- **웹메일**: Gmail, Outlook.com, Yahoo Mail
- **데스크톱**: Outlook 2016+, Apple Mail, Thunderbird
- **모바일**: iOS Mail, Android Gmail

### 웹 브라우저 지원 (아카이브 뷰)
- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

## 📊 성능 최적화

### 적용된 최적화 기법
1. **인라인 CSS**: 이메일 클라이언트 호환성
2. **이미지 최적화**: 인라인 SVG 사용 권장
3. **단일 파일 구조**: HTTP 요청 최소화
4. **경량 마크업**: 불필요한 태그 제거
5. **UTF-8 최적화**: 한글 처리 최적화

### 성능 메트릭 (목표)
- **파일 크기**: < 30KB (이미지 제외)
- **로딩 시간**: < 2초
- **렌더링 시간**: < 1초
- **이메일 전송 시간**: < 30초

## 🏗 코드 구조

### Python 모듈 구조
```
jsha-newsletter-agent.py
├── JSHANewsletterAgent (클래스)
│   ├── __init__() - 초기화 및 설정
│   ├── generate_newsletter() - 메인 생성 함수
│   ├── _generate_markdown_content() - MD 생성
│   ├── _generate_html_content() - HTML 생성
│   ├── _convert_md_to_html_simple() - 간단 변환
│   └── save_newsletter() - 파일 저장
└── create_sample_newsletter() - 샘플 생성
```

### HTML 구조 (생성된 뉴스레터)
```html
<!DOCTYPE html>
├── <head>
│   ├── 메타 태그 (UTF-8, viewport)
│   └── <style> (인라인 CSS)
├── <body>
│   ├── .header (제목, 부제목)
│   ├── .greeting (인사말)
│   ├── .section (의료 정보)
│   ├── .section (케이스 스터디)
│   ├── .section (최신 연구)
│   ├── .section (건강 팁)
│   ├── .section (공지사항)
│   ├── .publisher (발행인)
│   ├── .contributors (기여자)
│   └── .footer (저작권, 면책사항)
```

### Markdown 구조 (아카이브용)
```markdown
---
YAML 프론트매터 (Obsidian 메타데이터)
---
# 제목
## 섹션들 (이모지 포함)
### 하위 섹션들
기여자 정보
푸터 정보
```

## 🌐 다국어 지원 (i18n)

### 현재 지원
- **언어**: 한국어 (ko-KR)
- **문자 인코딩**: UTF-8
- **날짜 형식**: YYYY-MM-DD (ISO 8601)

### 향후 확장 가능
- 영어 (en-US) 템플릿 추가
- 일본어 (ja-JP) 의료용어 지원
- 다국어 설정 파일 분리

## 📦 의존성 관리

### 외부 의존성
- **Python 표준 라이브러리만 사용**: 제로 디펜던시
- **설치 불필요**: 즉시 실행 가능
- **크로스 플랫폼**: OS 독립적

### 내부 의존성
- `pathlib`: 파일 경로 처리
- `datetime`: 날짜 처리
- `typing`: 타입 힌팅
- `json`: 설정 관리

## 🔍 SEO 및 접근성

### SEO 최적화 (웹 아카이브용)
- Semantic HTML 구조
- 명확한 제목 계층 (h1 > h2 > h3)
- 메타 태그 완전 구성
- Open Graph 태그 (향후 추가 예정)

### 접근성 (WCAG 2.1 AA)
- 색상 대비율 4.5:1 이상
- 명확한 폰트 크기 (최소 16px)
- 의미 있는 링크 텍스트
- 구조적 마크업

## 📝 특별 기능

### 1. YAML 프론트매터 자동 생성
- Obsidian 호환 메타데이터
- CMDS 카테고리 자동 분류
- 태그 시스템 연동
- 중요도 등급 설정

### 2. 이중 포맷 출력
- **MD**: 옵시디언 보관용, 검색 최적화
- **HTML**: 이메일 발송용, 시각적 최적화

### 3. 콘텐츠 모듈화
- 섹션별 독립적 관리
- 조건부 렌더링
- 재사용 가능한 템플릿

### 4. 한글 최적화
- UTF-8 완벽 지원
- 한글 폰트 우선순위
- 줄바꿈 최적화

## 🚀 배포 및 사용

### 로컬 실행
```bash
# 기본 샘플 생성
python jsha-newsletter-agent.py

# 풍부한 콘텐츠 생성
python create_rich_newsletter.py
```

### 통합 환경
- **Obsidian 연동**: 340 Newsletter 폴더 자동 저장
- **이메일 시스템**: HTML 파일 직접 복사 가능
- **웹 게시**: 정적 호스팅 즉시 가능

## 💡 향후 개선 계획

### 단기 계획 (1개월 내)
1. **이미지 처리 기능** 추가
2. **템플릿 다양화** (계절별, 주제별)
3. **자동 스케줄링** 기능
4. **이메일 발송 API** 연동

### 중기 계획 (3개월 내)
1. **웹 인터페이스** 개발 (Flask/FastAPI)
2. **구독자 관리 시스템**
3. **분석 대시보드** (오픈율, 클릭률)
4. **A/B 테스트** 기능

### 장기 계획 (6개월 내)
1. **AI 콘텐츠 생성** (GPT API 연동)
2. **다국어 완전 지원**
3. **모바일 앱** 연동
4. **CRM 시스템** 통합

## 🔒 보안 및 개인정보

### 데이터 보호
- **로컬 파일 처리**: 외부 서버 전송 없음
- **개인정보 최소화**: 필요한 정보만 수집
- **UTF-8 안전 처리**: 인코딩 오류 방지

### 향후 보안 강화
- **이메일 암호화** 지원
- **구독자 정보 암호화**
- **GDPR 준수** 기능

---

## 📄 라이선스
이 시스템은 JSHA 뉴스레터 제작 전용으로 개발되었습니다.

## 🔗 관련 파일
- `jsha-newsletter-agent.py` - 메인 생성 엔진
- `create_rich_newsletter.py` - 콘텐츠 생성기
- `JSHA Newsletter 형식.md` - 원본 템플릿
- `10월 0주 JSHA 뉴스레터.md` - 생성된 MD 파일
- `10월 0주 JSHA 뉴스레터.html` - 생성된 HTML 파일

## 📊 버전 관리
- **v1.0**: 기본 생성 기능
- **v1.1**: 풍부한 콘텐츠 지원
- **v1.2**: (예정) 이미지 처리 기능
- **v2.0**: (예정) 웹 인터페이스