# Django Basico

## Ambiente de Dev

Dependências do projeto

```
postgresql
postgresql-contrib
libpq-dev
python-psycopg2
python-pip
```

Variáveis do template `templates/settings.py.j2`

- `dbname`: Nome do banco de dados
- `dbuser`: Usuário do banco de dados
- `dbpassword`: Senha do banco de dados

O template `templates/settings.py.j2` deve substituir o arquivo `djangobasico/settings.py`

O arquivo de __fixtures__, dados iniciais do banco de dados, é o `db.fixture.json`

### Acesso

Para rodar o projeto:

```
python manage.py runserver 0:8000
```

O acesso deve ser feito através do `localhost:8000`.
