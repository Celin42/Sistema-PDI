# Sistema-PDI
Este repositório contém o projeto do meu Trabalho de Conclusão de Curso (TCC).

Esta é uma Plataforma web para ensino de Processamento Digital de Imagens (PDI). Permite que alunos façam upload de uma imagem original e de sua própria implementação de um algoritmo, comparem resultados via RMSE e, se a similaridade for satisfatória, recebam o código‑fonte como feedback.

Sumário

Pré‑requisitos

Estrutura do Projeto

Configuração do Banco de Dados

Instalação e Execução

Backend

Frontend

Uso

Algoritmos Disponíveis


Pré‑requisitos

Node.js (v14+) e npm — https://nodejs.org/

Python 3.7+ e pip — https://www.python.org/

PostgreSQL (v12+) — https://www.postgresql.org/

Estrutura do Projeto

root/
├── sistema-pdi-backend/       # Backend (Node.js + Express + scripts Python)
│   ├── py-algorithms/         # Scripts Python (OpenCV)
│   ├── routes/                # Definição de rotas Express
│   ├── services/              # pythonRunner.js, compareService.js
│   ├── models/                # db.js, userModel.js
│   ├── middleware/            # upload.js (Multer)
│   ├── temp/                  # Saída temporária (auto)
│   ├── uploads/               # Uploads de usuários (auto)
│   ├── .env                   # Variáveis de ambiente
│   └── server.js              # Ponto de entrada
└── sistema-pdi-frontend/      # Frontend (Vue.js)
    ├── src/
    │   ├── components/        # Header, Footer, FormInput
    │   ├── views/             # home-page, login, register
    │   ├── auth/              # auth-state.js
    │   ├── routes.js          # Rotas Vue
    │   └── main.js            # Bootstrap Vue
    ├── public/
    └── package.json

Configuração do Banco de Dados

No PostgreSQL, crie o banco:

CREATE DATABASE sistema_pdi;

Crie a tabela de usuários:

CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  matricula VARCHAR(50) NOT NULL,
  email VARCHAR(100) NOT NULL UNIQUE,
  senha VARCHAR(255) NOT NULL
);

Em sistema-pdi-backend/.env, configure:

DB_USER=seu_usuario
DB_HOST=localhost
DB_DATABASE=sistema_pdi
DB_PASSWORD=sua_senha
DB_PORT=5432

Instalação e Execução

Backend

cd sistema-pdi-backend
npm install
# (Opcional) Python virtualenv
env: python -m venv venv
# Ativar:
# Linux/Mac: source venv/bin/activate
# Windows: .\venv\Scripts\activate
pip install opencv-python numpy
npm run dev # ou node server.js

O backend estará em http://localhost:3000/api/.

Frontend

cd sistema-pdi-frontend
npm install
npm run serve

O frontend estará em http://localhost:8080/.

Uso

Acesse http://localhost:8080/.

Registre-se com matrícula, e-mail e senha.

Faça login.

Carregue a imagem Original e a imagem Student (sua implementação).

Escolha o algoritmo e clique em Processar.

Veja o RMSE; se for menor que o limiar, o código‑fonte será exibido.

Algoritmos Disponíveis

Negativo

Tons de Cinza (Grayscale)

Otsu

Canny

Sobel

Suavização Gaussiana

Filtro da Média (Mean Filter)

Filtro de Realce (Sharpen)

Filtro de Realce Genérico (Unsharp Mask)

Espelhamento (Mirror)

Transposta

Rotação 90°

Equalização de Histograma
