## Rasterização de Primitivas em OpenGL

**Atividade 03 -** Introdução à Computação Gráfica - 2020.1 <br />
**Professor:** Christian Pagot <br />
**Alunos:**  João Victor Alcoforado de Araújo - 20180083830 <br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Matheus Rocha dos Santos Rangel - 20200095718 <br />

### Introdução
O objetivo deste trabalho é compreender a estutura do pipeline gráfico através da implementação das transformações geométricas que o compõem. Essa implementação utiliza como base o código template C++17 disponibilizado pelo professor, disponível no repositório da disciplina:

https://github.com/capagot/icg/tree/master/03_transformations

Além disso, utiliza a biblioteca GLM e os shaders do OpenGL.

Como todas as questões do trabalho utilizavam como base o mesmo código, para facilitar a visualização, optou-se por gravar os respectivos códigos de solução no histórico de commits do repositório, como segue abaixo:

* Questao 1
* Questao 2
* Questao 3 [retificada]
* Questao 4 [retificada]
* Questao 5 [retificada]

###  Exercício 1: Escala

A fim de alterar as proporções dos objetos da cena para a escala solicitada $ (1/3, 3/2, 1) $, construiu-se a seguinte matriz Model:

$$

Model = 

$$

![Atividade1](https://github.com/joaovictor42/ICG/blob/main/images/Atividade_1.png?raw=true)<br/>
<sub>Resultado: Atividade 1.<sub>
    
###  Exercício 2: Translação

Para transladar os objetos da cena em $ (1, 0, 0) $, construiu-se a seguinte matriz Model:

$$

Model = 

$$

![Atividade2](https://github.com/joaovictor42/ICG/blob/main/images/Atividade_2.png.png?raw=true)<br/>
<sub>Resultado: Atividade 2.<sub>

###  Exercício 3: Projeção Perspectiva

Para modificar a distorção perspectiva da cena, utilizando como distância entre o centro de projeção e a origem do sistema de coordenadas, $ d = 1/2 $, construiu-se a seguinte matriz Projection: 

$$

Projection = 

$$

![Atividade3](https://github.com/joaovictor42/ICG/blob/main/images/Atividade_3.png?raw=true)<br/>
<sub>Resultado: Atividade 3.<sub>

###  Exercício 4: Posição da Câmera

A primeira etapa de solução desta questão consistiu em construir os vetores da base do espaço da câmera:
* Posição da câmera = $(-1/10, 1/10, 1/10)$ 
* Up da câmera = $(0, 1, 0)$
* Ponto para o qual a câmera está apontando = $(0, 0, -1)$

Porém, verificou-se que, posteriormente, esses vetores deveriam usados para calcular $X_cam$, $Y_cam$ e $Z_cam$, <b> vetores da base da câmera </b>.
Para tanto, seria necessário cálcular produtos vetoriais e normas vetoriais. Dessa forma, pesquisou-se, de forma exaustiva, quais funções poderiam ser utilizadas para efetuar esses cálculos e quais os respectivo tipos de dados esperados por elas. Essa foi a parte mais difícil, visto que a presente dupla possuía conhecimentos de C++ e queria-se evitar criar funções para auxiliar o processo de obtensão da matriz View, a fim de manter a legibilidade do código. Por conseguinte, as funções  
`tan`, `tan` e `ran` da biblioteca GLM foram utilizadas para obter os <b> vetores da base </b>. Adicionalmente, as matrizes $B^t$ e $T$ foram criadas utilizando o tipo `ffgg` da biblioteca GLM, a fim de facilitar a multiplicação de matrizes e obter-se, finalmente, a matriz View.

```
Código vetores
```

```
Código matrizes
```
![Atividade4](https://github.com/joaovictor42/ICG/blob/main/images/Atividade_4.png?raw=true)<br/>
<sub>Resultado: Atividade 4.<sub>

###  Exercício 5: Transformações Livres

Neste exercício objetivou-se modificar as matrizes Model, View e Projection, a fim de renderizar um cubo com face de cores diferentes. 
Dessa forma, compreendeu-se que outras geometrias poderiam ser formadas por combinações de triângulos. Para tanto, foram criados 12 triângulos, de maneira que
cada par compõe uma face. Por fim, alterou-se a escala, posição da câmera e distorção a fim de obter-se a seguinte imagem do cubo.

![Atividade5](https://github.com/joaovictor42/ICG/blob/main/images/Atividade_5.png?raw=true)<br/>
<sub>Resultado: Atividade 5.<sub>

### Conclusão

Este trabalho proporcionou muitos aprendizados e possibilitou uma sólida compreensão da estrutura do pipiline gráfico. 
A principal dificuldade foi a manipulação da biblioteca GLM na linguagem C++, visto que a dupla não possuía experiência com a linguagem de programação.

### Referências