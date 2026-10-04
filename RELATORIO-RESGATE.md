# Relatório de Resgate
- Equipe: Alexandre dos Santos, Pedro Queiroz, Jose Mauro, Lucas Lopes
- Branch de trabalho: resgate/equipe-01

## Diagnóstico

### Problemas que impactam a copilação:
Commit: 64f88f6 (release-dev) - A pasta util e a classe Validador.java foram excluídas. Como esses componentes são referenciados por outras partes do projeto, a exclusão provoca erros de compilação nas classes que dependem deles.

Commit a70ee84 (release-dev) — O parâmetro endereco, necessário para a criação de um objeto Mercadoria, foi removido. Além disso, o método responsável por salvar a Mercadoria foi renomeado apenas na camada service, enquanto a classe MercadoriaRepository manteve a nomenclatura anterior, gerando uma inconsistência entre as camadas e, consequentemente, erros de compilação.

### Problemas que impactam na compreensão do projeto:
Commit: 0cd80f6 (release-dev) - O README original foi substituído por uma versão simplificada, ocasionando a perda de informações importantes sobre a configuração e a execução do projeto. Com isso, as instruções necessárias para executar a aplicação deixaram de estar disponíveis na documentação.

### Problemas que impactam a segurança do projeto
Commit 6572d8a (release-dev) — O arquivo application.properties passou a expor variáveis que contêm credenciais. A presença de credenciais diretamente no repositório representa um risco de exposição de informações sensíveis e pode permitir acesso não autorizado aos recursos associados.

Commit 9a6d3b0 (release-dev) — A lógica de autenticação do usuário foi alterada de forma incorreta. O login é considerado bem-sucedido quando apenas o usuário ou apenas a senha está correta, em vez de exigir que ambas as credenciais sejam válidas. Essa falha permite a autenticação de usuários sem a validação adequada das credenciais.

## Comandos Git utilizados

### 1. Listagem de branches

```bash
git branch -a
```

**Finalidade:** lista as branches locais e remotas conhecidas pelo repositório.

### 2. Histórico de commits

```bash
git log --oneline --all --graph --decorate
```

**Finalidade:** exibe o histórico de commits de forma compacta e gráfica.

- `--oneline`: resume cada commit em uma linha.
- `--all`: considera todas as referências de commits.
- `--graph`: representa visualmente as ramificações.
- `--decorate`: exibe referências como branches e tags.
 
### 3. Inspeção de um commit

```bash
git show <hash>
```

**Finalidade:** exibe os detalhes de um commit específico, incluindo metadados, mensagem, arquivos modificados e diferenças no código em relação ao seu commit pai.

### 4. Restauração do arquivo EntregaService.java

```bash
 git restore --source=4574eee -- .\src\main\java\br\edu\entregas\service\EntregaService.java
 ```

 **Finalidade:** restaura o arquivo EntregaService.java para a versão existente no commit 4574eee, substituindo seu conteúdo atual no diretório de trabalho, sem alterar o histórico de commits.

### 5. Restauração da pasta util e do arquivo Validador.java

 ```bash
git restore --source=4574eee -- .\src\main\java\br\edu\entregas\util .\src\main\java\br\edu\entregas\util\Validador.java
  ```

**Finalidade:** restaura a pasta util e o arquivo Validador.java para as versões existentes no commit 4574eee, recuperando o código anterior sem alterar o histórico de commits.

### 6. Restauração do arquivo LoginService.java

 ```bash
git restore --source=4574eee -- .\src\main\java\br\edu\entregas\service\LoginService.java
  ```

**Finalidade:** restaura o arquivo LoginService.java para a versão existente no commit 4574eee, recuperando o código anterior sem alterar o histórico de commits.

### 7. Restauração do arquivo README.md

 ```bash
git restore --source=7fe8faa -- .\README.md
```

**Finalidade:**restaura o arquivo README.md para a versão existente no commit 7fe8faa, recuperando a documentação anterior sem alterar o histórico de commits.

### 8. Remoção de arquivo do controle de versão

 ```bash
git rm --cached config/application.properties
```

**Finalidade:**Remove o arquivo config/application.properties do controle de versão do Git mantendo-o intacto no disco.

## Commits relevantes

### Hashes Investigados:
- `64f88f6` (branch: `release-dev`)
- `a70ee84` (branch: `release-dev`)
- `0cd80f6` (branch: `release-dev`)
- `6572d8a` (branch: `release-dev`)
- `9a6d3b0` (branch: `release-dev`)
- `7fe8faa` (branch: `docs-readme`)

### Hashes Restaurados:
- `4574eee` (branch: `main`)
- `7fe8faa` (branch: `docs-readme`)

## Validação final
Após a aplicação das correções na branch `resgate/equipe-01`, foram realizadas as seguintes validações:

- **Compilação:** os componentes removidos no commit `64f88f6` foram restaurados a partir do commit `4574eee`, incluindo a pasta `util` e a classe `Validador.java`. Também foi restaurado o código de `EntregaService.java`, corrigindo as inconsistências identificadas no processo de compilação.

- **Cadastro de mercadoria:** o arquivo `EntregaService.java` foi restaurado para recuperar o construtor de `Mercadoria` e a chamada ao método de salvamento, corrigindo a inconsistência introduzida pelo commit `a70ee84`.

- **Login:** o arquivo `LoginService.java` foi restaurado para a versão do commit `4574eee`, recuperando a lógica de autenticação e garantindo que o acesso dependa da validação correta das credenciais.

- **Documentação:** o `README.md` foi restaurado para a versão do commit `7fe8faa`, recuperando as informações necessárias para configuração e execução do projeto.

- **Segurança:** o arquivo `config/application.properties`, que continha informações sensíveis, foi removido do controle de versão com `git rm --cached`. A pasta/configuração foi adicionada ao `.gitignore` para evitar que o arquivo seja versionado novamente.

- **Histórico:** as correções foram realizadas na branch `resgate/equipe-01`, preservando o histórico original dos commits investigados e registrando as alterações de resgate em novos commits.
