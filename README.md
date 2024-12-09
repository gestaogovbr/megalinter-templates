# Megalinter e pre-commit

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
