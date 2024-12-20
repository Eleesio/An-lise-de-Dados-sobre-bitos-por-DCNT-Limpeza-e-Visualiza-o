# Análise de Dados sobre Óbitos por DCNT: Limpeza, Correção e Visualização

## Introdução

O presente projeto visa realizar uma análise exploratória de um conjunto de dados relacionado a óbitos causados por Doenças Crônicas Não Transmissíveis (DCNT). A partir deste dataset, buscamos entender como características demográficas, como sexo, raça/cor, escolaridade e categorias CID (Classificação Internacional de Doenças), influenciam a distribuição de óbitos. A principal finalidade deste trabalho foi limpar, corrigir e visualizar os dados de forma que pudéssemos identificar padrões e obter insights que poderiam ser úteis para decisões em políticas de saúde pública.

As etapas do projeto envolveram a limpeza e pré-processamento dos dados, a realização de cálculos corretivos nas colunas de idade e data de nascimento/óbito, e a geração de visualizações gráficas para entender as distribuições e as relações entre as variáveis. Através de gráficos informativos, pretendemos oferecer uma visão mais clara e acessível sobre os óbitos causados por DCNT, permitindo, assim, que outros pesquisadores ou formuladores de políticas possam aproveitar os resultados desta análise.

## Desenvolvimento

### 1. **Carregamento e Leitura dos Dados**
Inicialmente, carregamos o conjunto de dados utilizando a biblioteca `pandas`, que é uma ferramenta poderosa para análise de dados em Python. O arquivo foi lido com a função `read_csv()`, especificando que o separador dos valores é `;` (padrão em muitos arquivos CSV de origem brasileira). Também configuramos a codificação como `utf-8` para garantir a leitura correta de caracteres especiais, como acentos e cedilhas.

Além disso, para garantir que o código funcione corretamente, adicionamos a opção `on_bad_lines='skip'` para ignorar qualquer linha malformada no arquivo.

### 2. **Pré-processamento das Colunas de Data**

A partir dos dados carregados, o próximo passo foi corrigir as colunas relacionadas à data, especificamente as de nascimento (`dt_nascimento`) e óbito (`dt_obito`). Utilizamos o `pd.to_datetime()` para transformar essas colunas em objetos datetime, facilitando cálculos posteriores. Caso houvesse datas inválidas ou mal formatadas, configuramos a opção `errors='coerce'` para substituir essas entradas por valores nulos (`NaT`).

A opção `dayfirst=True` foi essencial para garantir que as datas com o formato dia/mês/ano fossem corretamente interpretadas.

### 3. **Cálculo e Correção da Idade**

A coluna `nu_idade` foi analisada e corrigida. Inicialmente, verificamos a consistência da coluna, convertendo valores para numéricos, e corrigimos valores nulos e inconsistentes, como idades negativas. Caso a idade não estivesse presente, utilizamos a diferença entre as datas de nascimento e óbito para calcular a idade, considerando a diferença em anos.

Após esse processo, realizamos a substituição de idades inválidas por `None`, garantindo que os dados estivessem mais consistentes para as etapas seguintes.

### 4. **Substituição de Valores Nulos em Variáveis Categóricas**

Diversas colunas categóricas, como sexo (`sg_sexo`), raça/cor (`tp_raca_cor`), escolaridade (`tp_escolaridade`) e categoria CID (`categoria_cid_causa_basica`), apresentaram valores ausentes. Esses valores foram substituídos por uma categoria genérica "Desconhecido", a fim de evitar falhas nas análises subsequentes.

### 5. **Visualizações**

Para entender melhor os dados, criamos uma série de visualizações gráficas usando a biblioteca `seaborn`, que fornece uma maneira intuitiva de explorar visualmente as relações entre diferentes variáveis.

#### **Distribuição das Idades dos Óbitos**

O primeiro gráfico criado foi um histograma com uma estimativa de densidade (KDE), mostrando a distribuição das idades dos óbitos. Este gráfico nos permite observar a faixa etária mais afetada pelas DCNT.

#### **Boxplot por Sexo**

Em seguida, criamos um boxplot para comparar a distribuição das idades entre os diferentes sexos. Essa visualização ajuda a identificar se há diferenças significativas nas idades dos óbitos entre homens e mulheres.

#### **Contagem de Óbitos por Raça/Cor e Escolaridade**

Usamos gráficos de barras (`countplot`) para mostrar a distribuição dos óbitos por raça/cor e escolaridade, respectivamente. Esses gráficos fornecem uma visão clara de como esses fatores demográficos estão relacionados aos óbitos por DCNT.

#### **Contagem de Óbitos por Categoria CID**

A contagem de óbitos por categoria CID foi mostrada em outro gráfico de barras, com um agrupamento de categorias menores em "Outros" para evitar um gráfico excessivamente carregado.

#### **Idade por Sexo e Raça/Cor**

Por fim, fizemos uma análise cruzada entre as variáveis de sexo e raça/cor para examinar como a idade dos óbitos variava entre esses grupos, usando um boxplot horizontal.
 
## Conclusão

Através deste trabalho, conseguimos realizar uma análise profunda e detalhada sobre os óbitos causados por Doenças Crônicas Não Transmissíveis (DCNT). As etapas de pré-processamento dos dados, correção de idades e preenchimento de valores ausentes garantiram que as análises fossem realizadas de forma precisa e consistente. As visualizações gráficas nos permitiram explorar as distribuições das variáveis e suas inter-relações, revelando padrões importantes sobre os óbitos por DCNT. Esses resultados podem servir como base para futuras pesquisas ou como insumos valiosos para a formulação de políticas públicas voltadas à prevenção e tratamento dessas doenças.
