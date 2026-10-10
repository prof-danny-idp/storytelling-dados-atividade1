# Diário de prompts

**Link compartilhado da conversa (opcional):** não compartilhado.

---

## Prompt 1

```
Tenho que entregar um trabalho numa disciplina de story telling. As orientacoes estão no git da disciplina em https://github.com/prof-danny-idp/storytelling-dados-atividade1 no arquivo readme.md. Analise as orientações e planeje como responder ao exercicio. Não execute nada ainda.
```

**O que funcionou / o que mudei:** Pedir um plano antes de executar funcionou: o Claude leu o README, o dicionário de dados e o modelo de entrega, e trouxe o que era exigido (4 arquivos, critérios de avaliação, regras do PR). Também apontou que o prazo do README (03/10/2026) já tinha passado e que faltava o tema que o professor atribuiu a mim. Como o prompt não trazia o tema, o plano ficou genérico e precisou de uma rodada de perguntas.

---

## Prompt 2

```
Tema: O mapa partidário de 2024
Pergunta: Como o poder municipal ficou distribuído entre partidos e alianças após as eleições de 2024?
Para quem: leitores de um especial jornalístico. Interessados em política, mas sem familiaridade com dados eleitorais. A história deve ir além da contagem de vitórias.
(Prazo: prorrogado/ok. Entrega: não entregar agora, solicitarei mais à frente.)
```

**O que funcionou / o que mudei:** Informar tema, pergunta e público (copiados do enunciado do professor) deu ao plano o ângulo certo: em vez de só ranquear partidos, passou a incluir peso em votos, território (porte e região) e alianças. Deixei explícito que não era para entregar ainda, para o Claude apenas preparar os arquivos localmente.

---

## Prompt 3

```
pasta sergio-parca, use chart.js
```

**O que funcionou / o que mudei:** Duas decisões curtas fecharam as dúvidas do plano (nome da pasta e biblioteca de gráficos) e liberaram a execução. A partir daí o Claude:
- clonou o repositório, leu `entregas/_modelo` e o verificador de PR (`validar-entrega.yml`) para conhecer as regras;
- explorou a base com pandas, filtrando só `cargo = Prefeito` e `ELEITO_ATUAL_TSE`, como pede o dicionário;
- escolheu os achados (concentração, peso em votos, porte e região, alianças, folga das vitórias) e gerou os números agregados por script, que alimentam tanto os gráficos quanto o texto;
- montou o `dashboard.html` com Chart.js, conferiu no navegador (desktop e tela estreita) e corrigiu um rótulo que sobrepunha o eixo no gráfico de diferenças;
- escreveu `skill.md` (genérica, sem citar o tema) e `claude.md`.

Se eu tivesse que repetir: pediria já no primeiro prompt o tema e o público, para evitar a rodada de perguntas, e pediria os rótulos dos gráficos revisados em tela de celular desde o início.
