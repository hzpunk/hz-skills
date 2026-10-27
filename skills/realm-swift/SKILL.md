---
name: realm-swift
description: "Modern offline-first mobile data persistence using Realm Swift: reactive @ObservedResults, Swift Concurrency (async/await), schema migrations, and sync."
---

# Realm Swift (`/realm-swift`)

Стандарт оффлайн-первого мобильного хранилища данных на Swift для iOS и macOS.

## Ключевые принципы:
- **Zero-Copy Architecture:** Realm считывает объекты напрямую из памяти без сериализации.
- **Live Objects:** Объекты обновляются автоматически при любых мутациях в фоновых потоках.
- **SwiftUI реактивность:** Использование `@ObservedResults` и `@ObservedRealmObject`.

## Пример Модели и Реактивного View:
```swift
import SwiftUI
import RealmSwift

class ClientSession: Object, ObjectKeyIdentifiable {
    @Persisted(primaryKey: true) var id: ObjectId
    @Persisted var clientName: String = ""
    @Persisted var date: Date = Date()
    @Persisted var notes: String = ""
    @Persisted var isCompleted: Bool = false
}

struct SessionListView: View {
    @ObservedResults(ClientSession.self) var sessions

    var body: some View {
        List {
            ForEach(sessions) { session in
                VStack(alignment: .leading) {
                    Text(session.clientName).font(.headline)
                    Text(session.date.formatted(date: .abbreviated, time: .shortened))
                        .font(.caption).foregroundColor(.secondary)
                }
            }
        }
    }
}
```
