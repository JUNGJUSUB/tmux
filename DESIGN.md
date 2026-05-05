# Design System

## Modern Design Guide
> 영감: Vercel, Linear, Notion, Apple — 깔끔하고 기능적인 미니멀리즘

---

## 1. Color System

### Palette — Neutral + Accent
| Token | Value | Usage |
|-------|-------|-------|
| `--color-bg` | `#FFFFFF` | 기본 배경 |
| `--color-bg-subtle` | `#F9FAFB` | 섹션 구분 배경 |
| `--color-surface` | `#F3F4F6` | 카드, 입력 필드 배경 |
| `--color-border` | `#E5E7EB` | 구분선, 테두리 |
| `--color-border-strong` | `#D1D5DB` | 강조 테두리 |
| `--color-text` | `#111827` | 본문 텍스트 |
| `--color-text-secondary` | `#6B7280` | 보조 텍스트 |
| `--color-text-disabled` | `#9CA3AF` | 비활성 텍스트 |
| `--color-primary` | `#2563EB` | CTA, 링크, 활성 상태 |
| `--color-primary-hover` | `#1D4ED8` | 버튼 hover |
| `--color-success` | `#16A34A` | 성공 상태 |
| `--color-warning` | `#D97706` | 경고 상태 |
| `--color-danger` | `#DC2626` | 에러 상태 |

### 다크 모드
```css
:root {
  --color-bg:              #FFFFFF;
  --color-bg-subtle:       #F9FAFB;
  --color-surface:         #F3F4F6;
  --color-border:          #E5E7EB;
  --color-border-strong:   #D1D5DB;
  --color-text:            #111827;
  --color-text-secondary:  #6B7280;
  --color-text-disabled:   #9CA3AF;
  --color-primary:         #2563EB;
  --color-primary-hover:   #1D4ED8;
}

[data-theme="dark"] {
  --color-bg:              #0A0A0A;
  --color-bg-subtle:       #111111;
  --color-surface:         #1A1A1A;
  --color-border:          #262626;
  --color-border-strong:   #404040;
  --color-text:            #FAFAFA;
  --color-text-secondary:  #A3A3A3;
  --color-text-disabled:   #525252;
  --color-primary:         #3B82F6;
  --color-primary-hover:   #60A5FA;
}
```

---

## 2. Typography

### 폰트 스택
- **Display**: `"Geist"`, `"Inter"`, system-ui, sans-serif
- **Body**: `"Inter"`, `"DM Sans"`, system-ui, sans-serif
- **Mono**: `"Geist Mono"`, `"JetBrains Mono"`, monospace

```css
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap");
```

### Type Scale
```css
--text-xs:      0.75rem;    /* 12px — 라벨, 캡션 */
--text-sm:      0.875rem;   /* 14px — 보조 텍스트 */
--text-base:    1rem;       /* 16px — 본문 */
--text-lg:      1.125rem;   /* 18px — 서브헤드 */
--text-xl:      1.25rem;    /* 20px */
--text-2xl:     1.5rem;     /* 24px */
--text-3xl:     1.875rem;   /* 30px */
--text-4xl:     2.25rem;    /* 36px */
--text-5xl:     3rem;       /* 48px — 히어로 */

--font-normal:  400;
--font-medium:  500;
--font-semibold: 600;
--font-bold:    700;

--leading-tight:  1.25;
--leading-normal: 1.5;
--leading-relaxed: 1.75;

--tracking-tight:  -0.02em;
--tracking-normal:  0em;
--tracking-wide:    0.02em;
```

```css
.heading-1 {
  font-size: var(--text-5xl);
  font-weight: var(--font-bold);
  letter-spacing: var(--tracking-tight);
  line-height: var(--leading-tight);
  color: var(--color-text);
}

.body {
  font-size: var(--text-base);
  font-weight: var(--font-normal);
  line-height: var(--leading-relaxed);
  color: var(--color-text-secondary);
}
```

---

## 3. Spacing & Sizing

