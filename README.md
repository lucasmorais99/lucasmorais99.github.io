# DocuChat — Cloudflare AI Search + GitHub Pages

Página HTML estática para testar o widget de chat da Cloudflare AI Search no GitHub Pages. Não precisa de Node.js, build ou dependências locais.

## 1. Configure o endpoint

1. No painel da Cloudflare, abra **AI Search → sua instância → Settings → Public Endpoint**.
2. Ative **Enable Public Endpoint** e copie o ID/URL público.
3. Edite `index.html` e substitua `COLE_SEU_ID_AQUI` nesta linha:

   ```js
   const PUBLIC_ENDPOINT_ID = "COLE_SEU_ID_AQUI";
   ```

   Use apenas o ID do endpoint, não a URL inteira. Se a URL for `https://abc123.search.ai.cloudflare.com/`, o ID é `abc123`.

## 2. Publique no GitHub Pages

1. Crie um repositório no GitHub. Para um teste simples, ele pode ser público.
2. Envie `index.html` para a raiz do branch `main`.
3. No repositório, abra **Settings → Pages**.
4. Em **Build and deployment**, selecione **Deploy from a branch**.
5. Selecione o branch `main` e a pasta `/(root)`, e salve.
6. Aguarde a publicação e abra a URL que o GitHub Pages mostrar.

## 3. Autorize a origem na Cloudflare

Na instância de AI Search, abra **Settings → Public Endpoint → Authorized hosts** e adicione a origem do site publicado. Exemplos:

- Site de projeto: `https://SEU-USUARIO.github.io`
- Site de usuário: `https://SEU-USUARIO.github.io`
- Domínio personalizado: `https://www.seudominio.com`

Inclua apenas o esquema e domínio, sem o caminho `/nome-do-repositorio`. Salve e teste novamente.

## 4. Teste

O widget aparece como uma bolha no canto inferior direito. Se não aparecer:

- confira o ID em `PUBLIC_ENDPOINT_ID`;
- confirme que o Public Endpoint está habilitado;
- confira se a origem do GitHub Pages está em `Authorized hosts`;
- abra as ferramentas do desenvolvedor do navegador e veja erros de console/rede.

## Segurança e custos

- Um endpoint público e a página GitHub Pages podem ser acessados por qualquer pessoa. Não indexe documentos confidenciais para este teste.
- A lista de hosts autorizados é um controle de CORS para navegadores, não autenticação; não impede chamadas diretas por scripts externos.
- Confira cotas e cobrança atuais da Cloudflare antes de divulgar o site publicamente.

## Documentação

- Cloudflare AI Search UI snippets: https://developers.cloudflare.com/ai-search/configuration/retrieval/public-endpoint/embed-search-snippets/
- Configurar GitHub Pages por branch: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
