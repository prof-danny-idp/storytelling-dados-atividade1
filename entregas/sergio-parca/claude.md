## Qual história meu dashboard conta?

Em 2024, 5.530 cidades elegeram prefeito, e nenhum partido ficou com mais de 16% delas. Mas o poder municipal não é tão pulverizado quanto parece: cinco partidos concentram 65% das prefeituras, cada um domina um tipo de cidade e uma região, e quase toda vitória (95%) veio de aliança. O leitor deve terminar entendendo que o mapa partidário é feito de território e de alianças, e não só de quantas prefeituras cada sigla ganhou.

## Contexto do projeto

- **Tema:** O mapa partidário de 2024.
- **Pergunta norteadora:** Como o poder municipal ficou distribuído entre partidos e alianças após as eleições de 2024?
- **Disciplina:** PCDIA – Storytelling de Dados (Mestrado em Administração Pública, IDP).
- **Base:** `dados/eleitos.csv` (prefeitos e vices eleitos em 2024, 11.106 linhas, 72 colunas, 5.553 municípios). Cuidados do dicionário aplicados:
  - Votos aparecem repetidos nas linhas de prefeito e vice: todas as contagens e somas usam só `cargo = Prefeito`, uma linha por município.
  - Base principal: `classificacao_validacao = ELEITO_ATUAL_TSE` (5.530 municípios). Ficam de fora 9 chapas cassadas e 14 eleições históricas documentadas.
  - Não há população na base: o porte da cidade é aproximado pelos votos válidos do município no turno decisivo.
  - Células vazias não viram zero. Reeleição, bens e perfil pessoal não foram usados, pelas ressalvas do dicionário.
  - Os dados refletem a extração de 01/10/2026 e descrevem 2024, não os atuais ocupantes dos cargos.

## Público-alvo

Leitores de um especial jornalístico: pessoas interessadas em política, mas sem familiaridade com dados eleitorais. Leem no celular ou no computador, em poucos minutos, e esperam entender sem conhecer termos como coligação, federação ou votos válidos. O painel precisa explicar o jargão, dar a conclusão em linguagem direta e ir além da contagem de vitórias.

## Perguntas que os dados respondem

1. Quanto poder cada partido tem, e ele é concentrado ou pulverizado?
2. Contar prefeituras basta? Quantos eleitores cada partido governa de fato?
3. Cada partido manda em um tipo de lugar (porte da cidade, região)?
4. As alianças são exceção ou regra? Quem encabeça as chapas vencedoras e quem só apoia?
5. Com quem cada partido costuma se aliar?
6. As vitórias foram apertadas ou folgadas?

## Decisões de design

- **Estrutura de reportagem:** título, pergunta como subtítulo, quatro números-âncora, cinco seções com manchete afirmativa e conclusão que responde à pergunta. O arco vai do panorama (quem tem quanto) para as camadas (peso, território, alianças) e termina na síntese.
- **Barras horizontais ordenadas** para o ranking de 24 partidos: é a forma mais legível para muitos rótulos de texto.
- **Barras divergentes** para a diferença entre peso em votos e peso em prefeituras: o sinal (acima ou abaixo) é a mensagem.
- **Barras empilhadas a 100%** para porte e região: mostram composição; só os cinco maiores partidos têm cor própria e os demais viram "Outros" cinza, para não passar de 6 categorias.
- **Barras com duas tonalidades** (encabeça x apoia): separa quem lidera de quem acompanha na mesma barra.
- **Mapa de calor em tabela HTML** para o cruzamento entre partidos aliados, com o valor escrito em cada célula.
- **Cores por entidade, fixas em todos os gráficos** (PSD azul, MDB laranja, PP verde-água, União amarelo, PL magenta). Elas não representam ideologia nem cores oficiais dos partidos.
- **Fora do painel:** mapa geográfico (sem malha de municípios no arquivo), ideologia dos partidos (seria inferência minha, não dado), reeleição, bens e perfil dos eleitos (fora da pergunta e com ressalvas no dicionário).
- **Acessibilidade:** `aria-label` nos gráficos, tabela de dados sob cada gráfico, modo escuro, e aviso se o Chart.js não carregar.
- Seguir a skill descrita em `skill.md`.

## Instruções para o Claude

- Gerar um único arquivo `dashboard.html`, autocontido, com os dados agregados embutidos.
- Seguir a skill descrita em `skill.md`.
- Usar Chart.js (cdnjs, versão fixa 4.4.1). Não ler o CSV no navegador.
- Ler `dados/dicionario.md` antes de qualquer cálculo e respeitar seus cuidados de leitura.
- Filtrar `cargo = Prefeito` antes de contar ou somar; contar municípios por `codigo_municipio_tse`.
- Importar a base como texto, com `;` e UTF-8 com BOM, e converter vírgula decimal só nas colunas numéricas.
- Todo número escrito no texto deve vir dos dados agregados, e não de memória.
- Linguagem simples, sem jargão sem definição, sem inferir ideologia dos partidos.
