---
name: dashboard-narrativo-html
description: Regras narrativas e visuais para criar dashboards em HTML único com Chart.js que contam uma história com dados. Use sempre que for criar gráfico, painel ou relatório visual para um público não especialista.
---

# Dashboard narrativo em HTML

## Quando usar

Ao transformar uma base de dados em um painel que precisa **explicar algo a um leitor**, não só exibir números. Vale para qualquer tema e qualquer base. Entrega: um único `.html` autocontido, com dados já agregados e embutidos.

## Estrutura narrativa

- Comece pela **pergunta** que o painel responde, em uma frase, como subtítulo do título.
- Abra com 3 a 4 números-âncora (cartões) que dão a escala do assunto.
- Organize em seções numeradas, cada uma com: **manchete que afirma algo** (não "Gráfico de X"), 2 a 4 linhas de texto com o número que importa em destaque, e o gráfico que prova a afirmação.
- Ordem: panorama, depois camadas de explicação (peso, território, relações), depois um ponto de tensão ou nuance, e por fim uma **conclusão que responde à pergunta** em 2 a 3 pontos.
- Cada seção deve levar à próxima: a limitação de uma contagem simples abre a seção que a corrige.
- Termine com notas de método: filtros aplicados, aproximações usadas, limites dos dados e glossário de termos técnicos.
- Escreva para quem não conhece o jargão: defina cada termo técnico na primeira vez ou no glossário.

## Escolha de gráficos

- **Comparar categorias:** barras horizontais ordenadas do maior para o menor, com rótulo de valor na ponta. Nunca pizza com mais de 3 fatias.
- **Composição de um total:** barras empilhadas a 100%, com no máximo 5 a 6 segmentos mais "Outros".
- **Diferença ou polaridade:** barras divergentes a partir do zero, duas cores com sentido oposto.
- **Distribuição:** histograma com faixas de largura igual e eixo começando em zero.
- **Cruzamento de duas categorias:** tabela de calor em HTML com uma única cor em intensidade crescente e o valor escrito na célula.
- **Parte dentro do todo, por item:** barra empilhada com duas tonalidades da mesma cor (destaque e versão clara).
- Barras sempre partem de zero. Nunca use eixo duplo, 3D, nem trunque o eixo para exagerar diferenças.
- Se o dado principal é um único número, use um cartão de destaque, não um gráfico.

## Paleta de cores

Defina as cores como variáveis CSS em `:root` e redefina-as para o modo escuro (`prefers-color-scheme: dark`), lendo-as no JavaScript ao montar os gráficos.

- Categorias (ordem fixa, cada entidade mantém sua cor em todos os gráficos): azul `#2a78d6`, laranja `#eb6834`, verde-água `#1baf7a`, amarelo `#eda100`, magenta `#e87ba4`.
- Neutro para "Outros" e itens secundários: cinza `#a9a8a1`.
- Magnitude: um só matiz (azul) do claro ao escuro.
- Divergência: azul `#2a78d6` e vermelho `#e34948`, com cinza no ponto neutro.
- Use cor de destaque só no que a história enfatiza; o resto fica neutro.
- Texto sobre cores: escolha preto ou branco pelo contraste. Texto de rótulo nunca usa a cor da série.
- Fundo `#f6f5f2`, superfície `#fcfcfb`, texto `#0b0b0b`, texto secundário `#52514e`.
- Nunca dependa só de cor: sempre legenda, rótulo direto ou tabela.

## Tipografia e layout

- Fonte do sistema para texto e serifada (Georgia) para títulos. Título principal com `clamp()` para escalar.
- Coluna de leitura de até ~740px para texto; gráficos em cartões de até ~980px.
- Cada gráfico tem título, subtítulo que explica como ler, legenda e uma versão em tabela (`<details>`).
- Barras finas com cantos arredondados de 4px, grade discreta, sem bordas pesadas, e 2px de separação entre segmentos empilhados.
- Responsivo: contêiner com altura definida, `maintainAspectRatio:false`, grades em `auto-fit`, nada de rolagem horizontal da página (tabelas largas em contêiner com `overflow-x:auto`).
- Gráficos com muitas categorias precisam de altura proporcional (cerca de 24px por barra).
- Dê `aria-label` a cada `<canvas>` descrevendo o que mostra.

## Checklist final

- [ ] Um único arquivo `.html`, com dados embutidos e agregados, sem ler arquivos locais.
- [ ] Biblioteca por CDN com versão fixa; mensagem de aviso se ela não carregar, e tabelas continuam visíveis.
- [ ] Título-pergunta, números-âncora, seções com manchete afirmativa e conclusão que responde à pergunta.
- [ ] Todos os números do texto conferem com os dados agregados (gerar o texto a partir deles, quando possível).
- [ ] Nenhum eixo truncado, nenhum eixo duplo, barras partindo do zero.
- [ ] A mesma entidade tem a mesma cor em todos os gráficos; legenda presente quando há mais de uma série.
- [ ] Modo escuro testado; contraste dos textos adequado.
- [ ] Abre direto no navegador, sem erros no console, legível em tela de 390px e de 1280px.
- [ ] Notas de método, limites dos dados e glossário no rodapé.
