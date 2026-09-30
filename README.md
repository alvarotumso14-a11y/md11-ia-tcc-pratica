# Avaliação Individual — Módulo 11 — Tecnologias Emergentes e IA

**Data de entrega:** DD/MM/AAAA
**Formato:** individual, de consulta aberta — use slides, anotações e a própria IA à vontade para pesquisar e testar suas respostas.

## Como participar

1. Faça um **fork** deste repositório.
2. Clone o seu fork localmente.
3. Responda as questões teóricas **direto neste README**, abaixo de cada uma.
4. Complete a parte prática (veja abaixo) editando `CLAUDE.md`, `.claude/skills/minha-skill/SKILL.md` e `EVIDENCIAS.md`.
5. Abra um **Pull Request** do seu fork de volta para este repositório.

> O PR não será mergeado — ele existe só para eu avaliar o seu diff. Pode deixar aberto depois de enviar.

O objetivo não é decorar definições, e sim demonstrar que você entende os conceitos e sabe aplicá-los para ganhar eficiência ao usar IA no seu projeto de TCC. Responda com suas próprias palavras — copiar e colar resposta pronta de IA sem entender não demonstra o aprendizado esperado.

---

## Questões dissertativas

### Questão 1 — O que é um "agent"?
O que é um "agent" (agente de IA)? Explique com suas próprias palavras e dê um exemplo de situação em que faz mais sentido usar um agente do que um chat comum.

**Sua resposta:**
Um agente de IA é um sistema que recebe um objetivo, analisa o que precisa ser feito e pode executar uma sequência de ações usando ferramentas, verificando os resultados ao longo do processo. Um chat comum normalmente responde à solicitação com texto, enquanto um agente pode, por exemplo, consultar arquivos, executar testes e corrigir um erro. No projeto GerenciadorDeTarefas, faria mais sentido usar um agente para investigar por que uma operação de tarefas falha, localizar o código relacionado, propor uma correção e rodar os testes. Para uma pergunta conceitual simples, um chat comum seria suficiente.

### Questão 2 — O que são guidelines?
O que são "guidelines" (diretrizes) ao usar uma IA generativa? Qual é o papel delas na qualidade das respostas geradas pelo modelo?

**Sua resposta:**
Guidelines são instruções e critérios que orientam como a IA deve trabalhar e responder. Podem definir o contexto do projeto, o público, o estilo, as ferramentas permitidas, os limites e o formato esperado. Elas melhoram a relevância e a consistência das respostas e ajudam a evitar sugestões incompatíveis com o projeto. Não garantem que a resposta esteja correta: ainda é necessário revisar o resultado.

### Questão 4 — Escolha de modelo e nível de esforço
Qual modelo de IA utilizar para cada tipo de tarefa? Dê um exemplo de tarefa simples e outra mais complexa, explicando como você escolheria o modelo em cada caso. O que é o "nível de esforço" (effort level) e quando faz sentido aumentá-lo ou diminuí-lo?

**Sua resposta:**
Eu escolheria o modelo considerando a dificuldade, o risco e o custo da tarefa. Para uma tarefa simples, como corrigir a ortografia de uma mensagem ou explicar uma função pequena, usaria um modelo rápido e econômico. Para uma tarefa complexa, como analisar a arquitetura do aplicativo, rastrear um erro que envolve várias classes ou propor uma alteração com impacto em diferentes partes do sistema, escolheria um modelo mais capaz e com bom desempenho em programação. O nível de esforço indica quanto raciocínio e recursos o modelo deve dedicar à resposta. Eu o aumentaria para problemas ambíguos, com várias etapas ou consequências importantes, e diminuiria para tarefas diretas e rotineiras, em que uma resposta rápida é suficiente.

### Questão 5 — Como estruturar um bom prompt
Descreva os elementos que tornam um prompt mais eficaz (ex.: contexto, objetivo, formato esperado, exemplos, restrições).

**Sua resposta:**
Um bom prompt informa o contexto necessário, descreve claramente o objetivo e delimita o que deve ou não ser feito. Também pode indicar o formato da resposta, critérios de qualidade, exemplos do resultado desejado e restrições, como manter a linguagem usada no projeto ou não alterar arquivos fora do escopo. Por exemplo: "No GerenciadorDeTarefas, analise o método que marca uma tarefa como concluída; explique primeiro o comportamento atual, identifique possíveis erros e sugira uma alteração pequena. Não modifique outros métodos e apresente os testes que devo executar." Quanto mais específico e verificável for o pedido, menor a chance de receber uma resposta genérica ou fora do escopo.

### Questão 6 — Iteração de prompt
O que significa "iterar" um prompt? Por que a primeira resposta de uma IA geralmente não é a versão final, e como você usaria a resposta recebida para melhorar o próximo prompt?

**Sua resposta:**
Iterar um prompt significa fazer novas solicitações com base no que aconteceu na tentativa anterior. A primeira resposta pode interpretar o pedido de outra forma, deixar de considerar algum detalhe ou propor algo amplo demais, porque a IA trabalha com as informações fornecidas e pode cometer erros. Eu compararia a resposta com o objetivo, apontaria o que faltou ou ficou incorreto e acrescentaria contexto ou critérios concretos no próximo prompt. Por exemplo, depois de uma sugestão de correção, eu poderia informar o erro observado e pedir uma solução menor que preserve o comportamento já existente.

### Questão 7 — Zero-shot vs. few-shot
Qual é a diferença entre um prompt "zero-shot" e um prompt "few-shot"? Dê um exemplo de situação em que vale a pena incluir exemplos dentro do próprio prompt.

