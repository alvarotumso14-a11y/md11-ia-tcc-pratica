<<<<<<< HEAD
# CLAUDE.md
## Sobre o projeto
GerenciadorDeTarefas é um console app em C# (.NET) usado como material de prática 
para a avaliação do Módulo 11 (Tecnologias Emergentes e IA). É um gerenciador de 
tarefas simples e intencionalmente minimalista.
## Como rodar
cd GerenciadorDeTarefas
dotnet run
## Estrutura
- Todo o código está em `GerenciadorDeTarefas/Program.cs`
- Não há classes: o projeto usa top-level statements (código direto no arquivo, sem declarar `class`)
- As tarefas são armazenadas como uma lista de tuplas: `(int Id, string Titulo, bool Concluida)`
- Três funções principais:
  - `Adicionar`: cria uma nova tarefa na lista
  - `Concluir`: marca uma tarefa existente como concluída
  - `Listar`: exibe as tarefas no console
## Convenções
- Nomes de funções em PascalCase, em português (Adicionar, Concluir, Listar)
- Manter o estilo simples e direto (top-level statements), sem introduzir camadas 
  de abstração desnecessárias, a menos que peça explicitamente
## Regras para a IA
- Não adicionar frameworks externos ou dependências sem necessidade
- Manter a lista de tarefas em memória (não é objetivo do projeto persistir em banco/arquivo)
- Ao adicionar uma nova função, seguir o mesmo padrão das existentes (nome em português, 
  operando sobre a lista de tuplas)
=======
# CLAUDE.md — GerenciadorDeTarefas

Guia para assistentes de IA trabalhando neste repositório. O código de referência é o console app em `GerenciadorDeTarefas/`.

## Contexto do projeto

- Repositório da avaliação individual do **Módulo 11** (Tecnologias Emergentes e IA).
- App de exemplo: **GerenciadorDeTarefas**, console C# (.NET 8), gerenciador de tarefas em memória.
- Solução: `GerenciadorDeTarefas.sln` → único projeto `GerenciadorDeTarefas/GerenciadorDeTarefas.csproj`.
- O app é **simples de propósito**. Não é um produto; serve para praticar IA conectada ao código local (CLAUDE.md, Skill, evidências).
- Avaliação (README, respostas, skill, EVIDENCIAS.md) fica na raiz; o código executável fica só em `GerenciadorDeTarefas/Program.cs`.

## Mapa de arquivos

| Caminho | Papel |
|---|---|
| `GerenciadorDeTarefas/Program.cs` | Todo o comportamento do app |
| `GerenciadorDeTarefas/GerenciadorDeTarefas.csproj` | SDK `Microsoft.NET.Sdk`, `net8.0`, `RootNamespace` GerenciadorDeTarefas |
| `GerenciadorDeTarefas.sln` | Solução Visual Studio |
| `README.md` | Enunciado e respostas dissertativas da avaliação |
| `EVIDENCIAS.md` | Registro de uso real da IA |
| `.claude/skills/` | Skills reutilizáveis da avaliação |

## Modelo de dados e fluxo

Em `Program.cs`:

- Estado: `List<(int Id, string Titulo, bool Concluida)> tarefas` e `proximoId` começando em `1`.
- Não há classe `Tarefa`, repositório, interface nem persistência.

Funções atuais:

- `Adicionar(string titulo)` — insere `(proximoId++, titulo, false)`.
- `Concluir(int id)` — percorre com `for`; se o id bater, substitui a tupla com `Concluida = true`.
- `Listar()` — imprime `{status} #{id} — {titulo}`, com `[X]` ou `[ ]`.

O script de demonstração adiciona três tarefas, lista, conclui a `#1`, lista de novo e espera `Console.ReadLine()`.

## Convenções de código

- Top-level statements: **não** criar `class Program` nem camadas (serviço, MVC, DI) sem pedido explícito.
- Nomes de funções em **PascalCase e português** (`Adicionar`, `Concluir`, `Listar`). Novas operações no mesmo padrão (`Remover`, `ListarPendentes`, etc.).
- Tarefa continua sendo **tupla** `(Id, Titulo, Concluida)`, não record/class, salvo pedido explícito.
- Estilo: funções locais `void`, `for`/`foreach`, `Console.WriteLine`, interpolação de string. Evitar LINQ, async e bibliotecas extras se o existente não usa.
- Formato da listagem: `[X] #1 — Título` (espaço, `#`, travessão `—`).
- Comentários e textos de console em português, alinhados ao que já existe.
- `ImplicitUsings` e `Nullable` já ligados no csproj; não desligar.

## Comandos úteis

Na pasta `GerenciadorDeTarefas/`:

```bash
dotnet run
dotnet build
```

Abrir a solução: `GerenciadorDeTarefas.sln` no Visual Studio.

Não há testes automatizados neste projeto. Validar pelo `dotnet run` e pela saída no console.

## O que a IA NÃO deve fazer

- Não adicionar NuGet, banco, arquivo JSON/SQLite, API, UI web ou framework sem pedido explícito.
- Não refatorar o app inteiro para OOP, Clean Architecture ou arquivos extras “porque seria mais correto”.
- Não mudar o `TargetFramework` nem o tipo do projeto (continua `OutputType` Exe).
- Não persistir tarefas entre execuções; o estado é só em memória.
- Não alterar `README.md`, respostas da avaliação, template de PR ou evidências a menos que a tarefa peça isso.
- Não inventar funcionalidades fora do pedido (filtros, prioridade, prazo, usuários).
- Não remover `Console.ReadLine()` no final sem motivo: o app espera Enter antes de fechar.
- Não reescrever `Concluir` de um jeito que quebre o contrato: id inexistente simplesmente não altera a lista.

## Como estender (quando pedido)

Uma função nova deve: operar na lista `tarefas`, ter nome em português, caber no mesmo `Program.cs` e ser demonstrada no fluxo do console se fizer sentido (chamar depois das tarefas de exemplo, como já acontece com `Concluir(1)`).
>>>>>>> parent of bab4e30 (Simplificar o CLAUDE.md com o guia do GerenciadorDeTarefas.)
