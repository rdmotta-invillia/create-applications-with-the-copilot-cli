## Passo 3: Expandir a Funcionalidade da Calculadora

Joãozinho quer expandir a calculadora com operações adicionais criando uma nova issue e trabalhando com o Copilot CLI para implementar as melhorias.

### 📖 Teoria: Desenvolvimento Iterativo com o Copilot CLI

#### Mantendo o Ritmo com o Copilot CLI

O Copilot CLI standalone ajuda a manter o ritmo de desenvolvimento ao:

- Gerar código rapidamente para novos recursos usando os modelos de IA mais recentes
- Sugerir melhores práticas e padrões
- Ajudar a depurar e testar novas funcionalidades
- Reduzir a troca de contexto mantendo você no terminal
- Lidar com comandos shell de longa duração de forma mais eficiente
- Suportar automação aprimorada com o modo headless `-p`

#### Delegando Tarefas Maiores

Para tarefas mais complexas, você pode usar o comando `/delegate` exemplificado abaixo para atribuir trabalho ao Copilot coding agent:

> ```bash
> copilot
> ```
>
> ```text
> /delegate Add modulo, exponentiation, and square root functions to calculator.js with proper error handling
> ```

O Copilot coding agent irá:

1. Criar uma nova branch automaticamente
2. Abrir um draft pull request
3. Trabalhar na tarefa de forma autônoma
4. Transmitir a saída para o seu terminal
5. Solicitar sua revisão quando estiver completo

> [!NOTE]
> Usar o comando `/delegate` para utilizar o Copilot Coding Agent (CCA) consumirá premium requests da sua assinatura do GitHub Copilot. O Copilot CLI também pode ser usado com modelos regulares, que não consomem premium requests.

#### Fluxos de Trabalho de Teste e Melhoria

À medida que você adiciona recursos, o Copilot CLI pode ajudá-lo a:

- Gerar casos de teste para novas operações
- Sugerir edge cases a considerar
- Criar documentação
- Refatorar código para melhor manutenibilidade
- Salvar e compartilhar suas sessões de desenvolvimento usando `/share`

> [!IMPORTANT]
> Se você reiniciou seu codespace, pode ser necessário executar `copilot --allow-all --enable-all-github-mcp-tools` e depois autenticar com o GitHub novamente executando `!gh auth login` de dentro da sessão do Copilot CLI.

> [!NOTE]
> A opção `--allow-all` no Copilot CLI habilita todas as permissões de uma vez:
> é equivalente a `--allow-all-tools`, `--allow-all-paths` e `--allow-all-urls`.
> Isso permite que o CLI acesse qualquer caminho de arquivo, use qualquer ferramenta e acesse qualquer URL sem pedir confirmação.
> Use com cautela, pois concede ao CLI acesso total e capacidades de automação.

### ⌨️ Atividade: Adicionar Mais Operações à Calculadora

1. Inicie uma sessão interativa do Copilot CLI (se ainda não estiver em uma sessão):

   > ![Static Badge](https://img.shields.io/badge/Terminal-text?logo=gnometerminal&labelColor=0969da&color=ddf4ff)
   >
   > ```bash
   > copilot --allow-all --enable-all-github-mcp-tools
   > ```

1. Peça ao Copilot CLI para ajudá-lo a criar outra issue para expandir a calculadora:

   > ![Static Badge](https://img.shields.io/badge/CLI-Prompt-text?style=flat-square&logo=github-copilot&labelColor=8250df&color=fbefff)
   >
   > ```prompt
   > Create a GitHub issue for a Node.js CLI calculator app using the feature_request.md template 
   > as the markdown format.
   > I want to request a feature to add more operations including 
   > - modulo
   > - exponentiation (power)
   > - square root
   > Create the issue directly for the current owner and repository in this session on github.com using the `gh` CLI commands.
   > List the issue link when complete
   > ```

1. Trabalhe com o Copilot CLI para implementar as novas operações:

   > ![Static Badge](https://img.shields.io/badge/CLI-Prompt-text?style=flat-square&logo=github-copilot&labelColor=8250df&color=fbefff)
   >
   > ```prompt
   > Add these functions to my existing calculator.js based on latest issue created:
   > 1. modulo(a, b) - returns the remainder of a divided by b
   > 2. power(base, exponent) - returns base raised to the exponent
   > 3. squareRoot(n) - returns the square root of n with error handling for negative numbers
   > ```

   1. Opcionalmente, use o modo headless:

      > ![Static Badge](https://img.shields.io/badge/CLI-Prompt-text?style=flat-square&logo=github-copilot&labelColor=8250df&color=fbefff)
      >
      > ```prompt
      > copilot -p "Add these functions to my existing calculator.js based on latest issue created:
      > 1. modulo(a, b) - returns the remainder of a divided by b
      > 2. power(base, exponent) - returns base raised to the exponent
      > 3. squareRoot(n) - returns the square root of n with error handling for negative numbers"
      > ```

1. Teste suas novas funções e adicione testes:

   > ![Static Badge](https://img.shields.io/badge/CLI-Prompt-text?style=flat-square&logo=github-copilot&labelColor=8250df&color=fbefff)
   >
   > ```prompt
   > Add tests for the new calculator operations: 
   > - Expand tests based on the following example:
   >   - @images/calc-extended-operations.png
   > - Add new tests for the new operations to the existing src/tests/calculator.test.js file
   > - Use a popular Node.js testing framework if one isn't installed
   > - Make sure to include edge case tests like square root of negative numbers
   > - Make sure all tests run and pass
   > ```

1. Faça commit das suas alterações:

   > ![Static Badge](https://img.shields.io/badge/CLI-Prompt-text?style=flat-square&logo=github-copilot&labelColor=8250df&color=fbefff)
   >
   > ```prompt
   > Add all calculator and test files to git.
   > Commit with message "Implemented additional calculator operations and tests: 
   > modulo, power, square root" 
   > Push the changes
   > ```

1. Aguarde um momento para Mona verificar seu trabalho, fornecer feedback e compartilhar a próxima lição.

> [!TIP]
> Use `/share gist` na sua sessão do Copilot CLI para salvar sua sessão do exercício GitHub Skills como um GitHub gist para referência futura!

<details>
<summary>Está com problemas? 🤷</summary><br/>

- Certifique-se de que o título da sua issue inclui "Calculator" ou "Operations"
- O arquivo calculator.js deve exportar funções que possam ser requeridas/importadas
- Você pode testar operações manualmente usando o Node.js REPL: `node` e depois digite seu código
- Para raiz quadrada de números negativos, considere retornar `NaN` ou lançar um erro
- Lembre-se de fazer commit e push de quaisquer alterações de código que você fizer
- Use `copilot --help` para ver todas as opções de comando disponíveis

</details>
