# 🔒 Projeto de Autenticação de Usuário em Flask

Este é um projeto de API de autenticação de usuário construído com Flask. Ele inclui operações de login, logout, registro de usuário e controle de acesso a informações e operações sensíveis, utilizando SQLAlchemy para gerenciamento de banco de dados e Flask-Login para autenticação de sessão.

## ⚙️ Funcionalidades

- 🔑 **Registro de Usuário**: Criação de novos usuários, com senha criptografada, armazenada no banco de dados.
- 🔓 **Login**: Autenticação de usuário com verificação de senha utilizando bcrypt.
- 🚪 **Logout**: Encerramento de sessão para usuários autenticados.
- 📋 **CRUD de Usuário**:
  - 👤 **Consulta de Usuário**: Obtenção de informações de um usuário específico.
  - ✏️ **Atualização de Senha**: Modificação da senha do usuário autenticado.
  - ❌ **Deleção de Usuário**: Exclusão de um usuário, restrito ao administrador.

## 🛠️ Tecnologias Utilizadas

- 🐍 **Python** - Linguagem de programação utilizada.
- 🔥 **Flask** - Framework web em Python.
- 🐬 **MySQL** - Banco de dados relacional.
- 🐳 **Docker** - Para conteinerização da aplicação.

## 📚 Bibliotecas Utilizadas

- 🔗 [Flask-SQLAlchemy](https://flask-sqlalchemy.palletsprojects.com/en/latest/) - Integração do SQLAlchemy com Flask.
- 🔑 [Flask-Login](https://flask-login.readthedocs.io/en/latest/) - Gerenciamento de sessão de login.
- ⚙️ [Werkzeug](https://werkzeug.palletsprojects.com/en/latest/) - Utilitário WSGI para Flask.
- 💾 [pymysql](https://pymysql.readthedocs.io/en/latest/) - Driver para integração com MySQL.
- 🛡️ [cryptography](https://cryptography.io/en/latest/) - Biblioteca de criptografia para Python.
- 🔒 [bcrypt](https://pypi.org/project/bcrypt/) - Para hashing seguro de senhas.


## 🚀 Como Rodar o Projeto

1. Clone o repositório:

```bash
git clone https://github.com/joschonarth/flask-sample-auth
```

2. Entre na pasta do projeto:

```bash
cd flask-sample-auth
```

3. Crie um ambiente virtual:

```bash
python -m venv .venv
```

4. Ative o ambiente ambiente virtual:

```bash
.venv\Scripts\activate
```

5. Instale as dependências do projeto que estão no arquivo [`requirements.txt`](requirements.txt):

```bash
pip install -r requirements.txt
```

6. Execute o arquivo [`docker-compose.yml`](docker-compose.yml) para baixar e rodar a imagem do MySQL:

```bash
docker-compose up -d
```

7. Inicie o servidor de desenvolvimento:

```bash
python app.py
```

🌐 A aplicação estará disponível em `http://127.0.0.1:5000`.


## 🛠️ Comandos Úteis do `Flask Shell`

```bash
# Cria todas as tabelas definidas nos modelos
db.create_all()

# Para deletar todas as tabelas (use com cuidado)
db.drop_all()

# Salva as alterações no banco de dados
db.session.commit()

# Sai do shell
exit()
```