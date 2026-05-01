# 🎼 Orquestra App — Deploy na Vercel

## Pré-requisitos
- Conta na [Vercel](https://vercel.com)
- App funcionando no Google Apps Script com deploy ativo

## Deploy

### 1. Configurar a URL do Apps Script
Edite `public/redirect.html` e substitua:
```
var APPS_SCRIPT_URL = 'https://script.google.com/macros/s/AKfycbzFyOsgU3YlYYXnzKrful2W1zmTTRy3nJedPOF8H8YTkHVGhNcMJkNidA6V0ICVR6LH/exec';
```
pela URL real do seu deploy do Apps Script.

### 2. Deploy na Vercel

**Via CLI:**
```bash
npm i -g vercel
cd vercel
vercel
```

**Via GitHub:**
1. Suba esta pasta para um repositório GitHub
2. Acesse [vercel.com/new](https://vercel.com/new)
3. Importe o repositório
4. Output Directory: `public`
5. Deploy

### 3. Domínio customizado (opcional)
Na dashboard da Vercel:
- Settings → Domains → Adicione seu domínio (ex: `orquestra.seusite.com`)
- Configure o DNS conforme instruções da Vercel
- HTTPS é automático

## Estrutura
```
vercel/
├── public/
│   ├── index.html        ← Landing page
│   ├── redirect.html     ← Redirect para Apps Script
│   └── privacidade.html  ← Política de Privacidade (LGPD)
├── vercel.json           ← Config de headers e rewrites
├── package.json
└── README.md
```

## Rotas
- `/` → Landing page
- `/app` → Redirect para o Apps Script
- `/privacidade` → Política de Privacidade

## Segurança (headers)
- `X-Frame-Options: DENY` — impede iframe
- `X-Content-Type-Options: nosniff` — impede MIME sniffing
- `Strict-Transport-Security` — força HTTPS
- `Content-Security-Policy` — restringe origens
- `Referrer-Policy` — limita dados do referrer
- `Permissions-Policy` — desativa câmera/microfone/geolocalização
