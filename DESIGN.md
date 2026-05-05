# Design System

## Retro & Vintage Design Guide
> 영감: 1970s–90s 그래픽 디자인, Y2K, 아날로그 인쇄, 픽셀 아트

---

## 1. Color System

### Palette — Vintage Warm
| Token | Value | Usage |
|-------|-------|-------|
| `--color-cream` | `#F5F0E8` | 기본 배경 (누렇게 바랜 종이) |
| `--color-paper` | `#EDE6D3` | 카드, 패널 배경 |
| `--color-ink` | `#1C1917` | 본문 텍스트 |
| `--color-primary` | `#C0392B` | 강조색 (복고 레드) |
| `--color-accent` | `#E67E22` | 보조 강조 (번트 오렌지) |
| `--color-teal` | `#2A6B6B` | 포인트 (청록 인쇄색) |
| `--color-mustard` | `#D4A017` | 하이라이트 (머스타드 옐로) |
| `--color-border` | `#1C1917` | 굵은 검정 테두리 |

### 복고 색상 규칙
- 밝은 배경(크림/페이퍼)을 기본으로 — 흰색 `#FFFFFF`는 사용하지 않음
- 채도를 낮추고 노란 기(warmth)를 더해 바랜 느낌 연출
- 최대 3~4색 팔레트 유지 (옛날 인쇄 잉크 한계 재현)

```css
:root {
  --color-cream:   #F5F0E8;
  --color-paper:   #EDE6D3;
  --color-ink:     #1C1917;
  --color-primary: #C0392B;
  --color-accent:  #E67E22;
  --color-teal:    #2A6B6B;
  --color-mustard: #D4A017;
  --color-border:  #1C1917;
}
```

---

## 2. Typography

### 복고 폰트 스택
- **Display / 헤드라인**: `"Playfair Display"`, `"Libre Baskerville"`, Georgia, serif
- **Slab Serif / 서브헤드**: `"Rockwell"`, `"Zilla Slab"`, `"Roboto Slab"`, serif
- **Body**: `"IM Fell English"`, `"Lora"`, Georgia, serif
- **Mono / 타자기**: `"Special Elite"`, `"Courier Prime"`, `"Courier New"`, monospace
- **Decorative**: `"Bebas Neue"` (포스터 제목), `"Alfa Slab One"` (신문 헤드라인)

### Type Scale — 고정 크기 (유체 스케일 사용 안 함)
```css
--text-xs:   0.75rem;    /* 12px */
--text-sm:   0.875rem;   /* 14px */
--text-base: 1rem;       /* 16px */
--text-lg:   1.25rem;    /* 20px */
--text-xl:   1.5rem;     /* 24px */
--text-2xl:  2rem;       /* 32px */
--text-3xl:  3rem;       /* 48px */
--text-display: 4.5rem;  /* 72px — 포스터/헤드라인 */
```

### 복고 타이포 규칙
- 헤드라인: 대문자 + 넓은 자간 (`letter-spacing: 0.1em` 이상)
- 인쇄물 느낌: 약간 불균일한 베이스라인 허용
- 타자기 스타일 텍스트엔 `Special Elite` 또는 `Courier Prime` 사용

```css
.headline-retro {
  font-family: "Playfair Display", Georgia, serif;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: var(--color-ink);
}

.typewriter {
  font-family: "Courier Prime", "Courier New", monospace;
  font-size: var(--text-base);
  line-height: 1.8;
  color: var(--color-ink);
}
```

---

## 3. Texture & Paper Effect

복고 디자인의 핵심 — 디지털의 완벽함을 일부러 깨뜨린다.

### 종이 질감 배경
```css
.paper-texture {
  background-color: var(--color-cream);
  background-image:
    url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='400' height='400'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3CfeColorMatrix type='saturate' values='0'/%3E%3C/filter%3E%3Crect width='400' height='400' filter='url(%23noise)' opacity='0.06'/%3E%3C/svg%3E");
}
```

### 낡은 사진 필터 (CSS)
```css
.vintage-photo {
  filter: sepia(40%) contrast(110%) brightness(95%) saturate(80%);
}

.aged {
  filter: sepia(60%) hue-rotate(-10deg) contrast(105%);
  mix-blend-mode: multiply;
}
```

