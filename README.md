# Trabalho Prático sobre Testes de Software

### ESLint
https://github.com/eslint/eslint

Com mais de 19,5 mil estrelas e cerca de 17,4 mil downloads semanais no npm, ESLint é a maior ferramenta para identificar e reportar problemas com códigos ECMAScript/JavaScript. 
A escolha do ESLint se deu por ser uma das maiores ferramentas de código aberto e também por, provavelmente, ter sido implementada em quase todos os trabalhos práticos da disciplina. 

#### Testes
https://github.com/eslint/eslint/blob/main/tests/lib/linter/linter.js
Os testes que serão apresentados fazem parte do módulo _ _linter_ _.

Esse módulo utiliza algumas bibliotecas para auxiliar nos testes, essas são:
```
assert = require("chai").assert,
sinon = require("sinon"),
espree = require("espree"),
esprima = require("esprima")
```
Além disso a entidade que vai ser testada: 
```
const { Linter } = require("../../../lib/linter");
```


###### Teste 1

No trecho abaixo, há um exemplo de teste do método _getSourceLines_
![image](https://user-images.githubusercontent.com/32281559/146291760-645acbfa-5419-43ad-a5fb-9434405db6a7.png)
O objetivo desse teste é verificar se ao buscar um código fonte, o programa está conseguindo separar linhas quebradas com _ _/n_ _ . Para isso, é criada uma string _ _code_ _  contendo _ _\n_ _ e criada uma regra, atráves do método _spy_ da biblioteca _sinon_, onde é esperado que o método _getSourceLines_ retorna duas strings, ao envés de uma. Logo após essa regra é definida e verificada.


###### Teste 2
Abaixo, há um teste que verifica se uma variável declarada está sendo usada:
![image](https://user-images.githubusercontent.com/32281559/146292973-71ee86e6-3089-4271-9109-c7fa04b4980d.png)
No teste, é criada uma string que simula a declaração de duas variaves, no trecho: 

```
 const code = "var a = 1, b = 2;";
 ```
 Então, é criada uma regra que marca a variável _a_ como usada, através do método _markVariableAsUsed_ e verifica se o a variável _a_ é verdadeira para a propriedade _eslintUsed_ , que deve ser verdadeira se a variável é usada, e se a variável _b_ é falsa para mesma propriedade
 
 ###### Teste 3
A seguir é testada uma funcionalidade substitui um código com bases na verificação regras configuradas do ESLint:
![image](https://user-images.githubusercontent.com/32281559/146295002-37701669-89c0-4e7b-b81e-0dbe9720ccb2.png)
O método testado é o _verifyAndFix_ , nele é passado como primeiro parâmetro uma string que simula a declaração de uma variável sem ponto final no fim da linha, o segundo parâmetro é justamente a regra que padroniza pontos vírgulas ao final das linhas. Com isso, o teste se o retorno do método será a string passada com o acréscimo de um ponto vírgula no final.


#### Conclusão
Com a verificação do módulo de testes, é possível entender porque a ferramenta é tão bem sucedida. Apenas o módulo que testa os métodos do _Linter_ tem 13660 linhas, sendo um exemplo da importância dos testes para os sistemas.
 
 

