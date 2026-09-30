---
name: adicionar-funcionalidade
description: Adiciona uma nova funcionalidade (ex.: remover tarefa, listar pendentes, editar título) ao Program.cs do GerenciadorDeTarefas seguindo o estilo já existente no código. Use sempre que o usuário pedir para criar, estender ou alterar uma operação sobre as tarefas do console app.
---

# Adicionar funcionalidade ao GerenciadorDeTarefas

Skill para a tarefa recorrente de **estender o `Program.cs`** mantendo o estilo do projeto (C# / .NET 8, console app com top-level statements).

## Quando usar

- "Adiciona um método para remover tarefa"
- "Quero listar só as pendentes"
- "Permite editar o título de uma tarefa"
- Qualquer pedido de nova operação sobre a lista de tarefas.

Não use para: criar projetos novos, trocar de framework, ou mudar a estrutura do repositório.

## Passo a passo

1. **Leia `GerenciadorDeTarefas/Program.cs` inteiro** antes de escrever qualquer coisa. Não assuma como ele está — confira.
2. **Identifique o padrão existente.** Hoje o código funciona assim:
   - Estado em variáveis no topo: `tarefas` (`List<(int Id, string Titulo, bool Concluida)>`) e `proximoId`.
   - Cada operação é uma **função local** declarada no topo do arquivo (`Adicionar`, `Concluir`, `Listar`), sem classes, sem arquivos novos.
   - O "programa principal" (chamadas e `Console.WriteLine`) fica **abaixo** das funções.
3. **Implemente a nova função local** seguindo as convenções abaixo.
4. **Demonstre o uso** no fluxo principal, abaixo das funções, com um cabeçalho no mesmo formato dos existentes: `Console.WriteLine("=== Descrição ===");` seguido de `Listar();`.
5. **Compile e rode** (veja "Verificação") e confira a saída no console.
6. **Resuma** para o usuário o que foi adicionado, em 2–4 linhas.

## Convenções de código (copiar do que já existe)

- **Idioma:** nomes de funções, variáveis e textos de saída em **português**, sem acento em identificadores (`Concluir`, `Listar`, `titulo`).
- **Nome de função:** verbo no infinitivo, PascalCase (`Remover`, `ListarPendentes`, `EditarTitulo`).
- **Parâmetros:** camelCase (`int id`, `string titulo`).
- **Dados:** continue usando a lista de tuplas nomeadas `(Id, Titulo, Concluida)`. Não crie classe/record `Tarefa` a menos que o usuário peça.
- **Saída:** formato `[X]` / `[ ]` + `#Id — Titulo` (com travessão `—`), igual ao `Listar()`. Se a nova função listar tarefas, reaproveite o formato.
- **Estilo:** chaves em linha própria, 4 espaços de indentação, `var` para variáveis locais, interpolação `$"..."`.
- **Nullable/ImplicitUsings** estão habilitados: não adicione `using` desnecessário.
- **Mudança mínima:** altere só o necessário. Não reformate, renomeie nem "melhore" código que não faz parte do pedido.

## Cuidados com a lista de tuplas

- Tuplas são **valores**: para alterar uma tarefa, **substitua o item** (`tarefas[i] = (...)`), como `Concluir` faz. Não tente `tarefas[i].Concluida = true` (não compila).
- Para remover, **não** use `foreach` com remoção dentro. Use `tarefas.RemoveAll(t => t.Id == id)` ou um `for` de trás para frente.
- **Nunca reaproveite ou reordene IDs** — `proximoId` só cresce.
- Se o `id` não existir, avise o usuário com `Console.WriteLine` em vez de falhar em silêncio ou lançar exceção.

## Verificação

Execute a partir da pasta do projeto:

```bash
cd GerenciadorDeTarefas
dotnet build
dotnet run
```

Checklist antes de dizer que terminou:

- [ ] `dotnet build` sem erros **nem warnings novos**.
- [ ] A saída do `dotnet run` mostra a nova funcionalidade funcionando.
- [ ] Cenário de borda testado (id inexistente, lista vazia, etc.).
- [ ] O comportamento anterior (`Adicionar`, `Concluir`, `Listar`) continua igual.
- [ ] Nenhum arquivo fora de `Program.cs` foi alterado (a não ser que o usuário tenha pedido).

> O programa termina com `Console.ReadLine()`; ao testar pelo terminal, pressione Enter para encerrar.

## O que NÃO fazer

- ❌ Criar novos arquivos, pastas, classes ou projetos sem pedido explícito.
- ❌ Adicionar pacotes NuGet ou alterar o `.csproj`.
- ❌ Mudar a assinatura ou o comportamento das funções existentes.
- ❌ Apagar o `Console.ReadLine()` ou o comentário final do arquivo.
- ❌ Mexer em `README.md`, `CLAUDE.md`, `EVIDENCIAS.md` ou na `.sln`.

## Exemplo de referência

Pedido: *"adiciona um método de remover tarefa"*

Função (junto das demais, antes do fluxo principal):

```csharp
void Remover(int id)
{
    var removidas = tarefas.RemoveAll(t => t.Id == id);

    if (removidas == 0)
    {
        Console.WriteLine($"Tarefa #{id} não encontrada.");
    }
}
```

Uso (depois do `Concluir(1);` e suas listagens):

```csharp
Console.WriteLine();
Console.WriteLine("=== Depois de remover a tarefa #2 ===");
Remover(2);
Listar();
```
