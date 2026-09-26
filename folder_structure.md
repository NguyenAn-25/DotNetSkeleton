DotNetSkeleton.sln
│
├── DotNetSkeleton.API/                        # Entry point - Host project
│   ├── Program.cs
│   ├── appsettings.json
│   ├── appsettings.Development.json
│   ├── appsettings.Production.json
│   ├── Properties/
│   │   └── launchSettings.json
│   └── DotNetSkeleton.API.csproj
│
├── Modules/                                    # Module theo feature/domain
│   ├── Users/
│   │   ├── Controllers/
│   │   │   └── UsersController.cs
│   │   ├── Entities/
│   │   │   └── User.cs
│   │   ├── DTOs/
│   │   │   ├── Requests/
│   │   │   │   ├── CreateUserRequest.cs
│   │   │   │   └── UpdateUserRequest.cs
│   │   │   └── Responses/
│   │   │       └── UserResponse.cs
│   │   ├── Services/
│   │   │   ├── IUserService.cs
│   │   │   └── UserService.cs
│   │   ├── Repositories/
│   │   │   ├── IUserRepository.cs
│   │   │   └── UserRepository.cs
│   │   ├── Validators/
│   │   │   └── CreateUserValidator.cs
│   │   ├── Mappings/
│   │   │   └── UserProfile.cs             # AutoMapper
│   │   ├── Configurations/
│   │   │   └── UserEntityConfiguration.cs # EF Fluent API config
│   │   └── UsersModule.cs                 # Đăng ký DI cho module
│   │
│   ├── Orders/
│   │   └── (cấu trúc tương tự Users)
│   │
│   └── Auth/
│       ├── Controllers/
│       │   └── AuthController.cs
│       ├── Services/
│       │   ├── IAuthService.cs
│       │   ├── AuthService.cs
│       │   └── JwtTokenService.cs
│       ├── DTOs/
│       └── AuthModule.cs
│
├── Shared/                                     # Hạ tầng dùng chung toàn bộ modules
│   ├── DotNetSkeleton.Shared/
│   │   ├── Persistence/
│   │   │   ├── AppDbContext.cs               # DbContext chính
│   │   │   ├── Migrations/                   # Migration tự sinh (dotnet ef)
│   │   │   ├── Interceptors/                 # Audit, soft-delete interceptor
│   │   │   │   └── AuditableEntityInterceptor.cs
│   │   │   └── Seeders/                      # Seed data
│   │   │       ├── ISeeder.cs
│   │   │       ├── UserSeeder.cs
│   │   │       ├── RoleSeeder.cs
│   │   │       └── DatabaseSeeder.cs         # Gom & chạy toàn bộ seeder
│   │   │
│   │   ├── Middlewares/
│   │   │   ├── ExceptionHandlingMiddleware.cs
│   │   │   └── RequestLoggingMiddleware.cs
│   │   │
│   │   ├── Filters/
│   │   │   └── ValidationFilter.cs
│   │   │
│   │   ├── Extensions/
│   │   │   ├── SwaggerExtensions.cs          # Cấu hình Swagger
│   │   │   ├── DatabaseExtensions.cs         # Cấu hình DbContext + auto-migrate
│   │   │   ├── AuthenticationExtensions.cs   # Cấu hình JWT
│   │   │   └── CorsExtensions.cs
│   │   │
│   │   ├── Configurations/                   # Options pattern (bind từ appsettings)
│   │   │   ├── JwtSettings.cs
│   │   │   ├── DatabaseSettings.cs
│   │   │   └── CorsSettings.cs
│   │   │
│   │   ├── Common/
│   │   │   ├── BaseEntity.cs                 # Id, CreatedAt, UpdatedAt...
│   │   │   ├── Result.cs                     # Wrapper response chung
│   │   │   ├── PagedResult.cs
│   │   │   └── Exceptions/
│   │   │       ├── NotFoundException.cs
│   │   │       └── BadRequestException.cs
│   │   │
│   │   └── DotNetSkeleton.Shared.csproj
│
├── tests/
│   ├── DotNetSkeleton.UnitTests/
│   │   └── Modules/
│   │       └── Users/
│   │           └── UserServiceTests.cs
│   └── DotNetSkeleton.IntegrationTests/
│       └── Users/
│           └── UsersControllerTests.cs
│
├── .gitignore
├── .editorconfig
├── README.md
└── DotNetSkeleton.sln