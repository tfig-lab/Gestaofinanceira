# Painel Financeiro de Projetos

Painel em uma única página (HTML + JavaScript, sem servidor) para acompanhar a parte financeira de engagements a partir da exportação de horas e despesas (abas **TIME** e **EXPENSE**).

## O que calcula

- **Receita** = charge-out rate × horas × **realização** (%, informada por projeto)
- **Saldo líquido** = valor final do projeto (líquido, ou bruto − impostos) − receita (− despesas, se marcado)
- **Disponível por mês** até a data limite, em R$ de receita, em R$ a tabela e em horas aproximadas
- Horas e receita por profissional (total e por mês), com os BOTs agrupados numa linha só
- Despesas por mês, por tipo e por profissional, com uma descrição de cada tipo

## Como usar

1. Abra a página (GitHub Pages ou `index.html` direto no navegador).
2. **Importar planilha**: escolha o .xls/.xlsx exportado. Cada engagement vira um card.
3. Em cada projeto, preencha a realização, o valor final (líquido ou bruto + % de imposto) e a data limite.
4. **Salvar dados** baixa um `.json` com os dados importados e os parâmetros. **Carregar dados** abre esse arquivo depois, em outro computador ou navegador.

Os parâmetros e a última planilha ficam guardados no navegador (localStorage). Se o navegador for limpo, recarregue pelo `.json`.

### Carregar automaticamente

Se existir um arquivo `dados.json` (o mesmo gerado por **Salvar dados**) na mesma pasta do `index.html` publicado, a página o carrega ao abrir. Se o navegador tiver algo salvo mais recente, prevalece o do navegador.

## Publicar no GitHub Pages

1. Suba o `index.html` (e este README) para o repositório.
2. Em **Settings → Pages**, escolha a branch `main` e a pasta `/ (root)`.
3. A página fica em `https://<usuario>.github.io/<repositorio>/`.

## Confidencialidade

A planilha é lida só no navegador e nada é enviado a servidores. Mas **não suba a planilha nem o `dados.json` para um repositório público**, porque eles têm nomes, taxas e valores de clientes. O `.gitignore` já ignora esses arquivos. Para usar o `dados.json` automático, prefira um repositório privado. Lembre que, dependendo do plano, o GitHub Pages pode publicar até repositórios privados de forma aberta.

## Dependências

- [SheetJS 0.18.5](https://cdnjs.com/libraries/xlsx), via cdnjs, para ler .xlsx/.xls binários. O formato XML 2003 exportado pelo sistema é lido sem biblioteca.
- Fontes Archivo, Public Sans e IBM Plex Mono (Google Fonts).
