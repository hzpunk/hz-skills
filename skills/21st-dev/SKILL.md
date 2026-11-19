---
name: 21st-dev
description: "Master catalog and implementation blueprints for 21st.dev (The NPM for Design Engineers). Production-ready shadcn-compatible creative components, Apple-grade spring physics, interactive bento grids, glowing borders, dynamic docks, and micro-interactions. Mandatory for all frontend work to elevate UI quality beyond generic boilerplate."
metadata:
  author: hz-ecosystem
  version: "1.0.0"
  source: "https://21st.dev"
---

# 21st.dev Component & Design Engineering Catalog

Инженерный стандарт и руководство по внедрению компонентов с платформы **21st.dev** («The NPM for Design Engineers» / открытый реестр компонентов для дизайн-инженеров).

21st.dev ориентирован на сочетание доступности `shadcn/ui`, микро-взаимодействий уровня Apple WWDC, пружинной кинематики Framer Motion и премиальной эстетики темных/светлых интерфейсов.

---

## 1. Архитектурные принципы 21st.dev

1. **Совместимость с shadcn/ui:** Каждый компонент строится поверх Radix UI primitives и использует Tailwind токены (`bg-background`, `border-border`, `text-primary`).
2. **Анти-дженерик (Anti-Slop):** Запрещены скучные прямоугольники и сухие дефолтные таблицы. Применяются глубина, слоистость, стекломорфизм с легким оптическим шумом и динамические световые границы.
3. **Пружинная кинематика (Spring Physics):** Все переходы настраиваются через физические параметры (`stiffness`, `damping`, `mass`), а не линейные временные кривые.
4. **Контекстный отклик:** Элементы интерфейса отзываются на курсор, скролл, касание и фокус клавиатуры с осязаемым откликом.

---

## 2. Ключевые компоненты и паттерны

### A. Dynamic Island & Floating Glass Bar (Плавающий адаптивный бар)
Компактный остров состояния, который плавно морфируется при смене режима (уведомление, плеер, статус заказа, поиск).
```tsx
'use client';
import { motion, AnimatePresence } from 'framer-motion';
import { useState } from 'react';

export function DynamicIsland({
  collapsedContent,
  expandedContent,
}: {
  collapsedContent: React.ReactNode;
  expandedContent: React.ReactNode;
}) {
  const [isExpanded, setIsExpanded] = useState(false);

  return (
    <motion.div
      layout
      transition={{ type: 'spring', stiffness: 400, damping: 30 }}
      onClick={() => setIsExpanded(!isExpanded)}
      className="fixed top-6 left-1/2 -translate-x-1/2 z-50 cursor-pointer overflow-hidden rounded-full border border-border/40 bg-background/80 backdrop-blur-xl shadow-2xl px-4 py-2"
    >
      <AnimatePresence mode="wait">
        {!isExpanded ? (
          <motion.div
            key="collapsed"
            initial={{ opacity: 0, scale: 0.9 }}
            animate={{ opacity: 1, scale: 1 }}
            exit={{ opacity: 0, scale: 0.9 }}
            transition={{ duration: 0.15 }}
          >
            {collapsedContent}
          </motion.div>
        ) : (
          <motion.div
            key="expanded"
            initial={{ opacity: 0, scale: 0.95 }}
            animate={{ opacity: 1, scale: 1 }}
            exit={{ opacity: 0, scale: 0.95 }}
            transition={{ duration: 0.2 }}
            className="p-2"
          >
            {expandedContent}
          </motion.div>
        )}
      </AnimatePresence>
    </motion.div>
  );
}
```

