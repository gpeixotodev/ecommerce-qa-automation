# E-commerce QA Automation — Professional Portfolio Project

Projeto de portfólio para **Analista de QA**, reunindo automação Web, testes de API, validações de banco, evidências, relatórios, CI e planejamento no Jira.

## Stack

- Python
- Selenium WebDriver / Selenium Manager
- Pytest
- Requests
- SQLite (banco local de teste)
- pytest-html
- pytest-json-report
- Git / GitHub
- GitHub Actions
- Jira

## Cenários Web

1. Login válido
2. Login inválido
3. Usuário vazio
4. Senha vazia
5. Adição de produto ao carrinho
6. Remoção de produto do carrinho

## Cenários API

Usamos o DummyJSON como API pública de teste. A documentação oficial disponibiliza recursos de produtos e endpoints GET/POST para prototipação e testes. 

- GET /products
- GET /products/1
- POST /products/add

## Banco de dados

O projeto usa SQLite em arquivo temporário apenas para demonstrar:

- criação de schema;
- INSERT;
- SELECT;
- validação da persistência.

Nenhuma credencial de banco real é necessária.

## Evidências

Quando um teste Web falha, o `conftest.py` salva automaticamente um screenshot em:

```text
screenshots/
```

## Relatórios

Execute:

```bash
pytest --json-report --json-report-file=reports/pytest.json
```

Ou:

```bash
pytest --html=reports/report.html --self-contained-html
```

Para gerar o dashboard:

```bash
python scripts/generate_dashboard.py
```

## Execução completa

```bash
pytest --json-report --json-report-file=reports/pytest.json --html=reports/report.html --self-contained-html
python scripts/generate_dashboard.py
```

Arquivos gerados:

```text
reports/report.html
reports/pytest.json
reports/dashboard.html
```

## Jira

O arquivo `jira-backlog.csv` pode ser utilizado para planejamento/importação manual.

Para integração real com Jira Cloud, use variáveis de ambiente:

```text
JIRA_BASE_URL=https://suaempresa.atlassian.net
JIRA_EMAIL=seu-email
JIRA_API_TOKEN=seu-token
JIRA_PROJECT_KEY=QA
```

Depois:

```bash
python scripts/jira_create_issue.py "Automatizar checkout" "Criar cenário de checkout automatizado."
```

Nunca comite o token.

## Git

```bash
git init
git add .
git commit -m "feat: initial professional QA automation suite"
git branch -M main
git remote add origin <URL-DO-SEU-REPOSITORIO>
git push -u origin main
```

## GitHub Actions

O workflow `.github/workflows/tests.yml` executa:

1. Checkout
2. Setup Python
3. Instalação do Chrome
4. Instalação das dependências
5. Suite Web + API + Banco
6. Relatório HTML/JSON
7. Dashboard
8. Upload dos artefatos

## Estrutura

```text
ecommerce-qa-automation/
├── api/
│   └── dummyjson_client.py
├── data/
│   └── test_data.py
├── database/
│   └── db.py
├── pages/
│   ├── login_page.py
│   ├── products_page.py
│   └── cart_page.py
├── scripts/
│   ├── generate_dashboard.py
│   └── jira_create_issue.py
├── tests/
│   ├── api/
│   ├── database/
│   └── ui/
├── reports/
├── screenshots/
├── .github/workflows/tests.yml
├── conftest.py
├── jira-backlog.csv
├── test-cases.csv
├── pytest.ini
└── requirements.txt
```

## Objetivo de negócio

Reduzir regressões em fluxos críticos, acelerar a validação de releases e gerar evidências objetivas para apoiar decisões de qualidade.

## Observação

A automação Web utiliza o SauceDemo como ambiente de demonstração. Os testes de API utilizam o DummyJSON como serviço de teste público; as alterações do DummyJSON são simuladas e não persistem no servidor.
