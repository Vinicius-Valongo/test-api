# 🚀 User Management API - Automated Testing Suite


Projeto de testes automatizados para API de gerenciamento de usuários usando **Newman** (Postman CLI) com integração completa de **CI/CD via GitHub Actions**.

## 📋 Índice

- [Sobre o Projeto](#sobre-o-projeto)
- [Pré-requisitos](#pré-requisitos)
- [Instalação](#instalação)
- [Executando os Testes](#executando-os-testes)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Cobertura de Testes](#cobertura-de-testes)
- [CI/CD Pipeline](#cicd-pipeline)
- [Relatórios](#relatórios)
- [API Testada](#api-testada)

## 🎯 Sobre o Projeto

Este projeto implementa uma **suíte completa de testes automatizados** para uma API RESTful de gerenciamento de usuários, garantindo **100% de cobertura** dos endpoints e cenários de teste.

### Funcionalidades Testadas

- ✅ **Autenticação JWT**
- ✅ **CRUD completo de usuários**
- ✅ **Validações de campos obrigatórios**
- ✅ **Tratamento de erros**
- ✅ **Testes de duplicação**
- ✅ **Rate limiting**


## 📦 Pré-requisitos

Antes de começar, certifique-se de ter instalado:

- [Node.js](https://nodejs.org/) v18+ 
- [npm](https://www.npmjs.com/) ou [yarn](https://yarnpkg.com/)
- [Git](https://git-scm.com/)

## 🚀 Instalação

1. Clone o repositório:
```bash
git clone https://github.com/YOUR_USERNAME/user-management-api.git
cd user-management-api
```

2. Instale as dependências:
```bash
npm install
```

## ▶️ Executando os Testes

### Localmente

#### Execução simples (output no terminal):
```bash
npm test
```

#### Execução com relatórios HTML e JSON:
```bash
npm run test:report
```

#### Execução para CI (com supressão de exit codes):
```bash
npm run test:ci
```

### Via GitHub Actions

Os testes são executados automaticamente:
- ✅ Em cada **push** para `main` ou `develop`
- ✅ Em cada **pull request**
- ✅ Diariamente às **9h UTC** (agendamento)
- ✅ Manualmente via **workflow_dispatch**

## 📁 Estrutura do Projeto

```
user-management-api/
├── .github/
│   └── workflows/
│       └── api-tests.yml          # Pipeline CI/CD
├── postman/
│   ├── User-Management-API.postman_collection.json  # Coleção de testes
│   └── environments/
│       └── production.postman_environment.json      # Variáveis de ambiente
├── reports/                        # Relatórios gerados (git ignored)
├── .gitignore
├── package.json
└── README.md
```

## 🎯 Cobertura de Testes

### Endpoints Cobertos (100%)

| Método | Endpoint | Cenários Testados |
|--------|----------|-------------------|
| POST | `/login` | ✅ Login bem-sucedido<br>✅ Credenciais inválidas |
| GET | `/usuarios` | ✅ Listar todos os usuários<br>✅ Validar estrutura da resposta |
| GET | `/usuarios/{id}` | ✅ Buscar usuário por ID<br>✅ Usuário não encontrado |
| POST | `/usuarios` | ✅ Criar usuário com sucesso<br>✅ Email duplicado<br>✅ Campos obrigatórios<br>✅ Email inválido |
| PUT | `/usuarios/{id}` | ✅ Atualizar usuário existente<br>✅ Criar se não existir<br>✅ Email duplicado |
| DELETE | `/usuarios/{id}` | ✅ Deletar usuário com sucesso<br>✅ Usuário não encontrado |

### Total de Testes

- **17 requests** testadas
- **67 assertions** implementadas
- **100% de cobertura** dos endpoints
- **100% de cobertura** dos cenários críticos

## 🔄 CI/CD Pipeline

### Workflow do GitHub Actions

O pipeline executa automaticamente:

1. **Checkout** do código
2. **Setup** do Node.js 20
3. **Instalação** de dependências
4. **Execução** dos testes Newman
5. **Upload** de artefatos (relatórios)
6. **Publicação** de resumo
7. **Quality Gate** - Validação de qualidade

### Artefatos Gerados

Após cada execução, os seguintes artefatos ficam disponíveis por **30 dias**:

- 📄 **HTML Report** - Relatório visual completo
- 📊 **JSON Report** - Dados estruturados para análise
- 📈 **Test Results** - Todos os resultados consolidados

### Quality Gate

O pipeline implementa um **quality gate** que:
- ❌ **Falha** se houver qualquer teste com erro
- ✅ **Passa** apenas se 100% dos testes forem bem-sucedidos

## 📊 Relatórios

### Relatório HTML

Após executar `npm run test:report`, abra o arquivo:
```
reports/newman-report.html
```

O relatório inclui:
- 📈 Estatísticas gerais
- 🎯 Resultados por request
- ⏱️ Tempos de resposta
- ✅ Assertions passadas/falhas
- 📋 Detalhes completos de cada teste

### Relatório JSON

Para integração com outras ferramentas:
```
reports/newman-report.json
```

## 🌐 API Testada

**Base URL**: `https://serverest.dev`

### Documentação Completa
[https://serverest.dev/](https://serverest.dev/)

### Credenciais de Teste
```json
{
  "email": "fulano@qa.com",
  "password": "teste"
}
```

## 📝 Exemplos de Requests

### Autenticação
```bash
POST https://serverest.dev/login
Content-Type: application/json

{
  "email": "fulano@qa.com",
  "password": "teste"
}
```

### Criar Usuário
```bash
POST https://serverest.dev/usuarios
Content-Type: application/json

{
  "nome": "Fulano da Silva",
  "email": "fulano@example.com",
  "password": "senha123",
  "administrador": "true"
}
```

## 🔧 Configuração de Ambiente

As variáveis de ambiente estão em:
```
postman/environments/production.postman_environment.json
```

Principais variáveis:
- `baseUrl` - URL base da API
- `adminEmail` - Email do administrador
- `adminPassword` - Senha do administrador
- `authToken` - Token JWT (gerado automaticamente)

