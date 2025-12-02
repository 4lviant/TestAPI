"# Product Management API - .NET 8

REST API untuk manajemen produk yang dibangun dengan .NET Core 8

## 📋 Fitur

- ✅ REST API dengan 4 endpoints (GET, POST, DELETE)
- ✅ Logging komprehensif menggunakan ILogger
- ✅ Error handling global
- ✅ Konfigurasi dari appsettings.json
- ✅ Docker containerization
- ✅ Swagger/OpenAPI documentation

## 🚀 API Endpoints

### 1. Get All Products
```http
GET /api/product
```
Response:
```json
{
  \"success\": true,
  \"message\": \"Products retrieved successfully\",
  \"data\": [
    {
      \"id\": \"1\",
      \"name\": \"Laptop\",
      \"description\": \"High-performance laptop for professionals\",
      \"price\": 1299.99,
      \"stock\": 50,
      \"createdAt\": \"2025-01-15T10:00:00Z\",
      \"updatedAt\": \"2025-01-15T10:00:00Z\"
    }
  ]
}
```

### 2. Get Product by ID
```http
GET /api/product/{id}
```
Response:
```json
{
  \"success\": true,
  \"message\": \"Product retrieved successfully\",
  \"data\": {
    \"id\": \"1\",
    \"name\": \"Laptop\",
    \"description\": \"High-performance laptop for professionals\",
    \"price\": 1299.99,
    \"stock\": 50,
    \"createdAt\": \"2025-01-15T10:00:00Z\",
    \"updatedAt\": \"2025-01-15T10:00:00Z\"
  }
}
```

### 3. Create Product
```http
POST /api/product
Content-Type: application/json

{
  \"name\": \"Smartphone\",
  \"description\": \"Latest smartphone with amazing features\",
  \"price\": 799.99,
  \"stock\": 100
}
```
Response:
```json
{
  \"success\": true,
  \"message\": \"Product created successfully\",
  \"data\": {
    \"id\": \"generated-uuid\",
    \"name\": \"Smartphone\",
    \"description\": \"Latest smartphone with amazing features\",
    \"price\": 799.99,
    \"stock\": 100,
    \"createdAt\": \"2025-01-15T10:00:00Z\",
    \"updatedAt\": \"2025-01-15T10:00:00Z\"
  }
}
```

### 4. Delete Product
```http
DELETE /api/product/{id}
```
Response:
```json
{
  \"success\": true,
  \"message\": \"Product deleted successfully\"
}
```

## 🛠️ Prerequisites

- [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)
- [Docker](https://www.docker.com/get-started) (untuk containerization)
- [AWS CLI](https://aws.amazon.com/cli/) (untuk deployment ke AWS)

## 📦 Setup dan Instalasi

### 1. Clone atau Extract Project

```bash
cd /app/dotnet-app
```

### 2. Restore Dependencies

```bash
dotnet restore
```

### 3. Build Project

```bash
dotnet build
```

### 4. Run Locally

```bash
dotnet run
```

## 🐳 Docker

### Build Docker Image

```bash
docker build -t TestAPI:latest .
```

### Run Docker Container

```bash
docker run -d -p 8080:80 --name TestAPI TestAPI:latest
```

### Stop Container

```bash
docker stop TestAPI
docker rm TestAPI
```

## 🔧 Konfigurasi

### appsettings.json

```json
{
  \"Logging\": {
    \"LogLevel\": {
      \"Default\": \"Information\",
      \"Microsoft.AspNetCore\": \"Warning\"
    }
  },
  \"AllowedHosts\": \"*\",
  \"ConnectionStrings\": {
  	\"DefaultConnection\": \"Server=servername;Database=databasename;User ID=sa;Password=password;"\
	}
  }
}
```


## 📊 Logging

Aplikasi menggunakan built-in ILogger dengan format:
- Console logging untuk development
- CloudWatch Logs

Contoh log:
```
[2025-01-15 10:30:00] INFO: GET /api/products called
[2025-01-15 10:30:00] INFO: Retrieving all products
[2025-01-15 10:30:00] INFO: POST /api/products called
[2025-01-15 10:30:00] INFO: Creating new product: Smartphone
```

## 🚨 Error Handling

Aplikasi memiliki global error handler yang menangani semua exception

```

Error response format:
```json
{
  \"success\": false,
  \"message\": \"An error occurred while processing your request\"
}
```

## 📚 Struktur Project

```
dotnet-app/
├── Controllers/
│   └── ProductsController.cs      # REST API endpoints
├── Models/
│   └── Product.cs                 # Data models
├── Services/
│   ├── IService.cs         # Service interface
│   └── PService.cs          # Business logic
├── appsettings.json               # Production config
├── appsettings.Development.json   # Development config
├── Program.cs                     # Application entry point
├── ProductApi.csproj              # Project file
├── Dockerfile                     # Docker configuration
└── README.md                      # This file
```

