# RAMON AUTOS PEÇAS

Ramon Autopeças é uma **vitrine digital moderna** que funciona como ponte entre o cliente e a loja oficial no Mercado Livre. Diferente de um e-commerce tradicional, o foco é na **apresentação profissional do catálogo** e na **facilitação do contato** via WhatsApp para negociação direta.

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

O Mercado Livre é a única fonte de verdade. Qualquer alteração manual no banco local é sobrescrita na próxima sincronização.

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

## Licença

© 2026 Ramon Autopeças. Todos os direitos reservados.

Este projeto é de propriedade exclusiva da Ramon Autopeças. Qualquer uso, reprodução ou distribuição não autorizada deste código é estritamente proibida.

---

## Desenvolvimento

**Desenvolvido por:** [Arthur Lanznaster](https://github.com/arthurlanz) e [Pedro Henrique Rodrigues](https://github.com/BlackVSK)

**Localização:** Joinville, SC - Brasil