# .NET Architecture
Use para Core/Application/Infrastructure.
- .NET 10.
- Domain puro.
- Application/CQRS quando a fase autorizar.
- Infrastructure implementa contratos.
- UI sem regra de negócio.
- Dependências apontam para dentro.
- I/O, storage, jogo e integrações ficam atrás de interfaces.
Evite abstrações especulativas sem uso na task atual.
