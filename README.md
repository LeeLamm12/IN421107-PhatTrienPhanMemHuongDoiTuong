# PTPMHDT-IN421107-DHCNTT24A-IT

Bài tập môn **Phát triển phần mềm hướng đối tượng**

- **Lớp:** ĐHCNTT24A-IT (IN421107)
- **Giảng viên:** Nguyễn Tuấn Kiệt
- **Sinh viên:** SonLeLam - 0024418698 *(thay bằng họ tên đầy đủ)*

## Cấu trúc repo

Mỗi chương nằm trên một nhánh riêng và được nộp bằng Pull Request vào `main`. Nhánh `main` chỉ chứa README này.

| Chương | Nhánh | Nội dung | Pull Request |
|--------|-------|----------|--------------|
| Ch01 | `ch01/0024418698` | *(điền tóm tắt nội dung Ch01)* | [#1](https://github.com/LeeLamm12/PTPMHDT-IN421107-DHCNTT24A-IT/pull/1) |
| Ch02 | `ch02/0024418698` | Refactor `ClubManager` theo SOLID và design pattern | [#2](https://github.com/LeeLamm12/PTPMHDT-IN421107-DHCNTT24A-IT/pull/2) |

## Ch02: Refactor SOLID và Design Pattern

Tách God class `ClubManager` thành các thành phần nhỏ, phụ thuộc qua interface (SRP, OCP, DIP, ISP). Phân tích chi tiết các vi phạm nằm ở `docs/solid-analysis.md` trên nhánh Ch02.

| Pattern | Áp dụng |
|---------|---------|
| Factory | `INotificationServiceFactory` thay chuỗi if/else khi gửi thông báo |
| Decorator | `LoggingClubRepository` bọc `IClubRepository` để ghi log |
| Strategy | `IReportStrategy` (`ConsoleReportStrategy`, `CsvReportStrategy`) |
| Observer | `IEventObserver` (`LogNotifier`, `EmailNotifier`) khi tạo sự kiện |

### Cấu trúc thư mục (nhánh Ch02)

```
Ch02.Refactor/
  Domain/          Club, Event, Member
  Logging/         IAppLogger, ConsoleLogger, FileLogger
  Notifications/   INotificationService, các kênh Email/SMS/Slack, Factory
  Repositories/    IClubRepository, IMemberRepository, IEventRepository, bản InMemory, Decorator
  Services/        ClubService, EventService, ReportService
  Reports/         IReportStrategy và các strategy
  Observers/       IEventObserver và các observer
  Program.cs       Composition root
Ch02.Refactor.Tests/   Unit test theo mẫu AAA
docs/                  solid-analysis.md
```

### Chạy thử

Chuyển sang nhánh `ch02/0024418698`, cần .NET SDK 10:

```
dotnet build Ch02.Refactor.sln
dotnet test Ch02.Refactor.sln
dotnet run --project Ch02.Refactor
```

Kết quả test: 12 test đều qua.
