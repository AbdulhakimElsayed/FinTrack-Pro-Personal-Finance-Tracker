# 💰 FinTrack Pro — Personal Finance Tracker

<div align="center">

![Flutter](https://img.shields.io/badge/Flutter-3.x-02569B?style=for-the-badge&logo=flutter&logoColor=white)
![Dart](https://img.shields.io/badge/Dart-3.x-0175C2?style=for-the-badge&logo=dart&logoColor=white)
![BLoC](https://img.shields.io/badge/State-BLoC%2FCubit-6A1B9A?style=for-the-badge)
![Tests](https://img.shields.io/badge/Tests-21%20Passing-2E7D32?style=for-the-badge&logo=checkmarx&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-F77F00?style=for-the-badge)

**A full-featured personal finance mobile app built with Flutter.**
Track your expenses, set monthly budgets, and take control of your money.

[Features](#-features) • [Screenshots](#-screenshots) • [Architecture](#-architecture) • [Getting Started](#-getting-started) • [Tech Stack](#-tech-stack)

</div>

---

## 📱 Screenshots

> *Actual screenshots from the app*

| Dashboard & Balance | Budget Overview | Transaction List |
|---------------------|----------------|------------------|
| ![Dashboard](assets/screenshots/dashboard.png) | ![Budget Overview](assets/screenshots/budget_overview.png) | ![Transaction List](assets/screenshots/transaction_list.png) |
| **Category Budgets** | **Analytics** | **Spending Trends** |
| ![Category Budgets](assets/screenshots/category_budgets.png) | ![Analytics](assets/screenshots/analytics.png) | ![Spending Trends](assets/screenshots/spending_trends.png) |

---

## ✨ Features

### 💳 Expense Tracking
- Log transactions with amount, category, date, and description
- Support for multiple currencies (default: Egyptian Pound EGP)
- Multi-language description input including Arabic
- Edit and delete existing transactions with confirmation dialog
- Real-time total spending calculation

### 📅 Temporal Navigation
- Navigate month by month to view historical spending
- Calendar view showing days with logged expenses
- Filter transactions by specific date

### 🎯 Budget Management
- Set an overall monthly budget
- Set per-category budgets with enable/disable toggle
- Real-time progress bars with color-coded status:
  - 🟢 **Safe** — under 70% spent
  - 🟡 **Warning** — 70–90% spent
  - 🔴 **Exceeded** — over 90% spent
- Smart alerts when approaching or exceeding budget limits
- Monthly budget report with category breakdown

### 👤 Account & Settings
- User authentication with cloud sync support
- Category management (create, edit, delete)
- Frequent expenses templates for quick entry
- Manual backup and restore data
- Reset all data option
- Currency localization
- Premium subscription to remove ads

### 🔔 Notifications
- Local push notifications for budget alerts
- Graceful fallback if notifications are unavailable

---

## 🏗 Architecture

This project follows **Clean Architecture** with a feature-first folder structure.

```
lib/
├── core/
│   ├── di/                  # Dependency injection (get_it)
│   ├── router/              # App routing (go_router)
│   ├── theme/               # App theme & colors
│   └── utils/               # Shared utilities
├── features/
│   ├── auth/                # Authentication (BLoC)
│   ├── transactions/        # Transaction CRUD (BLoC)
│   ├── budgets/             # Budget management (Cubit)
│   ├── dashboard/           # Home screen
│   ├── categories/          # Category management
│   └── settings/            # App settings (Cubit)
└── main.dart
```

### State Management Strategy

| Feature | Pattern | Reason |
|---------|---------|--------|
| Auth | Full BLoC | Complex event-driven flow |
| Transactions | Full BLoC | CRUD with multiple event types |
| Budget | Cubit | Straightforward data operations |
| Settings | Cubit | Simple key-value state |

### Data Flow

```
UI → Event → BLoC/Cubit → Repository → DataSource (SharedPreferences)
                ↓
           emit(State) → UI rebuilds
```

---

## 🚀 Getting Started

### Prerequisites

- Flutter SDK `>=3.0.0`
- Dart SDK `>=3.0.0`
- Android Studio / VS Code
- Android or iOS device / emulator

### Installation

**1. Clone the repository**
```bash
git clone https://github.com/your-username/fintrack-pro.git
cd fintrack-pro
```

**2. Install dependencies**
```bash
flutter pub get
```

**3. Run the app**
```bash
# Debug mode
flutter run

# Release mode (recommended for performance testing)
flutter run --release
```

**4. Run tests**
```bash
flutter test
```

---

## 🧰 Tech Stack

| Package | Version | Purpose |
|---------|---------|---------|
| `flutter_bloc` | ^8.x | State management (BLoC + Cubit) |
| `get_it` | ^7.x | Dependency injection |
| `go_router` | latest | Declarative routing |
| `shared_preferences` | ^2.x | Local data persistence |
| `equatable` | ^2.x | Value equality for BLoC states |
| `flutter_local_notifications` | latest | Push notifications |
| `uuid` | latest | Unique ID generation |
| `intl` | latest | Date & currency formatting |

---

## 🧪 Testing

The project includes **21 passing tests** covering core business logic.

```bash
# Run all tests
flutter test

# Run with coverage
flutter test --coverage
```

**Test coverage includes:**
- Transaction repository logic
- Budget calculation and progress
- BLoC state transitions
- Data serialization / deserialization

---

## 📁 Key Files

| File | Description |
|------|-------------|
| `lib/main.dart` | App entry point, DI initialization, MultiBlocProvider setup |
| `lib/core/di/service_locator.dart` | get_it registrations for all Blocs, Cubits, and Repos |
| `lib/core/router/app_router.dart` | All app routes defined with go_router |
| `lib/features/budgets/presentation/cubits/budget_cubit.dart` | Budget state management |
| `lib/features/transactions/presentation/bloc/transaction_bloc.dart` | Transaction state management |

---

## 🗺 Roadmap

- [ ] Charts & spending analytics
- [ ] Export transactions to CSV / PDF
- [ ] Recurring transactions
- [ ] Dark mode support
- [ ] iOS widget support
- [ ] Firebase cloud sync
- [ ] Multi-account support

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

Made with ❤️ using Flutter

⭐ Star this repo if you found it helpful!

</div>