```css
--space-0:  0;
--space-1:  0.25rem;   /*  4px */
--space-2:  0.5rem;    /*  8px */
--space-3:  0.75rem;   /* 12px */
--space-4:  1rem;      /* 16px */
--space-5:  1.25rem;   /* 20px */
--space-6:  1.5rem;    /* 24px */
--space-8:  2rem;      /* 32px */
--space-10: 2.5rem;    /* 40px */
--space-12: 3rem;      /* 48px */
--space-16: 4rem;      /* 64px */
--space-20: 5rem;      /* 80px */
--space-24: 6rem;      /* 96px */

--radius-sm:   0.25rem;   /*  4px */
--radius-md:   0.5rem;    /*  8px */
--radius-lg:   0.75rem;   /* 12px */
--radius-xl:   1rem;      /* 16px */
--radius-2xl:  1.5rem;    /* 24px */
--radius-full: 9999px;
```

---

## 4. Shadows

```css
--shadow-xs: 0 1px 2px rgba(0, 0, 0, 0.05);
--shadow-sm: 0 1px 3px rgba(0, 0, 0, 0.08), 0 1px 2px rgba(0, 0, 0, 0.04);
--shadow-md: 0 4px 6px rgba(0, 0, 0, 0.06), 0 2px 4px rgba(0, 0, 0, 0.04);
--shadow-lg: 0 10px 15px rgba(0, 0, 0, 0.08), 0 4px 6px rgba(0, 0, 0, 0.04);
--shadow-xl: 0 20px 25px rgba(0, 0, 0, 0.10), 0 8px 10px rgba(0, 0, 0, 0.04);
```

---

## 5. Layout

### 컨테이너
```css
.container {
  width: 100%;
  max-width: 1200px;
  margin-inline: auto;
  padding-inline: var(--space-6);
}

.container-sm  { max-width: 640px; }
.container-md  { max-width: 768px; }
.container-lg  { max-width: 1024px; }
.container-xl  { max-width: 1280px; }
```

### 12컬럼 그리드
```css
.grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: var(--space-6);
}

.col-4  { grid-column: span 4; }
.col-6  { grid-column: span 6; }
.col-8  { grid-column: span 8; }
.col-12 { grid-column: span 12; }
```

### 섹션 간격
```css
.section {
  padding-block: var(--space-24);
}

.section-sm {
  padding-block: var(--space-12);
}
```

---

## 6. Components

### 버튼
```css
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: var(--space-2);
  padding: var(--space-2) var(--space-4);
  font-size: var(--text-sm);
  font-weight: var(--font-medium);
  line-height: 1;
  border-radius: var(--radius-md);
  border: 1px solid transparent;
  cursor: pointer;
  transition: all 150ms ease;
  white-space: nowrap;
  user-select: none;
}

/* Primary */
.btn-primary {
  background: var(--color-primary);
  color: #fff;
  border-color: var(--color-primary);
}
.btn-primary:hover { background: var(--color-primary-hover); }

/* Secondary */
.btn-secondary {
  background: var(--color-surface);
  color: var(--color-text);
  border-color: var(--color-border);
}
.btn-secondary:hover { background: var(--color-border); }

/* Ghost */
.btn-ghost {
  background: transparent;
  color: var(--color-text-secondary);
}
.btn-ghost:hover {
  background: var(--color-surface);
  color: var(--color-text);
}

/* 사이즈 */
.btn-sm { padding: var(--space-1) var(--space-3); font-size: var(--text-xs); }
.btn-lg { padding: var(--space-3) var(--space-6); font-size: var(--text-base); }
```

### 카드
```css
.card {
  background: var(--color-bg);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-xl);
  padding: var(--space-6);
  box-shadow: var(--shadow-sm);
  transition: box-shadow 200ms ease, border-color 200ms ease;
}

.card:hover {
  box-shadow: var(--shadow-md);
  border-color: var(--color-border-strong);
}
```

