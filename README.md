# 🧪 Find Mottu — Quality Assurance (QA) de API

### Garantindo eficiência, rastreabilidade e qualidade na gestão de pátios de motos da Mottu 🚀  
Este documento descreve os processos de testes de API aplicados à aplicação **Find Mottu**, desenvolvida em **Java + Spring Boot**, com **autenticação JWT** e **banco de dados SQL Server**.

---

## 🧑‍🤝‍🧑 Informações dos Contribuintes

| Nome | Matrícula | Turma |
|------|------------|--------|
| Felipe Nogueira Ramon | 555335 | 2TDSPH |
| Gustavo de Souza Amorim | 556999 | 2TDSPW |
| Pedro Henrique Vasco Antonieti | 556253 | 2TDSPH |

---

## 📌 Visão do Problema

Os pátios de motos da **Mottu** enfrentavam dificuldades de **organização, localização e rastreabilidade** das motocicletas, gerando **lentidão operacional** e **falhas de controle**.  
O processo de **QA** foi projetado para garantir a **confiabilidade da API** responsável por resolver esses problemas, validando cada endpoint e assegurando o correto funcionamento do sistema de rastreamento e cadastro.

---

## 🎯 Objetivos do QA

- ✅ Validar todos os endpoints REST (CRUD completo)  
- 🔒 Garantir o funcionamento da autenticação JWT  
- ⚙️ Automatizar testes de requisições e respostas via Postman  
- 🧩 Assegurar a integridade dos dados armazenados no banco SQL Server  
- 🗂️ Padronizar scripts de validação e armazenamento de variáveis  
- 📊 Monitorar a estabilidade e consistência das respostas da API  

---

## 📈 Resultados Esperados

- 🔄 **100% de cobertura** dos endpoints principais  
- ⚙️ **Respostas consistentes** e com status adequados (`200`, `201`, `204`, `401`, `404`)  
- 🔐 **Validação JWT** funcional e segura  
- ⏱️ **Redução no tempo de execução** dos testes manuais  
- 🧠 **Rastreabilidade completa** de cada ciclo CRUD  

---

## 🏗️ Arquitetura Testada

| Camada | Tecnologia |
|--------|-------------|
| **Backend** | Java 17 + Spring Boot |
| **Banco de Dados** | SQL Server |
| **Autenticação** | JWT (Spring Security) |
| **Interface** | API REST |
| **Testes de QA** | Postman / Newman |
| **Formato de Dados** | JSON UTF-8 |

---

## 🧩 Escopo de Testes

| Módulo | Endpoint Base | Objetivo |
|---------|----------------|-----------|
| **Login** | `/login` | Autenticação e geração de JWT |
| **Validação de Token** | `/auth/validate` | Verificar validade do token |
| **Usuários** | `/usuarios` | CRUD completo de usuários |
| **Motos** | `/motos` | Gerenciamento das motos cadastradas |
| **Filiais** | `/filiais` | Controle de filiais e endereços |
| **Localizações** | `/localizacoes` | Registro e consulta de posições de motos |

---

## ⚙️ Ambiente de Teste

| Configuração | Valor |
|---------------|--------|
| **Base URL** | `http://localhost:8080/api` |
| **Autenticação** | JWT via `Authorization: Bearer {{token}}` |
| **Ferramenta de Teste** | Postman |
| **Execução Automática** | Newman (CLI) |
| **Banco de Dados** | SQL Server |
| **Ambiente** | Localhost / QA Server |
| **Formato** | JSON UTF-8 |

---

## 🧾 Estrutura dos Testes (Postman)

Find Mottu - API Tests/
├── Login/
│ ├── POST Login
│ └── POST Validate Token
├── Usuários/
│ ├── POST Criar Usuário
│ ├── GET Consultar Usuário
│ ├── PUT Atualizar Usuário
│ └── DELETE Remover Usuário
├── Motos/
│ ├── POST Criar Moto
│ ├── GET Consultar Moto
│ ├── PUT Atualizar Moto
│ └── DELETE Remover Moto
├── Filiais/
│ ├── POST Criar Filial
│ ├── GET Consultar Filial
│ ├── PUT Atualizar Filial
│ └── DELETE Remover Filial
└── Localizações/
├── POST Criar Localização
├── GET Consultar Localização
├── PUT Atualizar Localização
└── DELETE Remover Localização


---

## 🧪 Exemplos de Testes (Postman)

### 👤 **POST /usuarios**

**Body:**
```json
{
  "primeiroNome": "Gustavo",
  "sobrenome": "Amorim",
  "email": "gustavo.amorim@empresa.com",
  "cargo": "Técnico de Monitoramento",
  "idade": 28,
  "idFilial": 10
}

Test Script:

pm.test("Status 201 - Usuário criado com sucesso", () => {
    pm.response.to.have.status(201);
});

pm.test("Response contém ID do usuário", () => {
    const json = pm.response.json();
    pm.expect(json).to.have.property("id");
    pm.environment.set("usuarioId", json.id);
});


🔒 POST /login
Body:

{
  "email": "usuario@mottu.com",
  "senha": "123456"
}

Test Script:

pm.test("Status 200 - Login efetuado", () => {
    pm.response.to.have.status(200);
});

const token = pm.response.json().token;
pm.environment.set("token", token);

🏍️ POST /motos

Body:

{
  "idQrCode": "MOTO_001_QR",
  "idImei": 100000000000001,
  "numChassi": "CHS0012025",
  "numMotor": 20251,
  "modeloMoto": "Honda CG 160 Start",
  "placaMoto": "ABC1D23",
  "statusMoto": "ATIVA",
  "filial": {
    "endereco": "Rua dos Pátios, 123 - São Paulo"
  }
}

✅ Boas Práticas de QA Aplicadas

Scripts Postman reutilizáveis com variáveis de ambiente

Testes independentes e idempotentes

Armazenamento automático de IDs (motoId, usuarioId, etc.)

Validação da estrutura JSON em todas as respostas

Automação via Newman (pronto para CI/CD)

Evidências exportáveis (.json / .html reports)

🎥 Links Importantes

📽️ Apresentação do Projeto: YouTube

💻 Azure DevOps: Challenge QA

🧠 Conclusão

O processo de QA do Find Mottu assegura a confiabilidade, segurança e estabilidade de todos os endpoints da aplicação.
Com testes de API automatizados e validados via Postman + JWT, o sistema garante:

🔍 Controle completo de cadastro e rastreamento de motos

🔐 Validação contínua da autenticação JWT

🧾 Auditoria das movimentações e cadastros

💾 Integração segura com o banco SQL Server

🏁 Resultado Final

✅ APIs seguras, funcionais e prontas para integração com o sistema de monitoramento e pátios da Mottu.
