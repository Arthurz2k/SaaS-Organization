# Migração para o VS Code e arranque do projeto

> Guia de instalação e primeiro dia · 07/08/2026
> Corresponde à **Semana 1 — Fundação** do plano de desenvolvimento.

---

## 1. O que instalar

Instale nesta ordem. Cada linha tem o motivo, para você não instalar nada que não vá usar.

| Ferramenta | Por que | Onde |
|---|---|---|
| **Git** | Controle de versão. Configure `user.name` e `user.email` logo depois | git-scm.com |
| **Node.js LTS** | Runtime do Next.js e do backend. Instale a versão **LTS atual**, não a Current | nodejs.org |
| **pnpm** | Gerenciador de pacotes. Mais rápido e mais econômico em disco que o npm. `npm i -g pnpm` | — |
| **VS Code** | Editor | code.visualstudio.com |
| **Supabase CLI** | Migrações versionadas, tipos gerados e banco local. `pnpm add -g supabase` | — |
| **Docker Desktop** | Só se você quiser rodar o Supabase localmente. **Opcional na semana 1** — dá para trabalhar direto contra o projeto remoto no início | docker.com |

> **Sobre versões:** não vou citar números que não confirmei nesta sessão. Instale a LTS indicada no próprio site do Node no dia em que você fizer isso, e me diga qual foi — eu ajusto o `engines` do `package.json`.

### Extensões do VS Code

Essenciais para esta pilha:

- **ESLint** e **Prettier — Code formatter**
- **Tailwind CSS IntelliSense**
- **Prisma** ou **PostgreSQL** (realce de sintaxe em `.sql`)
- **Error Lens** — mostra o erro na própria linha, economiza muito tempo
- **GitLens** — histórico de linha, útil trabalhando sozinho
- **Claude Code** — ver seção 3

---

## 2. Contas necessárias

Todas no plano gratuito. **Custo total previsto na Fase 1: R$ 0**, com exceção do domínio.

| Serviço | Para quê | Quando criar |
|---|---|---|
| **GitHub** | Repositório privado | Semana 1 |
| **Supabase** | Banco, autenticação e storage | Semana 1 |
| **Vercel** | Hospedagem e deploy automático | Semana 1 |
| **Sentry** | Monitoramento de erro em produção | Semana 1 ou 2 |
| **Registro.br** ou similar | Domínio próprio (~R$ 40/ano) | **Semana 10** — depende do nome, que ainda não existe |
| **Resend** | E-mail transacional | Semana 11, junto com o convite |
| **UptimeRobot** ou similar | Verificação de disponibilidade | Semana 14 |

O teto de custo é R$ 100/mês com alerta em R$ 70 (`F10`). Os créditos de Google Cloud ficam guardados para quando o Supabase gratuito apertar.

---

## 3. Como me levar junto para o VS Code

O trabalho que fizemos aqui não migra sozinho — mas o **contexto** migra, e é isso que importa.

### O que instalar

O **Claude Code** roda no VS Code (extensão) ou no terminal integrado. Como eu não consegui confirmar a documentação nesta sessão, o caminho seguro é buscar por "Claude Code" no marketplace de extensões do VS Code, ou consultar `docs.claude.com/en/docs/claude-code`. Se você me mandar a página, eu te passo o passo a passo exato.

### O que faz a diferença de verdade

Dois arquivos, e não a ferramenta:

**`CLAUDE.md` na raiz do repositório.** Está pronto neste kit. Ele é lido automaticamente a cada sessão e carrega a pilha, as convenções, as nove regras invioláveis e a lista do que não fazer. É o que impede que uma sessão nova sugira criar tabela sem RLS ou texto literal em componente.

**A pasta `docs/`** com os onze arquivos que produzimos. Assim, quando você perguntar "o que faço esta semana", a resposta vem do plano real, não de suposição.

### Como fica a divisão de trabalho

| Aqui (Cowork) | No VS Code (Claude Code) |
|---|---|
| Revisão semanal de sexta | Escrever e rodar código |
| Replanejar escopo e prazo | Migrações e schema |
| Decisões de produto e ADRs | Testes e correção |
| Análise de material que você trouxer | Refatoração e revisão antes do merge |
| Documentos e painéis | Deploy |

Não é preciso escolher um dos dois. O repositório é a ponte: tudo que decidimos aqui vira arquivo em `docs/`, e o Claude Code lê de lá.

---

## 4. Primeiro dia, passo a passo

