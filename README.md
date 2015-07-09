# Melhores práticas com ABL Progress 4GL

*Guia de referencia para desenvolvimento utilizando melhores práticas com a linguagem OpenEdge ABL Progress*

## <a name='table-of-contents'>Índice</a>

  1. [Variáveis](#variaveis)
  2. [Tabelas temporárias](#temp-table)

  ## <a name='variaveis'>Variáveis</a>

 Uma boa prática para nomear uma variável é utilizar o primeiro caractere como indicador do tipo de dado, conforme a
  <a href="https://pt.wikipedia.org/wiki/Nota%C3%A7%C3%A3o_h%C3%BAngara" target="blank">notação Hungara</a>, dessa forma, evita
  a necessidade de retornar ao topo do documento para consulta de tipo.

 Outra prática a ser observada na definição de variáveis  é o uso do ``no-undo``, quando não incluso na definição da variável
  o Progress ira guardar o valor anterior da variável para uma possível operação de ``undo`` o que dispensa mais uso de memória, salvo
  quando houver a necessidade do uso desta função, utilize o  ``no-undo``.

  ```ABL
//Ruim
  def var num-status as int.

//Bom
  def var inum-status as int  no-undo.
  ```
  
  
  ## <a name='temp-table'>Tabelas temporárias</a>

  Na criação de tabelas temporárias, usamos sempre o prefixo de `tt`, já o restante deve ser definido com os mesmos critérios da
  criação de um tabela convencional, inclusive, com o uso de índices que interferem diretamente na performance do programa.

  ```ABL
//Ruim
def temp-table teste
   field id as int
    field nome as char.

//Bom
def temp-table tt-teste no-undo
  field id as int
  field nome as char
  index tte01 is primary unique id.

  ```
