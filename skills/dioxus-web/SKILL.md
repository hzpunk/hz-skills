---
name: dioxus-web
description: "Full-stack Rust reactive UI development for Web (WASM), Desktop, and Mobile with Dioxus 0.5/0.6: signals, RSX, server functions, and SSR."
---

# Dioxus Web (`/dioxus-web`)

Реактивная разработка производительных full-stack приложений на Rust под Web (WASM), Desktop и Mobile.

## Ключевые возможности:
- Быстрее React (zero-cost абстракции Rust, прямой DOM diff).
- Единая кодовая база для Web, macOS, Linux, Windows, iOS, Android.
- Поддержка Server Functions (`#[server]`), Signals (`use_signal`), и Server-Side Rendering (SSR).

## Базовый компонент (Dioxus 0.6):
```rust
use dioxus::prelude::*;

#[component]
pub fn Counter() -> Element {
    let mut count = use_signal(|| 0);

    rsx! {
        div { class: "p-6 rounded-2xl bg-card border border-border shadow-sm",
            h2 { class: "text-xl font-bold text-foreground", "Счетчик: {count}" }
            div { class: "mt-4 flex gap-2",
                button {
                    class: "px-4 py-2 bg-primary text-primary-foreground rounded-lg",
                    onclick: move |_| count += 1,
                    "Увеличить"
                }
                button {
                    class: "px-4 py-2 bg-muted text-muted-foreground rounded-lg",
                    onclick: move |_| count -= 1,
                    "Уменьшить"
                }
            }
        }
    }
}
```
