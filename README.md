# 🛠 Helpdesk

Repositório orquestrador do projeto **Helpdesk**, que une o backend e o frontend — mantidos em repositórios próprios — para facilitar a execução local do sistema completo com um único comando.

| Repositório | Papel |
|---|---|
| [`helpdesk-api`](https://github.com/jnobr3c/helpdesk-api) | Backend (Java 11 + Spring Boot) — incluído como *submodule* |
| [`helpdesk-front`](https://github.com/jnobr3c/helpdesk-front) | Frontend (Angular 12) — incluído como *submodule* |

> Este repositório **não contém código próprio**. Ele apenas referencia os dois projetos originais via `git submodule` e fornece um script de conveniência para subir os dois ao mesmo tempo.

---

## ✅ Pré-requisitos

- **Java 11** + **Maven**
- **Node.js** (18+) e **npm**
- **Angular CLI** (`npm install -g @angular/cli`)
- Git

---

## 📥 Clonando o projeto (com os submodules)

Como o backend e o frontend são *submodules*, um `git clone` normal **não traz o código deles**. Use um dos comandos abaixo:

```bash
# opção 1: clonar já trazendo os submodules
git clone --recurse-submodules https://github.com/jnobr3c/helpdesk.git

# opção 2: se já clonou sem o --recurse-submodules
git clone https://github.com/jnobr3c/helpdesk.git
cd helpdesk
git submodule update --init --recursive
```

---

## ▶️ Rodando front e back juntos

Na raiz do repositório:

```bash
npm install
npm run dev
```

Isso executa em paralelo:
- `helpdesk-api` → `mvn spring-boot:run` → sobe em `http://localhost:8080`
- `helpdesk-front` → `npm install && ng serve` → sobe em `http://localhost:4200`

Acesse **http://localhost:4200** no navegador. O frontend já está configurado para consumir a API em `localhost:8080` (`helpdesk-front/src/app/config/api.config.ts`).

Para rodar cada parte separadamente:

```bash
npm run dev:api     # só o backend
npm run dev:front   # só o frontend
```

---

## 🔄 Atualizando os submodules

Como cada projeto evolui em seu próprio repositório, de tempos em tempos é preciso atualizar a referência aqui:

```bash
cd helpdesk-api
git pull origin main
cd ../helpdesk-front
git pull origin main
cd ..
git add helpdesk-api helpdesk-front
git commit -m "chore: atualiza submodules"
git push
```

---

## 📚 Documentação

- Documentação completa da arquitetura do sistema (fluxo JWT, modelo de domínio, endpoints): ver [`helpdesk-documentacao-completa.md`](https://github.com/jnobr3c/helpdesk/blob/main/helpdesk-documentacao-completa.md)
- README específico do backend: [`helpdesk-api/README.md`](https://github.com/jnobr3c/helpdesk-api)
- README específico do frontend: [`helpdesk-front/README.md`](https://github.com/jnobr3c/helpdesk-front)

---

## 👨‍💻 Autor

José Nobre
🔗 [GitHub](https://github.com/jnobr3c) · 🔗 [LinkedIn](https://www.linkedin.com/in/jos%C3%A9-nobrec/)
