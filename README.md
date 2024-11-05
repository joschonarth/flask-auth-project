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

📌 1. Clone o repositório:

```bash
git clone https://github.com/joschonarth/flask-sample-auth
```

📌 2. Entre na pasta do projeto:

```bash
cd flask-sample-auth
```

📌 3. Crie um ambiente virtual:

```bash
python -m venv .venv
```

📌 4. Ative o ambiente ambiente virtual:

```bash
.venv\Scripts\activate
```

📌 5. Instale as dependências do projeto que estão no arquivo [`requirements.txt`](requirements.txt):

```bash
pip install -r requirements.txt
```

📌 6. Execute o arquivo [`docker-compose.yml`](docker-compose.yml) para baixar e rodar a imagem do MySQL:

```bash
docker-compose up -d
```

📌 7. Abra o `Flask Shell` no terminal e crie as tabelas no banco de dados:

- Primeiro, abra o Flask shell:

    ```bash
    flask shell
    ```
- Depois, dentro do Flask Shell, crie as tabelas:

    ```bash
    db.create_all()
    ```
- Salve as alterações no banco de dados:

    ```bash
    db.sessions.commit()
    ```
- Saia do Flask Shell:

    ```bash
    exit()
     ```

📌 8. Inicie o servidor de desenvolvimento:

```bash
python app.py
```

## 🌐 Acesso à API
A API estará disponível em: [http://127.0.0.1:5000](http://127.0.0.1:5000)

## 🔗 Endpoints

### ✍️ Criar Usuário
- **Descrição**: Cria um novo usuário com senha criptografada.
- **Método**: `POST`
- **Endpoint**: `/user`

🌐 **Exemplo de Requisição**: `http://localhost:5000/user`

```json
{
    "username": "novousuario",
    "password": "123456"
}
```

📄 **Exemplo de Resposta:**

```json
{
    "message": "Usuário cadastrado com sucesso!"
}
```

### 🔓 Fazer Login
- **Descrição**: Autentica um usuário e inicia uma sessão.
- **Método**: `POST`
- **Endpoint**: `/login`

🌐 **Exemplo de Requisição**: `http://localhost:5000/login`

```json
{
    "username": "novousuario",
    "password": "123456"
}
```

📄 **Exemplo de Resposta:**

```json
{
    "message": "Login realizado com sucesso!"
}
```

### 🚪 Fazer Logout
- **Descrição**: Encerra a sessão de um usuário autenticado.
- **Método**: `GET`
- **Endpoint**: `/logout`

🌐 **Exemplo de Requisição**: `http://localhost:5000/logout`

📄 **Exemplo de Resposta:**

```json
{
    "message": "Logout realizado com sucesso!"
}
```

### 👁️ Ler Usuário
- **Descrição**: Recupera as informações de um usuário específico.
- **Método**: `GET`
- **Endpoint**: `/user/{id_user}`

🌐 **Exemplo de Requisição**: `http://localhost:5000/user/{id_user}`

📄 **Exemplo de Resposta:**

```json
{
    "username": "novousuario"
}
```

### 🔄 Atualizar Usuário
- **Descrição**: Atualiza a senha do usuário autenticado.
- **Método**: `PUT`
- **Endpoint**: `/user/{id_user}`

🌐 **Exemplo de Requisição**: `http://localhost:5000/user/{id_user}`

```json
{
    "password": "654321"
}
```

📄 **Exemplo de Resposta:**

```json
{
    "message": "Usuário novousuario atualizado com sucesso!"
}
```

### 🗑️ Deletar Usuário
- **Descrição**: Exclui um usuário. Ação restrita ao administrador.
- **Método**: `DELETE`
- **Endpoint**: `/user/{id_user}`

🌐 **Exemplo de Requisição**: `http://localhost:5000/user/{id_user}`

📄 **Exemplo de Resposta:**

```json
{
    "message": "Usuário novousuario deletado com sucesso!"
}
```

## 🛠️ Comandos Úteis do `Flask Shell`

```bash
# Cria todas as tabelas definidas nos Models
db.create_all()

# Deleta todas as tabelas do banco de dados
db.drop_all()

# Salva as alterações no banco de dados
db.session.commit()

# Cancela as alterações pendentes do banco de dados que ainda não foram salvas definitivamente.
db.session.rollback()

# Consulta todos os registros de uma tabela específica (exemplo com a tabela 'User')
User.query.all()

# Consulta um registro específico por ID (exemplo com a tabela 'User')
User.query.get(1)

# Adiciona um novo registro no banco de dados (exemplo com a tabela 'User')
new_user = User(username="username", password="123456")
db.session.add(new_user)

# Atualiza um registro existente no banco de dados (exemplo com a tabela 'User')
user = User.query.get(1)
user.username = "new_username"

# Deleta um registro específico do banco de dados (exemplo com a tabela 'User')
user_to_delete = User.query.get(1)
db.session.delete(user_to_delete)

# Sai do shell
exit()
```

## 🤝 Contribuindo

Se você deseja contribuir com o projeto, fique à vontade para abrir uma pull request ou uma issue.

## 📞 Contato

<div>
    <a href="https://www.linkedin.com/in/joschonarth/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" target="_blank"></a>
    <a href="mailto:joschonarth@gmail.com" target="_blank"><img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white" target="_blank"></a>
</div>