### 인쇄 불량 효과 (Letterpress)
```css
.letterpress {
  text-shadow:
     1px  1px 0px rgba(255,255,255,0.6),
    -1px -1px 0px rgba(0,0,0,0.25);
  color: var(--color-ink);
}
```

---

## 4. Border & Frame — 굵고 단단한 선

복고 인쇄물은 얇은 그림자 대신 **굵은 실선 테두리**를 사용한다.

```css
/* 기본 복고 카드 */
.retro-card {
  background: var(--color-paper);
  border: 3px solid var(--color-border);
  border-radius: 0;              /* 둥근 모서리 금지 */
  box-shadow: 4px 4px 0px var(--color-border);  /* 오프셋 그림자 */
  padding: 1.5rem;
}

/* 이중 테두리 — 신문/포스터 스타일 */
.double-border {
  border: 3px solid var(--color-ink);
  outline: 6px solid var(--color-ink);
  outline-offset: 4px;
}

/* 장식선 — 빅토리안 스타일 */
.ornament-border {
  border-top: 6px double var(--color-ink);
  border-bottom: 6px double var(--color-ink);
  padding: 1rem 0;
}
```

---

## 5. Layout — 신문/잡지 그리드

```css
/* 신문 다단 레이아웃 */
.newspaper-grid {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr;
  gap: 1.5rem;
  border: 2px solid var(--color-border);
  padding: 2rem;
}

/* 컬럼 구분선 */
.newspaper-grid > * + * {
  border-left: 1px solid var(--color-border);
  padding-left: 1.5rem;
}

/* 포스터 레이아웃 */
.poster-layout {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 0.5rem;
  border: 4px solid var(--color-ink);
  padding: 3rem 2rem;
}
```

---

## 6. Buttons & UI Components

### 복고 버튼 — 오프셋 그림자
```css
.btn-retro {
  display: inline-block;
  padding: 0.625rem 1.5rem;
  background: var(--color-primary);
  color: var(--color-cream);
  font-family: "Rockwell", serif;
  font-weight: 700;
  font-size: var(--text-sm);
  text-transform: uppercase;
  letter-spacing: 0.1em;
  border: 2px solid var(--color-ink);
  border-radius: 0;
  box-shadow: 3px 3px 0px var(--color-ink);
  cursor: pointer;
  transition: box-shadow 80ms ease, transform 80ms ease;
}

.btn-retro:hover {
  box-shadow: 5px 5px 0px var(--color-ink);
  transform: translate(-1px, -1px);
}

.btn-retro:active {
  box-shadow: 1px 1px 0px var(--color-ink);
  transform: translate(2px, 2px);
}
```

### 스탬프 배지
```css
.stamp {
  display: inline-block;
  padding: 0.25rem 0.625rem;
  border: 2px solid currentColor;
  font-family: "Courier Prime", monospace;
  font-size: var(--text-xs);
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.15em;
  color: var(--color-primary);
  transform: rotate(-3deg);
  opacity: 0.85;
}
```

### 복고 입력 필드
```css
.input-retro {
  background: var(--color-cream);
  border: 0;
  border-bottom: 2px solid var(--color-ink);
  border-radius: 0;
  padding: 0.5rem 0.25rem;
  font-family: "Courier Prime", monospace;
  font-size: var(--text-base);
  color: var(--color-ink);
  outline: none;
  width: 100%;
}

.input-retro:focus {
  border-bottom-color: var(--color-primary);
}
```

### 복고 내비게이션 바
```css
.navbar-retro {
  background: var(--color-ink);
  color: var(--color-cream);
  padding: 0.75rem 2rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-bottom: 4px solid var(--color-primary);
  font-family: "Rockwell", serif;
  text-transform: uppercase;
  letter-spacing: 0.1em;
}
```

---

## 7. Motion — 느리고 기계적인 움직임

복고 UI는 매끄러운 스프링 대신 **딱딱하고 단계적인** 움직임을 사용한다.

