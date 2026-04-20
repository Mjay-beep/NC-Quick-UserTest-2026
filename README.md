# SKT 통합 채널 UT 프로토타입

시나리오 기반 Task 수행 UT용 Low-fi 프로토타입 3종 (A/B/C안)

## 파일 구조

```
.
├── index.html      # 컨셉 선택 런처
├── a.html          # A안 - Effortless Control
├── b.html          # B안 - Effortless Value Discovery
├── c.html          # C안 - Effortless Flow
└── vercel.json     # Vercel 배포 설정
```

각 HTML은 외부 리소스 없는 완전 독립형 단일 파일입니다.

## 로컬 확인

별도 빌드/서버 불필요. `index.html`을 브라우저로 열면 됩니다.

더 정확한 확인을 위해 간단한 로컬 서버로 띄우려면:

```bash
# Python 3
python3 -m http.server 8000

# Node.js (npx)
npx serve .
```

## Vercel 배포

### 방법 1. GitHub 연동 (권장)

1. 이 폴더의 파일들을 GitHub 리포지토리에 푸시
2. [vercel.com](https://vercel.com) → **Add New Project** → GitHub 리포 선택
3. Framework Preset: **Other** (자동 감지됨)
4. Build/Output 설정은 비워두거나 기본값 유지 (정적 파일이므로 빌드 불필요)
5. **Deploy** 클릭

푸시할 때마다 자동 재배포됩니다.

### 방법 2. Vercel CLI

```bash
npm i -g vercel
cd skt-ut
vercel          # 첫 배포 (미리보기)
vercel --prod   # 프로덕션 배포
```

### 배포 후 URL 구조

- `https://<프로젝트>.vercel.app/` → 컨셉 선택 런처
- `https://<프로젝트>.vercel.app/a` → A안
- `https://<프로젝트>.vercel.app/b` → B안
- `https://<프로젝트>.vercel.app/c` → C안

`vercel.json`의 `cleanUrls: true` 설정으로 `.html` 확장자가 생략됩니다.

## UT 진행 시

- **피험자별 컨셉 제시 순서는 랜덤화**합니다.
- 각 프로토타입은 시나리오 1(요금제 변경) / 시나리오 2(미납 납부) 선택 화면부터 시작합니다.
- 상단 UT 배너의 "다른 컨셉으로" 드롭다운 또는 "시나리오 재시작" 버튼을 사용합니다.
- `localStorage`/`sessionStorage` 미사용. 새로고침 시 시나리오 선택부터 재시작됩니다 (UT에서 오히려 자연스러움).

## 공통 프로토타입 데이터

| 항목 | 값 |
|------|-----|
| 페르소나 | 지훈 (SILVER) |
| 현재 요금제 | T 프리미엄 · 월 54,500원 · 50GB |
| 추천 요금제 | 다이렉트 5G 76 · 월 48,500원(선택약정 24,700원) · 80GB |
| 실시간 잔여 | 62GB |
| 미납 금액 | 3월분 63,200원 |
