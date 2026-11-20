# aulaExemploIA

## Executar front-end e API

1. Configure o PostgreSQL em `backend/.env`, usando `backend/.env.example` como modelo.
2. Em um terminal, na raiz do projeto, execute `npm run dev:backend`.
3. Em outro terminal, execute `npm run dev:frontend`.
4. Acesse o endereço informado pelo Vite (normalmente `http://localhost:8080`).

O front consulta a API em `http://localhost:3000` por padrão. Para usar outro endereço,
defina `VITE_API_URL` em `frontend/.env` (veja `frontend/.env.example`). Em produção,
configure também `FRONTEND_ORIGIN` no ambiente do back-end com a origem do front-end.

Os dados da interface são persistidos no PostgreSQL pela API; o front-end não usa mais
uma lista simulada.