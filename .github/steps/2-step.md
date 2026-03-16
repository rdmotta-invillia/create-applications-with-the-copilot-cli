## Passo 2: Trabalhar na Issue da Calculadora com o Copilot CLI

Com a issue criada, Joãozinho trabalha com o Copilot CLI standalone de forma interativa para começar a construir a aplicação calculadora.

### 📖 Teoria: Desenvolvimento Colaborativo com o Copilot CLI

#### Desenvolvimento Interativo com o Copilot CLI

O Copilot CLI standalone (comando `copilot`) oferece uma experiência interativa rica para desenvolvimento:

- Inicie uma sessão simplesmente executando `copilot` no seu terminal
- Tenha conversas naturais sobre seu código e obtenha sugestões inteligentes
- Gere código boilerplate com base nos seus requisitos
- Use os modelos de IA mais recentes para respostas de ponta
- `/share [file|gist] [path]` - Compartilhe a sessão em arquivo markdown ou GitHub gist

#### Custom Agents

O Copilot CLI suporta custom agents que você pode definir no seu repositório:

- Crie perfis de agentes no diretório `.github/agents/`
- Codifique prompts especializados, seleções de ferramentas e fluxos de trabalho
- Invoque agentes usando o comando `/agent <name>`
- Ótimo para documentação, infraestrutura, segurança ou tarefas específicas de domínio

#### Delegando Tarefas

Quando você tem tarefas maiores, pode delegá-las ao Copilot coding agent:

- Use `/delegate TASK-DESCRIPTION` para atribuir trabalho
- O Copilot cria uma nova branch e um draft pull request
- O coding agent trabalha de forma autônoma em segundo plano
- Revise as alterações quando estiverem completas

