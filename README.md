# Painel Financeiro de Projetos

Painel em uma única página (HTML + JavaScript, sem servidor) para acompanhar a parte financeira de engagements a partir da exportação de horas e despesas (abas **TIME** e **EXPENSE**).

## O que calcula

- **Receita** = charge-out rate × horas × **realização** (%, informada por projeto)
- **Saldo líquido** = valor líquido do projeto − receita (− despesas, se marcado)
- **Disponível por mês** até a data limite, em R$ de receita, em R$ a tabela e em horas aproximadas
- Horas e receita por profissional (total e por mês), com os BOTs agrupados numa linha só
- Despesas por mês, por tipo e por profissional, com uma descrição de cada tipo
- **Planejamento de horas**: horas por profissional e mês até a data limite para terminar com a reserva definida (padrão 5%). Usa a capacidade de cada pessoa (dias úteis sem feriados nacionais × horas/dia × % máximo × dedicação ao projeto), enche primeiro os mais juniores e distribui o restante entre gerentes e sócios. Regras fixas por pessoa ficam em `DEFAULT_PEOPLE` no `index.html`.

## Como usar

1. Abra a página (GitHub Pages ou `index.html` direto no navegador).
2. **Importar planilha**: escolha o .xls/.xlsx exportado. Cada engagement vira um card.
3. Os parâmetros dos projetos já cadastrados (realização, valor líquido e data limite) ficam fixos no código, em `DEFAULTS` no `index.html`. Todos os valores do painel são líquidos de impostos.
4. Para um projeto novo, preencha os parâmetros no painel à esquerda. Eles ficam salvos neste navegador.

## Publicar no GitHub Pages

1. Suba o `index.html` (e este README) para o repositório.
2. Em **Settings → Pages**, escolha a branch `main` e a pasta `/ (root)`.
3. A página fica em `https://<usuario>.github.io/<repositorio>/`.

## Confidencialidade

A planilha é lida só no navegador e nada é enviado a servidores. **Não suba a planilha para o repositório**, porque ela tem nomes, taxas e valores de clientes. O `.gitignore` já ignora esses arquivos.

## Dependências

- [SheetJS 0.18.5](https://cdnjs.com/libraries/xlsx), via cdnjs, para ler .xlsx/.xls binários. O formato XML 2003 exportado pelo sistema é lido sem biblioteca.
- Fontes Archivo, Public Sans e IBM Plex Mono (Google Fonts).
