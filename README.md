var builder = WebApplication.CreateBuilder(args);

builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();

var app = builder.Build();

if (app.Environment.IsDevelopment())
{
    app.UseSwagger();
    app.UseSwaggerUI();
}

// Пример эндпоинта
app.MapGet("/hello", () => new { message = "Hello, World!" })
   .WithName("HelloWorld")
   .WithOpenApi(); // Добавление в документацию Swagger

app.Run();
