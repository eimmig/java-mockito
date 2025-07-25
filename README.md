# Sistema de Leilões - Projeto Mockito

Este é um projeto Java Spring Boot que implementa um sistema de leilões online. O projeto foi desenvolvido como parte do aprendizado sobre testes unitários utilizando o framework **Mockito**.

## 📋 Sobre o Projeto

O sistema permite:
- Cadastro e autenticação de usuários
- Criação e gerenciamento de leilões
- Realização de lances em leilões ativos
- Finalização automática de leilões expirados
- Geração de pagamentos
- Envio de emails de notificação

## 🛠️ Tecnologias Utilizadas

- **Java 8**
- **Spring Boot 2.3.4**
- **Spring Security** - Autenticação e autorização
- **Spring Data JPA** - Persistência de dados
- **Thymeleaf** - Template engine para páginas web
- **H2 Database** - Banco de dados em memória
- **JUnit 5** - Testes unitários
- **Mockito** - Framework para mocking em testes
- **Maven** - Gerenciamento de dependências
- **Bootstrap** - Estilização das páginas

## 📁 Estrutura do Projeto

```
src/
├── main/
│   ├── java/br/com/alura/leilao/
│   │   ├── LeilaoApplication.java           # Classe principal
│   │   ├── controller/                      # Controllers MVC
│   │   │   ├── ErrorController.java
│   │   │   ├── IndexController.java
│   │   │   ├── LanceController.java
│   │   │   ├── LeilaoController.java
│   │   │   └── LoginController.java
│   │   ├── dao/                             # Data Access Objects
│   │   │   ├── LanceDao.java
│   │   │   ├── LeilaoDao.java
│   │   │   ├── PagamentoDao.java
│   │   │   └── UsuarioDao.java
│   │   ├── dto/                             # Data Transfer Objects
│   │   │   ├── NovoLanceDto.java
│   │   │   └── NovoLeilaoDto.java
│   │   ├── model/                           # Entidades JPA
│   │   │   ├── Lance.java
│   │   │   ├── Leilao.java
│   │   │   ├── Pagamento.java
│   │   │   └── Usuario.java
│   │   ├── security/                        # Configurações de segurança
│   │   │   ├── LeilaoUserDetails.java
│   │   │   ├── UserDetailsServiceImpl.java
│   │   │   └── WebSecurityConfig.java
│   │   └── service/                         # Serviços de negócio
│   │       ├── EnviadorDeEmails.java
│   │       ├── FinalizarLeilaoService.java
│   │       ├── GeradorDePagamento.java
│   │       └── LanceService.java
│   └── resources/
│       ├── application.properties           # Configurações da aplicação
│       ├── data.sql                        # Script de dados iniciais
│       ├── static/css/                     # Arquivos CSS
│       └── templates/                      # Templates Thymeleaf
└── test/
    └── java/
        ├── br/com/alura/leilao/service/    # Testes dos serviços
        │   ├── FinalizarLeilaoServiceTest.java
        │   └── GeradorDePagamentoTest.java
        └── leilao/
            └── HelloWorldMockito.java       # Exemplo básico do Mockito
```

## 🚀 Como Executar

### Pré-requisitos

- Java 8 ou superior
- Maven 3.6 ou superior

### Passos para execução

1. **Clone o repositório:**
   ```bash
   git clone <url-do-repositorio>
   cd java-mockito
   ```

2. **Compile e execute a aplicação:**
   ```bash
   mvn clean install
   mvn spring-boot:run
   ```

3. **Acesse a aplicação:**
   - Abra o navegador e acesse: `http://localhost:8080`

### Banco de Dados

O projeto utiliza o H2 Database em memória, que é automaticamente configurado na inicialização da aplicação. Os dados são carregados através do arquivo `data.sql`.

## 🧪 Executando os Testes

Para executar todos os testes:

```bash
mvn test
```

Para executar um teste específico:

```bash
mvn test -Dtest=FinalizarLeilaoServiceTest
```

## 📚 Conceitos de Mockito Demonstrados

O projeto demonstra os principais conceitos do framework Mockito:

### 1. Criação de Mocks
```java
@Mock
private LeilaoDao leilaoDao;

// ou

LeilaoDao mock = Mockito.mock(LeilaoDao.class);
```

### 2. Configuração de Comportamento
```java
Mockito.when(leilaoDao.buscarLeiloesExpirados())
       .thenReturn(leiloes);
```

### 3. Verificação de Chamadas
```java
Mockito.verify(leilaoDao).salvar(leilao);
```

### 4. Injeção de Dependências em Testes
```java
@BeforeEach
public void beforeEach() {
    MockitoAnnotations.initMocks(this);
    this.service = new FinalizarLeilaoService(leilaoDao, enviadorDeEmails);
}
```

## 🔧 Funcionalidades Principais

### Sistema de Autenticação
- Login/logout de usuários
- Controle de acesso baseado em papéis

### Gestão de Leilões
- Criação de novos leilões
- Listagem de leilões ativos
- Visualização de detalhes do leilão

### Sistema de Lances
- Realização de lances em leilões ativos
- Validação de regras de negócio para lances

### Finalização Automática
- Processamento de leilões expirados
- Determinação do lance vencedor
- Geração de pagamentos
- Envio de emails de notificação

## 📈 Objetivos de Aprendizado

Este projeto foi criado para demonstrar:

- **Testes Unitários com Mockito:** Como criar mocks, configurar comportamentos e verificar interações
- **Injeção de Dependências:** Como testar classes com dependências externas
- **Isolamento de Testes:** Como testar unidades de código de forma isolada
- **Padrões de Teste:** Boas práticas na escrita de testes automatizados

## 🤝 Contribuindo

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.

## 👨‍💻 Autor

Projeto desenvolvido como parte do curso de Mockito da Alura.

---

⭐ Se este projeto te ajudou, não esqueça de dar uma estrela!