```bash
# 1. Criar o projeto
pnpm create next-app@latest . --typescript --tailwind --app --eslint --src-dir --import-alias "@/*"

# 2. Repositório
git init
git add -A
git commit -m "estrutura inicial do projeto"
gh repo create <nome> --private --source=. --push   # ou criar pelo site e apontar o remote

# 3. Copiar o kit para a raiz
#    CLAUDE.md, .gitignore, .env.example, README.md
#    e os 11 arquivos .md para docs/

# 4. Dependências da pilha
pnpm add @tanstack/react-query zustand zod
pnpm add @trpc/server @trpc/client @trpc/react-query @trpc/next
pnpm add react-hook-form @hookform/resolvers
pnpm add @supabase/supabase-js @supabase/ssr
pnpm add @dnd-kit/core @dnd-kit/sortable
pnpm add @tiptap/react @tiptap/starter-kit
pnpm add -D vitest @playwright/test

# 5. Supabase
supabase init
supabase link --project-ref <ref-do-projeto>

# 6. Vercel
#    Importar o repositório pelo painel da Vercel e configurar as variáveis de ambiente
```

> **Não rode esses comandos em sequência sem parar.** O passo 4 instala catorze pacotes de uma vez; se algo quebrar, você não vai saber qual foi. Instale em três levas e rode `pnpm dev` entre elas.

---

## 5. O que a semana 1 precisa entregar

Conforme o plano, ao fim da semana 1 deve existir:

- Repositório privado no GitHub, com trunk-based configurado
- Next.js com TypeScript **em modo estrito**, ESLint e Prettier bloqueando o commit
- Supabase conectado, com a primeira migração versionada no repositório
- Autenticação funcionando (e-mail e senha, mais link mágico)
- `tenant_id` e **RLS ativa** já na primeira tabela
- Deploy automático na Vercel a cada merge na main
- i18n configurada — **no primeiro commit**, não depois
- Schema desenhado com a separação do contexto pessoal prevista

**Entrega verificável:** uma página autenticada em produção, lendo um registro do banco através de política RLS.

Se ao fim da semana 1 isso não estiver de pé, não avance para a semana 2. Fundação mal feita não aparece agora — aparece na semana 9, quando já é caro.

---

## 6. Sobre o template da landing page e o design

**Sim, pode mandar.** Três formas, em ordem de utilidade:

### O que mandar

| Material | Como | O que eu extraio |
|---|---|---|
| **Pasta de código do template** | Coloque dentro da pasta do projeto que já está conectada a esta sessão | Tokens (cores, tipografia, espaçamento, raios, sombras), estrutura de layout, padrões de componente, e como ele resolve responsividade |
| **Imagens e capturas de tela** | Mesma pasta | Hierarquia visual, densidade, tom, e as decisões que só aparecem no resultado final |
| **Arquivo de design** (Figma, XD) | Exporte como PDF ou imagens, ou me passe o link se for público | O mesmo, com mais precisão nos espaçamentos |

Se a pasta for grande, avise: eu leio até 50 arquivos por vez e prefiro que você me diga quais pastas importam (normalmente `src/components`, `src/styles`, `tailwind.config`, e as telas principais).

### O que eu faço com isso

Conforme `C10` do Bloco 3, você escolheu: **extrair os tokens e os padrões de layout, e reescrever os componentes no nosso código.** Não é copiar o template — é destilar dele o sistema visual e aplicá-lo sobre shadcn/ui.

Na prática eu entrego:

1. **`tailwind.config.ts`** com a paleta, a escala tipográfica e o espaçamento do seu template
2. **`globals.css`** com as variáveis de tema em claro e escuro
3. **Os componentes base** do shadcn já ajustados ao seu visual — botão, campo, cartão, diálogo, tabela
4. **A landing page** adaptada, se ela for aproveitável
5. **Um `docs/design-system.md`** registrando o que foi extraído, para você e eu não divergirmos depois

### Uma ressalva sobre licença

Se o template for comprado ou tiver licença restritiva, me diga qual é antes. Extrair tokens e padrões funcionais é livre; copiar componentes inteiros de um template licenciado para um produto comercial pode não ser. Eu não tenho como verificar a licença sozinho — preciso que você me diga.

### Onde fazer essa adaptação

**Aqui**, se for a primeira leitura: eu analiso o material, extraio o sistema e entrego os arquivos de configuração prontos.

**No VS Code**, depois: com o repositório já criado, o Claude Code aplica componente por componente vendo o código real rodando, o que é muito mais eficiente do que eu gerar arquivos no escuro.

Minha sugestão é fazer a extração aqui na semana 1, quando ainda não existe código, e a aplicação lá a partir da semana 4, que é quando as telas começam a aparecer.

---

## 7. Duas pendências que travam o cronograma

1. **O nome do produto.** Trava domínio, e-mail de convite e identidade visual. A semana 10 já precisa dele, e domínio leva alguns dias para propagar. Decida até a semana 8 para não virar caminho crítico.
2. **As instruções deste projeto** ainda dizem "mensagens de commit em inglês", enquanto `A5` decidiu português. Eu não tenho acesso de escrita a elas — a mudança é sua.
