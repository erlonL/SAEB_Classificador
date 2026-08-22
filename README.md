# SAEB Classificador

Estudo acadêmico de aprendizagem de máquina sobre desempenho estudantil no SAEB da Paraíba, desenvolvido por Erlon Lacerda e Maria Bandeira na UFPB.

**Site do projeto:** [erlonl.github.io/saeb](https://erlonl.github.io/saeb/)

O site Quarto apresenta a motivação, o contexto e os notebooks canônicos como um estudo de caso navegável. Para visualizar localmente, instale o Quarto 1.10.18 e execute `quarto preview`; para gerar `_site/`, execute `quarto render`. As células não são reexecutadas durante a publicação.

Consulte [Repositório e reprodutibilidade](reproducibilidade.qmd) para a ordem completa da análise, dependências observadas e limitações do snapshot atual.

# Introdução

O nosso objetivo para escolher o dataset era avaliar as notas e desempenho dos alunos com base em variáveis sociais / de estudo, sem considerar questões socioeconômicas. Sobre aplicações sociais, pensamos em como seria importante acompanhar o aluno durante o tempo anterior à prova, fazendo questionários antes, ir trabalhando nos pontos fracos do aluno e melhorar o desempenho geral do ensino nas escolas municipais com base nas respostas dadas pelo aluno. Esse estudo promove a ideia de que o desempenho do aluno poderia ser "previsto", mesmo se o questionário fosse respondido meses antes da prova em si, o que trás um alarme para como a qualidade de ensino deve ser melhorada, mas o aluno também pode ter melhores resultados, caso tenha um acompanhamento considerando essas variáveis.

# Descrição do Dataset

O Sistema de Avaliação da Educação Básica (Saeb) é um conjunto de avaliações externas em larga escala que permite ao Inep realizar um diagnóstico da educação básica brasileira e de fatores que podem interferir no desempenho do estudante. Desde 1995, a avaliação bienal busca fornecer um panorama da Educação Básica e sofreu algumas mudanças metodológicas para aprimoramento. Juntamente com outros indicadores, as notas do SAEB estruturam a nota do Índice de Desenvolvimento da Educação Básica (Ideb). Por meio de testes e questionários, aplicados a cada dois anos na rede pública e em uma amostra da rede privada, o Saeb reflete os níveis de aprendizagem demonstrados pelos estudantes avaliados, explicando esses resultados a partir de uma série de informações contextuais. Avalia as séries: 5º ano, 9º ano e 3º ano do EM. Em 2019, tem o 2º ano do E.F.

# Tratamento / Análise de Dados

Após a escolha do Dataset, disponível em [Base dos Dados - SAEB](https://basedosdados.org/dataset/e083c9a2-1cee-4342-bedc-535cbad6f3cd?table=d429a79a-eca1-461c-9c1f-ce65d61048a1), precisamos fazer o tratamento dos dados, tratamento das colunas, análise das correlações / feature engineering e análise dos dados, tudo para que tivéssemos os dados da melhor forma possível. Os notebooks estão separados em ordem, visando a [Reproducible Research](https://book.the-turing-way.org/reproducible-research/reproducible-research). Considerados como códigos-fonte a parte do projeto principal, eles estão separados na pasta `treatment_analysis/` da forma:

1. initial-treatment.ipynb: Contém o tratamento inicial, a lógica para juntar os dados de 2007 até 2017 (considerando que as provas são realizadas a cada 2 anos) e tratamentos básicos como preencher idades faltantes e remover questionários nao preenchidos;
2. columns-treatment.ipynb: Contém a transformação das colunas do dataset (com base no dicionário das perguntas) pra valores discretos, de forma ordinal. Também são retiradas colunas não consideradas para o estudo e remoção de outliers com base na proficiencia / erro_padrao;
3. correlation_featureengineering.ipynb: Contém a análise das correlações entre as variáveis / features a partir de heatmaps e remoção de colunas com baixa ou nenhuma correlação com o desempenho do aluno. O dataset utilizado para treinar os modelos também é salvo desse notebook;
4. data-analysis.ipynb: Contém a análise dos dados, com foco na distribuição das classes com base na proficiência e erro padrão do aluno e a aplicação de PCA para relacionar as variáveis entre si.
5. data-interpos.ipynb: Contém a análise e a remoção de interposição (ruído) nos dados, através de força bruta analisando todas as possibilidades, balanceando os grupos. Também é feita a remoção da classe 'Proficiente', e ao mesmo tempo a junção das classes 'Insuficiente' e 'Básico'.

# Resultados

Veja a [visão geral do estudo de caso](estudo-de-caso.qmd) ou abra diretamente o [relatório final renderizado](AM_Projeto_Erlon_Lacerda_Maria_Bandeira-v2.ipynb).

O site é publicado automaticamente pelo workflow `.github/workflows/publish.yml`. No GitHub, selecione **Settings → Pages → Source: GitHub Actions** uma única vez para ativar a URL.
