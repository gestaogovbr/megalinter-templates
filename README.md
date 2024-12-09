# Megalinter e pre-commit
O Mega-Linter é uma ferramenta de linting poderosa que ajuda a garantir a qualidade e a consistência do código em projetos de software. Ele suporta mais de 50 tipos de arquivos e 49 linguagens de programação, além de formatos de documentos e configurações. Mega-Linter automatiza a execução de linters (ferramentas de análise estática de código) e fornece relatórios detalhados para ajudar equipes de desenvolvimento a identificar e corrigir problemas. (ChatGPT)

O pre-commit é uma ferramenta que permite configurar e gerenciar ganchos de pré-commit (pre-commit hooks) para repositórios Git. Esses ganchos são scripts ou comandos que são executados automaticamente antes de um commit ser concluído. O objetivo principal é garantir que o código enviado ao repositório esteja em conformidade com padrões de qualidade, estilo e outras regras definidas pela equipe ou pelo desenvolvedor. (ChatGPT)


## Rodando Megalinter como pre-commit (máquina local)

1. Criar os arquivos .megalinter.yml e .pre-commit.config.yaml na raiz do repositório.
2. Definir no arquivo megalinter.yml os linters a serem ativados
3. Instalar a aplicação pre-commit na máquina local (pode ser necessário criar um venv)
   ```
   pre-commit install
   ```
4. Testar o pre-commit no repositório
   ```
   pre-commit run --all-files --verbose
   ```
5. Caso as configurações não tenham sido aplicadas:
   ```
   pre-commit install --install-hooks
   ```
   Verificar na pasta .git/hooks se os hooks do pre-commit existem.
6. Por padrão os erros estão sendo tratados como warning. Para bloquear o commit alterar a variável no arquivo .megalinter.yml
   ```
   DISABLE_ERRORS: false
   ```

7. Para habilitar a correção automática de código:
   ```
   APPLY_FIXES: all
   ```

## Rodando Megalinter no pós-commit (CI/CD)

Para inserir as regras de linter no repositório para todos os usuários via Github Actions, seguir os passos:

1. Criar o arquivo .github/workflows/mega-linter.yml, com base no template disponível.

2. Assim que criado um novo Pull Request, o Megalinter vai rodar o actions com o relatório de erros e correções.