### B. Border Beam (Световой луч по контуру карточки)
Анимированный луч, обходящий границы контейнера с закруглением через SVG и `offset-path`.
```tsx
export function BorderBeam({
  className = '',
  size = 200,
  duration = 15,
  anchor = 90,
  borderWidth = 1.5,
  colorFrom = '#F59E0B',
  colorTo = '#EF4444',
  delay = 0,
}: {
  className?: string;
  size?: number;
  duration?: number;
  anchor?: number;
  borderWidth?: number;
  colorFrom?: string;
  colorTo?: string;
  delay?: number;
}) {
  return (
    <div
      style={
        {
          '--size': size,
          '--duration': duration,
          '--anchor': anchor,
          '--border-width': borderWidth,
          '--color-from': colorFrom,
          '--color-to': colorTo,
          '--delay': `-${delay}s`,
        } as React.CSSProperties
      }
      className={`pointer-events-none absolute inset-0 rounded-[inherit] [border:calc(var(--border-width)*1px)_solid_transparent] ![mask-clip:padding-box,border-box] ![mask-composite:intersect] [mask:linear-gradient(transparent,transparent),linear-gradient(white,white)] after:absolute after:aspect-square after:w-[calc(var(--size)*1px)] after:animate-border-beam after:[animation-delay:var(--delay)] after:[background:linear-gradient(to_left,var(--color-from),var(--color-to),transparent)] after:[offset-anchor:calc(var(--anchor)*1%)_50%] after:[offset-path:rect(0_auto_auto_0_round_calc(var(--size)*1px))] ${className}`}
    />
  );
}
```

### C. Animated Bento Grid (Интерактивная бенто-сетка с микро-физикой)
Асимметричная сетка с акцентными карточками, эффектом глубины и живыми микро-графиками.
```tsx
import { ReactNode } from 'react';

export function BentoGrid({
  children,
  className = '',
}: {
  children: ReactNode;
  className?: string;
}) {
  return (
    <div className={`grid grid-cols-1 md:grid-cols-3 gap-4 max-w-7xl mx-auto ${className}`}>
      {children}
    </div>
  );
}

export function BentoCard({
  title,
  description,
  header,
  icon,
  className = '',
}: {
  title: string;
  description: string;
  header: ReactNode;
  icon?: ReactNode;
  className?: string;
}) {
  return (
    <div
      className={`group relative flex flex-col justify-between overflow-hidden rounded-2xl border border-border/60 bg-card p-6 shadow-sm hover:shadow-xl hover:border-primary/40 transition-all duration-300 ${className}`}
    >
      <div className="w-full transition-transform duration-300 group-hover:scale-[1.02]">
        {header}
      </div>
      <div className="z-10 mt-4">
        <div className="flex items-center gap-2 mb-2">
          {icon}
          <h3 className="font-semibold text-lg text-foreground tracking-tight">{title}</h3>
        </div>
        <p className="text-sm text-muted-foreground leading-relaxed">{description}</p>
      </div>
    </div>
  );
}
```

### D. Shimmer Button & Liquid Hover (Кнопки премиум-класса)
Кнопка с мягким градиентным мерцанием и осязаемым нажатием (`whileTap={{ scale: 0.98 }}`).
```tsx
'use client';
import { motion } from 'framer-motion';

export function ShimmerButton({
  children,
  onClick,
  className = '',
}: {
  children: React.ReactNode;
  onClick?: () => void;
  className?: string;
}) {
  return (
    <motion.button
      whileHover={{ scale: 1.02 }}
      whileTap={{ scale: 0.98 }}
      transition={{ type: 'spring', stiffness: 400, damping: 25 }}
      onClick={onClick}
      className={`relative inline-flex items-center justify-center overflow-hidden rounded-xl bg-primary px-6 py-3 text-sm font-medium text-primary-foreground shadow-lg shadow-primary/20 hover:shadow-primary/40 transition-shadow ${className}`}
    >
      <span className="absolute inset-0 bg-gradient-to-r from-transparent via-white/20 to-transparent -translate-x-full hover:animate-[shimmer_1.5s_infinite]" />
      <span className="relative z-10 flex items-center gap-2">{children}</span>
    </motion.button>
  );
}
```

---

## 3. Правила обязательного использования в Frontend задачах

1. **Никакой сырой верстки без динамики:** Любая кнопка, карточка, заголовок и модалка обязаны содержать продуманные состояния:
   - `initial` / `animate` / `whileHover` / `whileTap` / `exit`.
2. **Обязательная связка со скиллами:**
   - Комбинировать с `reactbits` для кинетической типографики.
   - Комбинировать с `apple-motion-design` для естественных пружин.
   - Комбинировать с `mojs-motion` для взрывных частиц при целевых действиях (успешная отправка заявки, подтверждение).
3. **Производительность:**
   - Избегать ре-рендеров через правильный `memo` и `useCallback`.
   - Использовать `layoutId` для плавных переходов табов и индикаторов без дерганий.