### 입력 필드
```css
.input {
  width: 100%;
  padding: var(--space-2) var(--space-3);
  background: var(--color-bg);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-md);
  font-size: var(--text-sm);
  color: var(--color-text);
  transition: border-color 150ms ease, box-shadow 150ms ease;
  outline: none;
}

.input::placeholder { color: var(--color-text-disabled); }

.input:hover { border-color: var(--color-border-strong); }

.input:focus {
  border-color: var(--color-primary);
  box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.12);
}
```

### 배지
```css
.badge {
  display: inline-flex;
  align-items: center;
  gap: var(--space-1);
  padding: 0.125rem var(--space-2);
  font-size: var(--text-xs);
  font-weight: var(--font-medium);
  border-radius: var(--radius-full);
  border: 1px solid transparent;
}

.badge-default  { background: var(--color-surface);  color: var(--color-text-secondary); border-color: var(--color-border); }
.badge-primary  { background: #EFF6FF; color: #1D4ED8; border-color: #BFDBFE; }
.badge-success  { background: #F0FDF4; color: #15803D; border-color: #BBF7D0; }
.badge-warning  { background: #FFFBEB; color: #B45309; border-color: #FDE68A; }
.badge-danger   { background: #FEF2F2; color: #B91C1C; border-color: #FECACA; }
```

### 내비게이션 바
```css
.navbar {
  position: sticky;
  top: 0;
  z-index: 50;
  height: 56px;
  display: flex;
  align-items: center;
  padding-inline: var(--space-6);
  background: rgba(255, 255, 255, 0.85);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--color-border);
}
```

### 구분선
```css
.divider {
  height: 1px;
  background: var(--color-border);
  border: none;
  margin-block: var(--space-6);
}
```

---

## 7. Motion

### 원칙
- **빠르게**: UI 피드백은 100–200ms
- **자연스럽게**: ease-out 기본, 강조엔 spring
- **절제**: 꼭 필요한 곳에만 사용

```css
--duration-fast:     100ms;
--duration-normal:   200ms;
--duration-slow:     400ms;

--ease-default:  cubic-bezier(0.4, 0, 0.2, 1);
--ease-out:      cubic-bezier(0, 0, 0.2, 1);
--ease-in:       cubic-bezier(0.4, 0, 1, 1);
--ease-spring:   cubic-bezier(0.34, 1.56, 0.64, 1);
```

```css
/* 페이드 인 */
@keyframes fade-in {
  from { opacity: 0; transform: translateY(8px); }
  to   { opacity: 1; transform: translateY(0); }
}

.animate-fade-in {
  animation: fade-in var(--duration-normal) var(--ease-out) both;
}

/* 스케일 인 (모달, 팝오버) */
@keyframes scale-in {
  from { opacity: 0; transform: scale(0.96); }
  to   { opacity: 1; transform: scale(1); }
}

.animate-scale-in {
  animation: scale-in var(--duration-fast) var(--ease-out) both;
}
```

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

---

## 8. Accessibility Baseline

- **대비**: 본문 텍스트 4.5:1 이상 (WCAG AA), 대형 텍스트 3:1 이상
- **포커스**: 항상 가시적인 포커스 링 유지
- **시맨틱**: `<button>`, `<nav>`, `<main>` 등 네이티브 요소 우선
- **색상**: 색상만으로 정보를 전달하지 않음 — 아이콘/레이블 병행

```css
:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 2px;
  border-radius: var(--radius-sm);
}
```

---

## Quick-reference

| 항목 | 스펙 |
|------|------|
| 배경 | White `#FFFFFF` / Dark `#0A0A0A` |
| 폰트 | Inter, Geist (시스템 UI 우선) |
| 기본 radius | `8px` (md) |
| 기본 border | `1px solid #E5E7EB` |
| 기본 shadow | `shadow-sm` |
| 버튼 높이 | sm `28px` / md `36px` / lg `44px` |
| 인터랙션 시간 | 150–200ms |
| 포커스 링 | `2px solid #2563EB`, offset `2px` |
| 다크 모드 | `[data-theme="dark"]` |
| 접근성 | WCAG AA |