**Sua resposta:**
Em um prompt zero-shot, a IA recebe a tarefa sem exemplos de como deve produzir o resultado. Em um prompt few-shot, são fornecidos um ou mais exemplos de entrada e da saída esperada para orientar o padrão. Vale incluir exemplos quando o formato ou a classificação desejada é específico. Por exemplo, para pedir que a IA organize tarefas em categorias como "pendente", "em andamento" e "concluída", eu mostraria alguns títulos e suas categorias corretas. Assim, ela tem referências concretas para seguir, embora os exemplos não substituam a revisão do resultado.

### Questão 8 — Memória e contexto entre sessões
O que significa uma IA "ter memória" entre sessões diferentes de conversa? Por que, em um projeto longo como o TCC, é importante decidir o que precisa ser "lembrado" e como fornecer esse contexto para a IA a cada nova conversa?

**Sua resposta:**
Ter memória entre sessões significa conseguir reutilizar informações de conversas anteriores, em vez de começar sempre sem contexto. Isso pode ocorrer por meio de recursos de memória da ferramenta ou de arquivos de orientação do projeto. Em um projeto longo, é importante registrar informações estáveis e úteis, como objetivo, tecnologias, convenções e restrições, para que as respostas continuem coerentes. Também é importante não guardar tudo: detalhes temporários ou dados sensíveis podem ser irrelevantes ou inadequados. Se a ferramenta não recuperar essas informações automaticamente, devo fornecer os arquivos ou um resumo atualizado no início da nova conversa.

### Questão 9 — Avaliar a resposta da IA
Antes de aplicar a sugestão de uma IA no seu projeto, como você verifica se ela está correta? Descreva pelo menos 2 formas práticas de checar a confiabilidade de uma resposta gerada por IA.

**Sua resposta:**
Eu não aplicaria uma sugestão só porque ela parece convincente. Primeiro, compararia a resposta com a documentação oficial e com o código e os requisitos do projeto, verificando se as APIs, premissas e comportamentos citados realmente existem. Depois, executaria os testes relevantes e, se necessário, criaria um teste pequeno para reproduzir o caso. Também revisaria o diff para procurar efeitos colaterais e pediria uma segunda análise ou consultaria outra fonte quando o tema fosse importante. Essas verificações ajudam a encontrar erros, mas não eliminam a necessidade de julgamento humano.

### Questão 10 — Dividir tarefas complexas em etapas
Por que, em tarefas mais complexas, pode ser melhor dividir o trabalho em um fluxo de etapas (ex.: primeiro classificar/organizar, depois processar, depois revisar) em vez de pedir tudo em um único prompt? Dê um exemplo aplicado a uma tarefa do seu TCC.

**Sua resposta:**
Dividir uma tarefa complexa em etapas torna o processo mais claro e fácil de conferir. Cada etapa tem um objetivo menor, e um erro pode ser encontrado antes de afetar as etapas seguintes. Também fica mais simples ajustar o trabalho sem pedir tudo novamente. No GerenciadorDeTarefas, se eu precisasse adicionar uma opção para filtrar tarefas concluídas, começaria identificando onde as tarefas são armazenadas e exibidas; depois definiria e implementaria o filtro; por fim, revisaria a alteração e testaria listas vazias, tarefas concluídas e tarefas pendentes. Assim, consigo validar cada parte e manter a mudança dentro do escopo.

> **Questão 3** (como escrever um bom CLAUDE.md) e a **Questão 11** (prática, evidência de uso real da IA) são respondidas nos próprios arquivos `CLAUDE.md` e `EVIDENCIAS.md` — veja a parte prática abaixo.

---

## Parte prática

1. **Complete o `CLAUDE.md`** na raiz deste repositório — é onde você responde a Questão 3, documentando o projeto para orientar um assistente de IA.
2. **Complete a Skill** em `.claude/skills/minha-skill/SKILL.md`, com instruções reutilizáveis para uma tarefa recorrente do projeto. Renomeie a pasta `minha-skill/` para o nome real da sua skill.
3. **Conecte um assistente de IA ao código local** (Claude Code, GitHub Copilot, Cursor, ou outro de sua escolha) e use-o pelo menos uma vez de verdade, aplicando o `CLAUDE.md` e/ou a Skill que você criou em uma tarefa real do projeto `GerenciadorDeTarefas`.
4. **Complete o `EVIDENCIAS.md`** — é onde você responde a Questão 11, documentando essa experiência (ferramenta usada, prompt exato, o que a IA fez, se seguiu suas instruções).

### O que NÃO fazer

- ❌ Copiar as respostas, o CLAUDE.md ou a Skill de um colega
- ❌ Inventar uma evidência que não aconteceu de verdade
- ❌ Alterar arquivos fora do escopo pedido

## Sobre o projeto de exemplo

Dentro de `GerenciadorDeTarefas/` tem um console app simples em C# — um gerenciador de tarefas fictício — que serve de base para você praticar. Não é necessário adicionar funcionalidades novas ao app; o foco é a configuração e o uso da IA em cima desse código.

Abra `GerenciadorDeTarefas.sln` no Visual Studio, ou rode pelo terminal:

```bash
cd GerenciadorDeTarefas
dotnet run
```

---

## Critérios de avaliação (10 pontos)

| Critério | Pontos |
|---|---|
| Questões dissertativas (conjunto) | 4 |
| `CLAUDE.md` bem estruturado e específico ao projeto (Questão 3) | 2 |
| Skill funcional e realmente reutilizável | 2 |
| `EVIDENCIAS.md` — uso real da IA, seguindo (ou não) o CLAUDE.md/Skill (Questão 11) | 1 |
| Qualidade do Pull Request (descrição clara, organizado, dentro do escopo) | 1 |

## Entrega

Envie o **link do seu Pull Request** pelo Akademos até a data acima.
