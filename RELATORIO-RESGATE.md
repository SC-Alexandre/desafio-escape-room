# Relatório de Resgate
- Equipe: Alexandre dos Santos, Pedro Queiroz, Jose Mauro, Lucas Lopes
- Branch de trabalho: resgate/equipe-01
## Diagnóstico
Descreva os problemas encontrados e suas evidências.

### Problemas que impactam a copilação:
Commit: 64f88f6 (release-dev) - A pasta util e a classe Validador.java foram excluídas. Como esses componentes são referenciados por outras partes do projeto, a exclusão provoca erros de compilação nas classes que dependem deles.

Commit a70ee84 (release-dev) — O parâmetro endereco, necessário para a criação de um objeto Mercadoria, foi removido. Além disso, o método responsável por salvar a Mercadoria foi renomeado apenas na camada service, enquanto a classe MercadoriaRepository manteve a nomenclatura anterior, gerando uma inconsistência entre as camadas e, consequentemente, erros de compilação.

### Problemas que impactam na compreensão do projeto:
Commit: 0cd80f6 (release-dev) - O README original foi substituído por uma versão simplificada, ocasionando a perda de informações importantes sobre a configuração e a execução do projeto. Com isso, as instruções necessárias para executar a aplicação deixaram de estar disponíveis na documentação.

### Problemas que impactam a segurança do projeto
Commit 6572d8a (release-dev) — O arquivo application.properties passou a expor variáveis que contêm credenciais. A presença de credenciais diretamente no repositório representa um risco de exposição de informações sensíveis e pode permitir acesso não autorizado aos recursos associados.

Commit 9a6d3b0 (release-dev) — A lógica de autenticação do usuário foi alterada de forma incorreta. O login é considerado bem-sucedido quando apenas o usuário ou apenas a senha está correta, em vez de exigir que ambas as credenciais sejam válidas. Essa falha permite a autenticação de usuários sem a validação adequada das credenciais.


## Comandos Git utilizados
Liste os comandos e explique a finalidade de cada um.

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
 
 
## Commits relevantes
Informe os hashes investigados, revertidos ou recuperados.

### Hashes Investigados:
commit: 64f88f6 (release-dev)
commit: a70ee84 (release-dev)
commit: 0cd80f6 (release-dev) 
commit: 6572d8a (release-dev) 
commit 9a6d3b0 (release-dev) 


## Validação final
Registre como a equipe confirmou compilação, login, cadastro, README e segurança.


