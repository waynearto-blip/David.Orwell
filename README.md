cat >"$ROOT/README.md" <<'EOF'
# Companion

Companion is the application layer for the **6185 ecosystem**. It consumes the shared Swift package **CompanionCore**, which provides reusable models, networking, validation, and domain logic.

---

## Workspace Layout

```text
~/Developer/waynearto/
├── shared/
│   └── swift/
│       ├── Package.swift
│       └── Sources/
│           └── CompanionCore/
│               ├── Models/
│               │   └── Register.swift
│               ├── Networking/
│               │   ├── ApiClient.swift
│               │   └── RegisterService.swift
│               └── Validation/
│                   └── RegisterValidator.swift
├── Companion/
│   └── iOS/
│       └── Companion/
│           ├── CompanionApp.swift
│           ├── ContentView.swift
│           └── ...
├── 6185/
├── datasets/
├── MoDuSRegister/
├── David.Orwell/
├── .github/
├── README.md
├── Makefile
└── .gitignore
