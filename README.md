# Dashboard Produtividade & Utilização — publicação no GitHub Pages

Arquivo a publicar: **`index.html`** (autocontido, não precisa de mais nada).

---

## Antes de publicar — 2 pré-requisitos

**1. A planilha precisa estar pública para leitura.**
Na planilha → *Compartilhar* → Acesso geral → **Qualquer pessoa com o link** → papel **Leitor**.
Sem isso o dashboard abre, mas mostra o aviso de falha ao carregar.

**2. A aba precisa continuar se chamando `import`.**
Se renomear a aba, ajuste a linha no `index.html`:

```js
const SHEET_TAB = 'import';
```

---

## Passo a passo — GitHub Pages

1. Crie uma conta em [github.com](https://github.com) (se ainda não tiver).
2. **New repository** → nome ex.: `dash-produtividade` → visibilidade **Public** → *Create repository*.
   *(o repositório precisa ser Public para o Pages funcionar no plano gratuito)*
3. Na tela do repositório: **Add file → Upload files** → arraste o `index.html` → *Commit changes*.
4. Menu **Settings** (do repositório) → **Pages** (barra lateral esquerda).
5. Em *Build and deployment* → **Source: Deploy from a branch** → Branch: **main** / pasta **/ (root)** → *Save*.
6. Aguarde 1–2 minutos e recarregue a página. O link aparece no topo:

```
https://SEU-USUARIO.github.io/dash-produtividade/
```

Pronto — esse é o link para compartilhar.

### Para atualizar o dashboard depois

Repositório → clique no `index.html` → ícone de lápis (**Edit**) ou **Upload files** com o arquivo novo → *Commit*. O site atualiza sozinho em ~1 minuto.

---

## Como os dados se atualizam

Os dados **não ficam salvos** no arquivo. A cada abertura o dashboard lê a aba `import` direto do Google Sheets.

- Recarregar a página = dados frescos
- Botão **↻ Atualizar** = releitura imediata
- Seletor **Auto** no cabeçalho = releitura automática (padrão: 10 min)

Ou seja: atualizou a planilha, o dashboard reflete. Não precisa republicar nada.

---

## Atenção — privacidade

A versão publicada **não tem senha**. Quem tiver o link vê nomes completos, gestor, área e desempenho individual de todos os colaboradores.

Mitigações já aplicadas no arquivo:

- `<meta name="robots" content="noindex, nofollow, noarchive">` — pede a buscadores que não indexem a página (não impede acesso direto, apenas evita que apareça no Google)
- URL longa e não divulgada funciona como "link não listado"

Se em algum momento quiser restringir o acesso, dá para:

- Adicionar uma tela de senha simples na página (barreira leve, não é criptografia)
- Publicar no SharePoint / intranet, onde o login corporativo já protege
- Trocar nomes completos por nome + iniciais

Me avise qual desses e eu gero a versão.

---

## Alternativas de hospedagem

| Opção | Tempo | Observações |
|---|---|---|
| **GitHub Pages** | ~5 min | Gratuito, HTTPS, link estável, fácil de atualizar |
| **Netlify Drop** (app.netlify.com/drop) | ~1 min | Arrasta o arquivo e já está no ar, sem conta. Link aleatório |
| **SharePoint / intranet** | varia | Protegido pelo login corporativo. Confirme antes se o ambiente permite scripts e acesso a CDN externo |

---

## Requisitos técnicos da página

- Navegador moderno com internet (Chrome, Edge, Firefox)
- Acesso liberado a `docs.google.com` (leitura da planilha) e `cdn.jsdelivr.net` (biblioteca de gráficos)

Se a rede corporativa bloquear o jsdelivr, os gráficos do painel individual não aparecem — o restante do dashboard continua funcionando. Nesse caso peça que eu embuta a biblioteca no próprio arquivo.
