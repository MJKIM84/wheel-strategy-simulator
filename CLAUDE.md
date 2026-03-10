# Wheel Strategy Simulator

## Project Overview
SoFi 중심 Covered Call + Cash-Secured Put (Wheel) 옵션 전략 시뮬레이터.
Monte Carlo 분석으로 4가지 투자 전략을 비교하는 인터랙티브 웹 대시보드.

## Tech Stack
- **Frontend**: Single-file HTML with inline React 18 + Babel standalone
- **Charts**: Recharts 2.12 (CDN)
- **Fonts**: JetBrains Mono (Google Fonts CDN)
- **Deploy**: GitHub Pages (static, no build step)

## Architecture
```
index.html          ← 전체 앱 (단일 파일, CDN 기반)
README.md           ← 프로젝트 문서
CLAUDE.md           ← 이 파일 (Claude Code 컨텍스트)
package.json        ← 로컬 dev server용
.github/workflows/  ← GitHub Pages 자동 배포
```

## 4 Strategies Compared
1. **Wheel (After Tax)**: CC + CSP 프리미엄 수입, 배정 시 매수/매도, 세금 반영
2. **Tax-Free**: 동일 전략, 비과세 계좌 가정
3. **RE + Dividend**: 부동산 $700K (연 4% 상승 + 4% 임대수익) + 배당주 $300K
4. **Buy & Hold**: 단순 매수 후 보유

## Simulation Engine Key Params
- Jump-diffusion model (Merton): 정규분포 + 포아송 점프
- SoFi: 현재가 $18.90, 기본 목표 $60, 변동성 조정 +30%
- GOOGL: 현재가 $298, 목표 $500 (현재 비활성: ratio=0)
- 횡보장 3개월+ 시 스트라이크 타이트닝
- 프리미엄은 변동성 기반 동적 계산

## Key Files
- `index.html`: 모든 코드 포함 (시뮬레이션 엔진 + UI + 차트)
  - `runSim(params)` → 단일 시뮬레이션 실행, history 배열 반환
  - `runMC(params, runs)` → 몬테카를로 N회 실행, 통계 반환
  - `App()` → 메인 React 컴포넌트 (탭: Growth/Price/Premiums/MC/Ledger)

## Commands
```bash
npm start          # 로컬 개발 서버 (localhost:3000)
npm run deploy     # GitHub Pages 배포 (gh-pages)
```

## Development Notes
- Babel standalone으로 JSX 런타임 변환 → 빌드 불필요
- 파라미터 변경 시 useMemo로 시뮬레이션 자동 재실행
- Re-Roll 버튼: simKey 증가 → 새로운 랜덤 시드로 재시뮬레이션
- 모든 CDN은 cdnjs.cloudflare.com 사용

## Future Improvements
- [ ] Sharpe Ratio, Max Drawdown 등 리스크 지표 추가
- [ ] GOOGL 병행 투자 시나리오 활성화
- [ ] 시뮬레이션 결과 CSV/PDF 내보내기
- [ ] 다크/라이트 테마 토글
- [ ] 모바일 반응형 개선
- [ ] URL params로 설정 공유 기능
