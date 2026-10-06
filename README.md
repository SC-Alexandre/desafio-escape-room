# Projeto Entregas

Sistema Java de console para controle de mercadorias e seus endereços de entrega.

## Requisitos
- Java 17 ou superior
- Maven 3.8 ou superior

## Compilar e executar
```bash
mvn clean package
java -cp target/classes br.edu.entregas.Main
```

## Acesso de demonstração
- Usuário: `admin`
- Senha: `12345678`

## Funcionamento atual
Após a autenticação, o sistema cadastra automaticamente uma mercadoria de exemplo e exibe as mercadorias cadastradas.

Exemplo:
```bash
=== SISTEMA DE ENTREGAS ===
Usuário: admin
Senha: 12345678
Acesso autorizado. Mercadorias cadastradas:
#1 | Notebook | Notebook corporativo | 2.1 kg | R$ 4500.00 | AGUARDANDO ENVIO | Entrega: Av. Goiás, 1000 - Sala 8, Goiânia/GO - CEP: 74000-000
```

## Modelo
Cada Mercadoria possui:
- `ID`
- `Nome`
- `Descrição`
- `Peso`
- `Valor`
- `Status`
- Um `endereço` de entrega

O endereço (`Endereco`) contém:

- `Logradouro`
- `Complemento`
- `Número`
- `CEP`
- `Cidade`
- `Estado`

## Validações
O cadastro verifica:

- Nome obrigatório
- Descrição obrigatória
- Peso positivo
- Valor positivo
- Endereço obrigatório

## Estrutura Principal
```
src/
└── main/
    └── java/
        └── br/edu/entregas/
            ├── Main.java
            ├── model/
            │   ├── Endereco.java
            │   └── Mercadoria.java
            ├── repository/
            │   └── MercadoriaRepository.java
            ├── service/
            │   ├── EntregaService.java
            │   └── LoginService.java
            └── util/
                └── Validador.java
```

## Fluxo recomendado
Use branches de funcionalidade, Pull Request e revisão antes do merge.