> [!NOTE]
> Referências:
>
> - [Using GitHub Copilot CLI](https://docs.github.com/en/copilot/how-tos/use-copilot-agents/use-copilot-cli)
> - [Custom agents in Copilot CLI](https://github.blog/changelog/2025-10-28-github-copilot-cli-use-custom-agents-and-delegate-to-copilot-coding-agent/)
> - [About custom agents](https://docs.github.com/en/copilot/concepts/agents/coding-agent/about-custom-agents)

> [!IMPORTANT]
> Se você reiniciou seu codespace, pode ser necessário executar `copilot --allow-all --enable-all-github-mcp-tools` e depois autenticar com o GitHub novamente executando `!gh auth login` no Copilot CLI.

### ⌨️ Atividade: Criar uma Nova Branch para a Aplicação Calculadora

1. Inicie uma nova sessão interativa do Copilot CLI (feche a sessão anterior com `/exit`):

   > ![Static Badge](https://img.shields.io/badge/Terminal-text?logo=gnometerminal&labelColor=0969da&color=ddf4ff)
   >
   > ```bash
   > copilot --allow-all --enable-all-github-mcp-tools
   > ```

> [!NOTE]
> A opção `--allow-all` no Copilot CLI habilita todas as permissões de uma vez:
> é equivalente a `--allow-all-tools`, `--allow-all-paths` e `--allow-all-urls`.
> Isso permite que o CLI acesse qualquer caminho de arquivo, use qualquer ferramenta e acesse qualquer URL sem pedir confirmação.
> Use com cautela, pois concede ao CLI acesso total e capacidades de automação.

2. Crie e faça push de uma nova branch chamada `create-calc-app`:

   > ![Static Badge](https://img.shields.io/badge/CLI-Prompt-text?style=flat-square&logo=github-copilot&labelColor=8250df&color=fbefff)
   >
   > ```prompt
   > Create and push a new branch called 'create-calc-app'
   > ```

<details>
<summary>Está com problemas? 🤷</summary><br/>

Use o comando `!` no Copilot CLI para executar comandos shell diretamente da sua sessão de chat. Por exemplo, para criar e fazer push da branch sem sair do chat:

 ```prompt
 !git checkout -b create-calc-app && git push -u origin create-calc-app
 ```

 Verifique a branch atual depois:

 ```prompt
 !git branch --show-current
 ```
</details>

### ⌨️ Atividade: Gerar Código da Calculadora com o Copilot CLI Baseado em uma Imagem

1. Peça ao Copilot CLI para ajudá-lo a criar as funções da calculadora com base na imagem e na issue do GitHub criada anteriormente:

   > ![Static Badge](https://img.shields.io/badge/CLI-Prompt-text?style=flat-square&logo=github-copilot&labelColor=8250df&color=fbefff)
   >
   > ```prompt
   > @images/js-calculator.png help me create a Node.js CLI calculator app 
   > based only on the four basic math operations in this image and outlined
   > in the latest issue in this owner/repository.
   > Create the code and put it in the 'src' directory.
   > Make sure the calculator is commented with the operations it supports.
   > ```

   1. Opcionalmente, use o modo headless com um prompt:

      > ![Static Badge](https://img.shields.io/badge/Terminal-text?logo=gnometerminal&labelColor=0969da&color=ddf4ff)
      >
      > ```bash
      > copilot -p "@images/js-calculator.png help me create a Node.js CLI calculator app 
      > based only on the four basic math operations in this image and outlined
      > in the latest issue in this owner/repository.
      > Create the code and put it in the 'src' directory.
      > Make sure the calculator is commented with the operations it supports."
      > ```

> [!NOTE]
> Embora este exemplo use uma imagem de uma calculadora JavaScript web, ele demonstra como você pode usar arquivos (incluindo imagens) com o Copilot CLI para fornecer contexto para suas solicitações.

2. Execute e teste as funções da sua calculadora pedindo ao Copilot CLI:

   > ![Static Badge](https://img.shields.io/badge/CLI-Prompt-text?style=flat-square&logo=github-copilot&labelColor=8250df&color=fbefff)
   >
   > ```prompt
   > Run and test the calculator functions with some example operations 
   > shown in the image @images/calc-basic-operations.png.
   > ```

3. Peça ao Copilot CLI para criar testes abrangentes para as funções da calculadora:

   > ![Static Badge](https://img.shields.io/badge/CLI-Prompt-text?style=flat-square&logo=github-copilot&labelColor=8250df&color=fbefff)
   >
   > ```prompt
   > Create comprehensive unit tests for all the calculator functions:
   > - Expand tests based on the following example:
   >   - @images/calc-basic-operations.png
   > - Add these tests to a src/tests/calculator.test.js file
   > - Use a popular Node.js testing framework if one isn't installed
   > - addition, subtraction, multiplication, and division
   > - test edge cases like division by zero
   > - Make sure all tests run and pass
   > ```

> [!NOTE]
> Pressione ctrl+o para ver a saída dos testes aprovados que o Copilot CLI executou para você!
  
4. Quando estiver satisfeito com o código, faça commit das suas alterações pelo Copilot CLI:

   > ![Static Badge](https://img.shields.io/badge/CLI-Prompt-text?style=flat-square&logo=github-copilot&labelColor=8250df&color=fbefff)
   >
   > ```prompt
   > Add all calculator and test files to git.
   > Commit with message "Implement basic calculator operations and tests: 
   > addition, subtraction, multiplication, division"
   > Push the changes
   > ```

5. Aguarde um momento para Mona verificar seu trabalho, fornecer feedback e compartilhar a próxima lição.

> [!TIP]
> Você pode colar ou arrastar e soltar imagens no Copilot CLI para fornecer contexto visual para suas perguntas!

> [!NOTE]
> Fazer push das suas alterações acionará o workflow para verificar seu trabalho e preparar o próximo passo!

<details>
<summary>Está com problemas? 🤷</summary><br/>

- Certifique-se de estar no diretório do repositório ao executar comandos
- O comando `copilot` requer Node.js 22+ instalado
- Se a autenticação falhar, execute `copilot` e siga os prompts de login
- Você também pode editar o arquivo calculator.js manualmente com base nas sugestões do Copilot
- Lembre-se de exportar suas funções usando `module.exports`

</details>
