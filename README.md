# Lucas Rodriguez Advocacia

Site institucional profissional para Lucas Rodriguez Advocacia, desenvolvido em React, TypeScript e Tailwind CSS.

O projeto foi estruturado para ser rápido, responsivo, seguro para publicação estática e simples de manter. Ele não depende de backend, banco de dados ou serviços de terceiros para envio do formulário.

## Principais Recursos

- Página inicial institucional com hero em vídeo e fallback visual.
- Áreas de atuação: Imobiliário, Família, Penal e Consumidor.
- Página “Quem Somos” com apresentação profissional.
- Galeria do escritório com fotos, vídeos, controles manuais e suporte a redução de movimento.
- Formulário de contato sem backend: prepara um e-mail no cliente do usuário.
- Atalhos diretos para WhatsApp, telefone, e-mail e redes sociais.
- SEO técnico com sitemap, robots, canonical e schema `LegalService`.
- Headers de segurança para hospedagens estáticas compatíveis com `_headers`.
- Layout responsivo com foco em mobile, tablet e desktop.

## Stack

- Vite
- React
- TypeScript
- Tailwind CSS
- shadcn/ui
- Framer Motion
- Vitest
- ESLint

## Requisitos

- Node.js 20 ou superior
- npm 10 ou superior

## Instalação

```sh
npm install
```

Este projeto não exige variáveis de ambiente para rodar localmente.

## Desenvolvimento

```sh
npm run dev
```

Servidor local padrão:

```txt
http://localhost:8080
```

## Scripts

```sh
npm run dev        # servidor local
npm run build      # build de produção
npm run preview    # preview do build
npm run lint       # análise estática
npm run test       # testes com Vitest
```

## Contato Sem Backend

O formulário de contato funciona diretamente no frontend:

1. O usuário preenche os campos.
2. O site monta um e-mail com assunto e corpo preenchidos.
3. O cliente de e-mail do usuário é aberto via `mailto:`.
4. O WhatsApp permanece como alternativa imediata.

Essa abordagem elimina:

- banco de dados;
- funções serverless;
- chaves públicas de backend;
- secrets de envio de e-mail;
- dependências externas para captura de leads.

Os dados de contato ficam centralizados em:

```txt
src/config/site.ts
```

## Estrutura

```txt
public/
  _headers                 headers de segurança para hospedagem estática
  sitemap.xml              sitemap público
  robots.txt               regras de indexação
  .well-known/security.txt contato para relatos de segurança
  media/                   imagens, logo e vídeos do escritório
  videos/                  vídeo principal do hero

src/
  components/              seções autorais e componentes de interface
  components/ui/           componentes base shadcn/ui
  config/                  dados centrais do site
  hooks/                   hooks reutilizáveis
  lib/                     utilitários
  pages/                   páginas e rotas
  test/                    configuração e testes
```

## Segurança

O projeto inclui:

- `Content-Security-Policy`;
- `Permissions-Policy`;
- `Referrer-Policy`;
- `X-Content-Type-Options`;
- `X-Frame-Options`;
- `Cross-Origin-Opener-Policy`;
- `security.txt`.

Esses headers estão definidos em:

```txt
public/_headers
```

Em servidores próprios, configure headers equivalentes no Nginx, Apache ou serviço de hospedagem utilizado.

## SEO

Arquivos e recursos incluídos:

- `public/sitemap.xml`;
- `public/robots.txt`;
- canonical na página inicial;
- metadados Open Graph e Twitter;
- schema JSON-LD `LegalService`.

Se o domínio final mudar, atualize:

```txt
src/config/site.ts
public/sitemap.xml
public/robots.txt
public/.well-known/security.txt
```

## Build e Publicação

Gere o build:

```sh
npm run build
```

O resultado será criado em:

```txt
dist/
```

Publique esse diretório em uma hospedagem estática com suporte a SPA e fallback para `index.html`, como Netlify, Cloudflare Pages, GitHub Pages configurado para SPA ou servidor próprio.

## Checklist Antes de Publicar

```sh
npm run lint
npm run test
npm run build
npm audit --audit-level=moderate
```

## Créditos

Desenvolvido por Michel Brotherhood.
