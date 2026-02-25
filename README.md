# RAMON AUTOS PEÇAS

Sistema interno da Ramon Autopeças para sincronização, consulta e exposição de produtos do Mercado Livre.

A arquitetura é separada em dois projetos independentes:
- **Backend (API)** — fonte de verdade
- **Frontend (Vitrine)** — apenas visualização e contato

---

## Arquitetura Geral

```text
Mercado Livre
      ↓
Backend (Django + Celery)
      ↓
Frontend (Vue)
      ↓
Cliente final
```

---

## Backend (API)

Responsável por:
- OAuth com Mercado Livre
- Sincronização de itens, preços e estoque
- Persistência em PostgreSQL
- Exposição via API REST protegida por JWT
- Processamento assíncrono com Celery

### Stack

- Python 3.11
- Django + Django REST Framework
- PostgreSQL
- Celery
- Redis / Valkey
- JWT (SimpleJWT)

### Fonte de Verdade

O Mercado Livre é a única fonte de verdade.
Qualquer alteração manual no banco local é sobrescrita na próxima sincronização.

---

## Frontend (Vitrine)

Responsável por:
- Exibir catálogo sincronizado
- Facilitar contato via WhatsApp
- Redirecionar para anúncios no Mercado Livre

### Stack

- Vue 3
- Vite
- Pinia
- Vue Router

---

## Comunicação Entre Serviços

- Frontend não grava dados no backend
- Backend não depende do frontend
- Toda integração externa ocorre exclusivamente no backend

---

## Execução em Desenvolvimento

Backend:

```bash
docker compose up --build
```

Frontend:

```bash
npm install
npm run dev
```

---

## Licença

Proprietário e confidencial.
Uso restrito à Ramon Autopeças.

---

## Desenvolvimento

Sistema desenvolvido para uso interno e comercial da Ramon Autopeças.

