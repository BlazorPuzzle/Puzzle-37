# Blazor Puzzle #37

## Minimal API Issue

YouTube Video: https://youtu.be/ncsI4qbXfUo

Blazor Puzzle Home Page: https://blazorpuzzle.com

### The Challenge:

This is a Global WebAssembly Blazor Web App that calls into a server-side minimal API endpoint. The app blows up when we try to retrieve the data as a string. Why?

### The Solution:

The problem is that the HttpClient added as a service in Program.cs is not configured with the base address of the server. Replace it with this:

```c#
builder.Services.AddScoped(sp => new HttpClient
{ BaseAddress = new Uri(builder.HostEnvironment.BaseAddress) });
```



