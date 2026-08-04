# una-gqs-zensical-202602

Site de apoio da disciplina **Garantia e Qualidade de Software (GQS)** — UNA,
2026/2. Gerado com [Zensical](https://zensical.org) e publicado automaticamente
no GitHub Pages via GitHub Actions.

## Estrutura de pastas

```
.
├── docs/                  # Conteúdo do site (única pasta publicada)
│   ├── assets/            # Imagens, logo, favicon
│   ├── aulas/             # Uma página por aula (01-aula.md, 02-aula.md, ...)
│   ├── listas/            # Listas de exercícios correspondentes a cada aula
│   ├── javascripts/       # Scripts extras (ex.: configuração do MathJax)
│   ├── index.md           # Página inicial (cronograma da disciplina)
│   ├── setup.md           # Guia de configuração para o professor
│   └── ferramentas.md     # Guia de instalação de ferramentas para o aluno
├── mkdocs.yml             # Configuração do site (tema, navegação, plugins)
├── requirements.txt       # Dependências Python (Zensical)
└── .github/workflows/     # Pipeline de build e publicação (GitHub Actions)
```

Só o conteúdo dentro de `docs/` é publicado. Se no futuro for necessário
guardar rascunhos que não devem ir para o site, crie uma pasta fora de
`docs/` (ex.: `rascunhos/` na raiz do repositório) — ver o comentário em
[`mkdocs.yml`](mkdocs.yml) sobre o motivo.

## Como rodar localmente

1. Clone o repositório (substitua pela URL real do seu fork, se aplicável):

   ```bash
   git clone https://github.com/danhpaiva/una-gqs-zensical-202602.git
   cd una-gqs-zensical-202602
   ```

2. Crie e ative um ambiente virtual Python:

   ```bash
   python -m venv venv
   # Windows:
   .\venv\Scripts\activate
   # Linux/macOS:
   source venv/bin/activate
   ```

3. Instale as dependências:

   ```bash
   pip install -r requirements.txt
   ```

4. Inicie o servidor de visualização com recarregamento automático:

   ```bash
   zensical serve
   ```

   Acesse `http://127.0.0.1:8000` no navegador.

## Como publicar (GitHub Pages)

O deploy é feito pelo workflow [`.github/workflows/ci.yml`](.github/workflows/ci.yml)
via GitHub Actions. Para funcionar em um repositório próprio (fork ou cópia),
configure uma única vez:

1. **Settings → Pages → Build and deployment → Source**: selecione
   **"GitHub Actions"** (não deixe em "Deploy from a branch").
2. **Settings → Actions → General → Workflow permissions**: selecione
   **"Read and write permissions"** e salve.
3. Faça `git push` para a branch `main`: o site é construído e publicado
   automaticamente.

Se aparecer o erro `Deployment failed, try again later`, a causa quase
sempre é a fonte do Pages ainda estar em "Deploy from a branch" — corrija o
passo 1 e refaça o deploy em **Actions → (workflow) → Re-run jobs**.

### Fluxo de branches do CI

| Branch    | O que o workflow faz                                          |
| :-------- | :-------------------------------------------------------------- |
| `develop` | Só builda (`zensical build --strict`) — valida que o site compila sem erros, sem publicar. |
| `main`    | Builda e, se o build passar, publica no GitHub Pages.           |

## Como personalizar

Edite [`mkdocs.yml`](mkdocs.yml) (o nome do arquivo continua `mkdocs.yml` —
o Zensical lê essa configuração sem precisar de conversão):

* **Nome da disciplina:** campo `site_name`.
* **URL do site / repositório:** campos `site_url`, `repo_url` e `repo_name`
  — mantenha-os sincronizados com a URL real do repositório (`git remote -v`).
* **Menu lateral:** seção `nav:`.
* **Cores e tema:** seção `theme.palette` (ex.: `deep purple`, `red`, `blue`).
* **Extensões Markdown** (admonitions, abas, tabelas, mermaid, MathJax):
  seção `markdown_extensions:`.

## Licença

Distribuído sob a licença [MIT](LICENSE).