```css
/* 타자기 텍스트 효과 */
@keyframes typewriter {
  from { width: 0; }
  to   { width: 100%; }
}

.typewriter-anim {
  overflow: hidden;
  white-space: nowrap;
  border-right: 3px solid var(--color-ink);
  animation:
    typewriter 2s steps(40) forwards,
    blink-cursor 0.75s step-end infinite;
}

@keyframes blink-cursor {
  50% { border-color: transparent; }
}

/* 레트로 스탬프 등장 */
@keyframes stamp-in {
  0%   { transform: scale(2) rotate(-5deg); opacity: 0; }
  60%  { transform: scale(0.95) rotate(-2deg); opacity: 1; }
  100% { transform: scale(1) rotate(-3deg); opacity: 0.85; }
}

.stamp-appear {
  animation: stamp-in 300ms cubic-bezier(0.25, 0.46, 0.45, 0.94) forwards;
}

/* 필름 흔들림 */
@keyframes film-jitter {
  0%, 100% { transform: translate(0, 0); }
  25%       { transform: translate(-1px, 1px); }
  50%       { transform: translate(1px, -1px); }
  75%       { transform: translate(-1px, -1px); }
}

.film-effect {
  animation: film-jitter 0.1s infinite;
}
```

---

## 8. Spacing & Sizing Tokens

```css
--space-1:  0.25rem;   /*  4px */
--space-2:  0.5rem;    /*  8px */
--space-3:  0.75rem;   /* 12px */
--space-4:  1rem;      /* 16px */
--space-6:  1.5rem;    /* 24px */
--space-8:  2rem;      /* 32px */
--space-12: 3rem;      /* 48px */
--space-16: 4rem;      /* 64px */
--space-24: 6rem;      /* 96px */

/* 복고 스타일은 radius 없이 사용하는 것이 기본 */
--radius-none: 0;
--radius-sm: 2px;   /* 최소한의 모서리 처리만 허용 */
```

---

## 9. Decorative Elements

### 구분선 — 인쇄물 스타일
```css
.divider-ornament {
  display: flex;
  align-items: center;
  gap: 1rem;
  color: var(--color-ink);
  font-size: 1.2rem;
}

.divider-ornament::before,
.divider-ornament::after {
  content: "";
  flex: 1;
  height: 2px;
  background: var(--color-ink);
}
```

### 워터마크 / 도장 효과
```css
.watermark {
  position: relative;
}

.watermark::after {
  content: "DRAFT";
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: "Rockwell", serif;
  font-size: 5rem;
  font-weight: 900;
  color: var(--color-primary);
  opacity: 0.08;
  transform: rotate(-30deg);
  pointer-events: none;
  text-transform: uppercase;
  letter-spacing: 0.2em;
}
```

---

## 10. Accessibility Baseline

복고 스타일이라도 접근성 기준은 동일하게 적용한다.

- **대비**: 크림 배경 위 잉크색 텍스트 — 자연스럽게 10:1 이상 확보
- **포커스**: 굵은 실선 포커스 링 (복고 스타일과 자연스럽게 어울림)
- **모션**: `prefers-reduced-motion` 적용 — 타자기 애니메이션 등 비활성화

```css
:focus-visible {
  outline: 3px solid var(--color-primary);
  outline-offset: 2px;
  border-radius: 0;
}

@media (prefers-reduced-motion: reduce) {
  .typewriter-anim,
  .film-effect,
  .stamp-appear {
    animation: none;
  }
}
```

---

## Quick-reference: Retro Design Checklist

| 요소 | 스타일 |
|------|--------|
| 배경 | 크림/페이퍼 (#F5F0E8 / #EDE6D3) |
| 폰트 | Serif / Slab Serif / Typewriter |
| 테두리 | 굵은 실선 + 오프셋 그림자 (no border-radius) |
| 색상 | 빈티지 레드, 번트 오렌지, 머스타드 (3~4색 제한) |
| 질감 | 종이 노이즈, 세피아 필터, Letterpress 텍스트 |
| 레이아웃 | 신문 다단 그리드, 포스터 중앙 정렬 |
| 버튼 | 오프셋 박스 그림자, 대문자, 각진 모서리 |
| 모션 | 타자기 효과, 스탬프 등장, 딱딱한 스텝 이징 |
| 장식 | 이중 테두리, 오너먼트 구분선, 워터마크 도장 |
| 접근성 | WCAG AA (자동 충족), reduced-motion 처리 |
