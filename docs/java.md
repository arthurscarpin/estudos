<div style="
  width: 95%;
  padding: 24px;
  background: linear-gradient(to right, #f0f0f0, #d0d0d0);
  border: 2px solid #333;
  border-radius: 8px;
  font-family: 'Segoe UI', sans-serif;
  font-size: 24px;
  font-weight: bold;
  color: #222;
  text-align: center;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
">
  Fundamentos do Java
</div>


<br>
<br>

**Sumário**

<!-- TOC -->
- [1 Variáveis](#1-variáveis)
  - [1.1 Variáveis de tipo primitivo](#11-variáveis-de-tipo-primitivo)
  - [1.2 Variáveis de tipo referencial](#12-variáveis-de-tipo-referencial)
- [2. Conversão de dados](#2-conversão-de-dados)
- [3. Escopo de variáveis](#3-escopo-de-variáveis)
- [4. Operadores](#4-operadores)
- [5. Estrutura condicional](#5-estrutura-condicional)
- [6. Laços de repetição](#6-laços-de-repetição)
- [7. Formatação de texto](#7-formatação-de-texto)
- [8. Expressões Regulares `REGEX`](#8-expressões-regulares-regex)
- [9. Manipulação de Data e Tempo](#9-manipulação-de-data-e-tempo)
- [10. Coleções](#10-coleções)
  - [10.1 List](#101-list)
  - [10.2 Set](#102-set)
    - [10.2.1 HashSet](#1021-hashset)
    - [10.2.2 LinkedHashSet](#1022-linkedhashset)
    - [10.2.3 TreeSet](#1023-treeset)
  - [10.3 Map](#103-map)
    - [10.3.1 HashMap](#1031-hashmap)
    - [10.3.2 LinkedHashMap](#1032-linkedhashmap)
    - [10.3.3 TreeMap](#1033-treemap)
- [11. Streams](#11-streams)
- [12. Programação Orientada a Objetos](#12-programação-orientada-a-objetos)
  - [12.1. Classes x Objetos](#121-classes-x-objetos)
  - [12.2. Atributos](#122-atributos)
  - [12.3. Métodos](#123-métodos)
  - [12.4. Encapsulamento](#124-encapsulamento)
  - [12.5. Modificadores de acesso](#125-modificadores-de-acesso)
  - [12.6. Herança](#126-herança)
  - [12.7. Polimorfismo](#127-polimorfismo)
    - [12.7.1. Sobrescrita](#1271-sobrescrita)
    - [12.7.2. Sobrecarga](#1272-sobrecarga)
  - [12.8. Classe Abstrata](#128-classe-abstrata)
  - [12.9. Métodos Abstratos](#129-métodos-abstratos)
  - [12.10. Interface](#1210-interface)
<!-- /TOC -->

## 1 Variáveis
### 1.1 Variáveis de tipo primitivo

Números inteiros
```java
int quantidadePassos = 500;
```

Números de ponto flutuante - `64 bits` - Precisão aproximada: `15 casas decimais`
```java
double alturaEmMetros = 1.60;
```

Números de ponto flutuante - `32 bits` - Precisão aproximada: `6 a 7 casas decimais`
```java
float temperatura = 36.5f;
```

Byte - `8 bits` - Intervalo `-128` a `127`
```java
byte idade = 30;
```

Short - `16 bits` - Intervalo `-128` a `127`
```java
short ano = 2024;
```

Long - `64 bits` - Intervalo `-9.223.372.036.854.775.808` a `9.223.372.036.854.775.807`
```java
long populacaoMundial = 8000000000L;
```

Caracteres
```java
char inicial = 'J';
```

Booleanos - `true` ou `false`
```java
boolean ativo = true;
```

### 1.2 Variáveis de tipo referencial

Texto ou cadeia de caracteres
```java
String nome = "José";
```

Arrays
```java
int[] numeros = {1, 2, 3, 4, 5};
```

Objeto de classe
```java
Paciente jose = new Paciente();
```

Objetos de classes wrapper `Empacotadoras`

- Números inteiros
```java
Integer idade = 30;
```

- Números de ponto flutuante
```java
Double peso = 70.5;
```

- Booleanos
```java
Boolean aprovado = false;
```

Coleções
```java
ArrayList<String> nomes = new ArrayList<>();
```

---

## 2. Conversão de dados

- Conversão implícita:
```java
int alturaEmCentimetros = (int) (alturaEmMetros * 100);

System.out.println(alturaEmCentimetros);
```

- Conversão explícita:
```java
alturaEmCentimetros = 170;
alturaEmMetros = alturaEmCentimetros / 100;
        
System.out.println(alturaEmMetros);
```

- Casting:
```java
((Gerente) gerente).setBonus(1000);
```

---

## 3. Escopo de variáveis

O escopo de uma variável determina onde ela pode ser acessada no código. Variáveis declaradas dentro de blocos (`{}`) só existem dentro desses blocos.

```java
double alturaEmMetros = 1.60; // Variável com escopo global ao método
String sugestao; // Declarada fora do IF, disponível em todo o método

if (quantidadePassos < 1000) { 
    sugestao = "Sugiro que você tente aumentar a meta!"; // Atribuição dentro do IF
    System.out.println(sugestao);
    alturaEmMetros = 2.3;
}

// Aqui, ainda é possível acessar 'sugestao' e 'alturaEmMetros'
System.out.println(sugestao); 
System.out.println(alturaEmMetros);
```

> Se a variável `sugestao` fosse declarada dentro do bloco `if`, ela não estaria disponível fora dele. Por isso, para acessar a variável após o bloco, declare-a antes do `if`.

---

## 4. Operadores

- Operadores Aritméticos:

| Operador | Nome           | Exemplo | Resultado                       |
| -------- | -------------- | ------- | ------------------------------- |
| `+`      | Adição         | `a + b` | Soma os operandos               |
| `-`      | Subtração      | `a - b` | Subtrai `b` de `a`              |
| `*`      | Multiplicação  | `a * b` | Multiplica `a` por `b`          |
| `/`      | Divisão        | `a / b` | Divide `a` por `b`              |
| `%`      | Módulo (resto) | `a % b` | Resto da divisão de `a` por `b` |

- Operadores Relacionais:

| Operador | Nome           | Exemplo  | Resultado                          |
| -------- | -------------- | -------- | ---------------------------------- |
| `==`     | Igualdade      | `a == b` | `true` se `a` for igual a `b`      |
| `!=`     | Diferente      | `a != b` | `true` se `a` for diferente de `b` |
| `>`      | Maior que      | `a > b`  | `true` se `a` for maior que `b`    |
| `<`      | Menor que      | `a < b`  | `true` se `a` for menor que `b`    |
| `>=`     | Maior ou igual | `a >= b` | `true` se `a` ≥ `b`                |
| `<=`     | Menor ou igual | `a <= b` | `true` se `a` ≤ `b`                |

- Operadores Lógicos:

| Operador | Nome             | Exemplo           |Resultado                                      |      
| -------- | ---------------- | ----------------- | ---------------------------------------------- | 
| `&&`     | E lógico (*AND*) | `a > 0 && b < 10` | `true` se ambas as condições forem verdadeiras |  
|  Ou lógico (*OR*)       |    \`a > 0               | b < 10\`  `true` se pelo menos uma condição for verdadeira   | `true` se pelo menos uma condição for verdadeira |
| `!`      | Negação (*NOT*)  | `!isento`         | Inverte o valor lógico                        |   
- Operadores de Atribuição:

| Operador | Nome                 | Exemplo  | Equivalente      |
| -------- | -------------------- | -------- | ---------------- |
| `=`      | Atribuição simples   | `a = 10` | Atribui 10 a `a` |
| `+=`     | Soma e atribuição    | `a += 5` | `a = a + 5`      |
| `-=`     | Subtrai e atribui    | `a -= 3` | `a = a - 3`      |
| `*=`     | Multiplica e atribui | `a *= 2` | `a = a * 2`      |
| `/=`     | Divide e atribui     | `a /= 4` | `a = a / 4`      |
| `%=`     | Módulo e atribui     | `a %= 2` | `a = a % 2`      |

- Operadores Unários:

| Operador | Nome              | Exemplo       | Descrição                             |
| -------- | ----------------- | ------------- | ------------------------------------- |
| `+`      | Valor positivo    | `+a`          | Retorna o valor positivo de `a`       |
| `-`      | Valor negativo    | `-a`          | Inverte o sinal de `a`                |
| `++`     | Incremento        | `a++` / `++a` | Soma 1 a `a` (pós/pre)                |
| `--`     | Decremento        | `a--` / `--a` | Subtrai 1 de `a` (pós/pre)            |
| `!`      | Lógico de negação | `!condicao`   | Inverte o valor lógico (true ↔ false) |

- Operadores Bit a Bit:

| Operador | Nome                   | Exemplo      | Descrição                                       |  
| -------- | ---------------------- | ------------ | ----------------------------------------------- | 
| `&`      | AND bit a bit          | `a & b`      | Compara bit a bit (1 se ambos forem 1)          |    
| \`       | \`                     | OR bit a bit | \`a                                       b\` Compara bit a bit (1 se um dos dois for 1) |
| `^`      | XOR bit a bit          | `a ^ b`      | 1 se os bits forem diferentes                   |   
| `~`      | Complemento bit a bit  | `~a`         | Inverte todos os bits                           |   
| `<<`     | Shift à esquerda       | `a << 2`     | Desloca bits 2 posições à esquerda (multiplica) |   
| `>>`     | Shift à direita        | `a >> 2`     | Desloca bits 2 posições à direita (divide)      |   
| `>>>`    | Shift lógico à direita | `a >>> 2`    | Igual ao `>>`, mas preenche com 0 à esquerda    |   


## 5. Estrutura condicional

```java
String nome = "João";
double salario = 2890.0;
int numeroDependentes = 2;
boolean isento = true;

if (salario > 2259.20 && !isento) {
    double irrf = salario / 100 * 7.5;
    System.out.println("Valor do IRRF: " + irrf);
} else if (isento) {
    System.out.println("Contribuinte isento de IRRF.");
}
else {
    System.out.println("Não há valores de IRRF a serem descontados.");
}
```

## 6. Laços de repetição

for
```java
String[] vendedores = {"Carlos", "Mariana", "João", "Fernanda"};
double[] vendas = {4000.00, 8000.00, 12000.00, 5000.00};

for (int i = 0; i < vendedores.length; i++) {
    if (vendedores[i].equalsIgnoreCase("mariana")) {
        // break; // Para o looping quando a condição é verdadeira
        continue; // Pula o índice quando a condição é verdadeira
    }
    System.out.printf("%s - comissão %.2f\n", vendedores[i], calcularComissao(vendas[i]));
}
```

for each
```java
String[] vendedores = {"Carlos", "Mariana", "João", "Fernanda"};
double[] vendas = {4000.00, 8000.00, 12000.00, 5000.00};

for (String nomeVendedor : vendedores) {
    System.out.printf("Nome: " + nomeVendedor + "\n");
}
```

while
```java
int j = 0;
boolean imprimeOutro = true;
Scanner leitura = new Scanner(System.in);

while (imprimeOutro) {
    System.out.printf("%s - comissão %.2f\n", vendedores[j], calcularComissao(vendas[j]));
    j++;
    System.out.println("Deseja imprimir outro?");
    imprimeOutro = leitura.nextBoolean();
}
```

do while
```java
int j = 0;
boolean imprimeOutro = true;
Scanner leitura = new Scanner(System.in);

do {
    System.out.printf("%s - comissão %.2f\n", vendedores[j], calcularComissao(vendas[j]));
    j++;
    System.out.println("Deseja imprimir outro?");
    imprimeOutro = leitura.nextBoolean();
} while (imprimeOutro);
```

## 7. Formatação de texto

Declaração de String:
```java
String professor = "Jacqueline Oliveira";
```

Declaração de Text Block `String formatada em bloco`:
```java
String curriculo = """
                Pós graduada em Engenharia de Software e
                Arquitetura de Software;
                Desenvolvedora backend Java desde 2010;
                """;
```

<u>Especificadores de formatação:</u>

| Especificador | Semântica                          | Exemplo de uso                         | Saída esperada           |
|---------------|------------------------------------|----------------------------------------|--------------------------|
| `%s`          | Placeholder para `String`          | `String.format("Olá, %s!", "Arthur")`  | `Olá, Arthur!`           |
| `%d`          | Inteiro decimal (`int`, `long`)    | `String.format("ID: %d", 42)`          | `ID: 42`                 |
| `%.2f`        | Ponto flutuante com 2 casas decimais | `String.format("R$: %.2f", 99.456)`  | `R$: 99.46`              |
| `%n`          | Nova linha (plataforma-independente) | `String.format("Linha 1%nLinha 2")`  | `Linha 1`<br>`Linha 2`   |
| `%05d`        | Inteiro com padding de zeros       | `String.format("%05d", 42)`            | `00042`                  |
| `%-10s`       | Alinhamento à esquerda em 10 chars | `String.format("%-10s", "OK")`         | `OK        `             |


format:
```java
String texto = String.format("Disciplina: %s - %s", disciplina.trim(), professor.toUpperCase());

System.out.println(texto);
```

printf
```java
System.out.printf("Nome: %s %nDisciplina: %s", professor, disciplina);
```

Letras Maiúsculas:
```java
professor.toUpperCase();
```

Letras minúsculas:
```java
professor.toLowerCase();
```

Remover espaços:
```java
professor.trim();
```

Substituir:
```java
professor.replace("Oliveira", "Magalhães")
```

## 8. Expressões Regulares `REGEX`

Formato E-mail
```java
String texto = "Meu email é jacqueline@alura.com";

String regex = "\\w+@\\w+\\.\\w+";
Pattern pattern = Pattern.compile(regex);
Matcher matcher = pattern.matcher(texto);

if (matcher.find()) {
    System.out.println(matcher.group());
}

System.out.println(formatarTelefone("2199887744"));
```

Formato Telefone
```java
String telefone = "2199887744";

String regex = "(\\d{2})(\\d{4,5})(\\d{4})";
Pattern pattern = Pattern.compile(regex);
Matcher matcher = pattern.matcher(telefone);

if (matcher.matches()) {
    return String.format("(%s) %s-%s", matcher.group(1), matcher.group(2), matcher.group(3));
}
```

---

## 9. Manipulação de Data e Tempo

Data atual de acordo com o local - Padrão: `ISO 8601`
```java
LocalDate dataCompra = LocalDate.now();
```

Especificando uma data - Padrão: `ISO 8601`
```java
LocalDate dataPrimeiraParcela = LocalDate.of(2025, 5, 15);
```

Somar dias na data - Padrão: `ISO 8601`
```java
LocalDate segundaParcela = dataPrimeiraParcela.plusDays(30);
```

Condicionais com datas - Padrão: `ISO 8601`
```java
if (dataPrimeiraParcela.isBefore(LocalDate.now())) {
    System.out.println("Hoje é o dia do vencimento");
} else {
    System.out.println("Superior ao dia do vencimento");
}
```

Formatação de data - Padrão `BR`
```java
DateTimeFormatter formato = DateTimeFormatter.ofPattern("dd/MM/yyyy");

System.out.println("Data formatada: " + dataCompra.format(formato));
```

Fuso horário - `Localidade Atual`
```java
ZonedDateTime dataConclusaoCompra = ZonedDateTime.now();

System.out.println("Data de conclusão da compra formatada: " + dataConclusaoCompra);
```

Fuso horário - `Localidade Nova York`
```java
ZonedDateTime dataCompraNy = dataConclusaoCompra.withZoneSameInstant(ZoneId.of("America/New_York"));

System.out.println("Data de conclusão da compra em Nova Iorque: " + dataCompraNy);
```

Calcular duração de tempo entre `Tempo Inicial` e `Tempo Final`
```java
LocalTime inicio = LocalTime.of(9 , 0);
LocalTime fim = LocalTime.of(17, 30);
Duration duracao = Duration.between(inicio, fim);

System.out.println("Duração do expediente: " + duracao.toHours() + " horas e " + duracao.toMinutesPart() + " minutos");
```

Calcular período entre `Data da Compra` e `Data do Pagamento`
```java
LocalDate dataCompra = LocalDate.now();
LocalDate dataPagamento = LocalDate.parse("2025-10-30");
Period periodo = Period.between(dataCompra, dataPagamento);

System.out.println("Diferença em dias: " + periodo.getDays());
```

---

## 10. Coleções

### 10.1 List
```java
List<String> funcionarios = new ArrayList<>();
funcionarios.add("João");
funcionarios.add("Maria");
funcionarios.add("João");

System.out.println(funcionarios.get(1)); // Recupera pelo índice da lista [1] = "Maria"
```
- Listas permitem duplicatas.
- Garante a ordem dos elementos.
- Manipulação dos elementos

### 10.2 Set

#### 10.2.1 HashSet
```java
Set<String> produtos = new HashSet<>();
produtos.add("Água");
produtos.add("Coca-Cola");
produtos.add("Água"); // Ignorado, duplicata

System.out.println(produtos);
```
- Não permite duplicatas.
- Não garante ordem dos elementos.
- Operações de inserção, remoção e busca são `O`(`1`) na média.

> Utilizado quando performance é prioridade e a ordem dos dados não é relevante.

#### 10.2.2 LinkedHashSet
```java
Set<String> produtos = new LinkedHashSet<>();
produtos.add("Água");
produtos.add("Coca-Cola");
produtos.add("Água"); // Ignorado, duplicata

System.out.println(produtos);
```
- Mantém a ordem de inserção dos elementos.
- Também não permite duplicatas.
- Leve overhead comparado ao `HashSet` para manter a ordem.

> Utilizado quando há necessidade de preservar a sequência de entrada, como em logs ordenados ou exibições controladas.

#### 10.2.3 TreeSet
```java
Set<String> produtos = new TreeSet<>();
produtos.add("Água");
produtos.add("Coca-Cola");
produtos.add("Água"); // Ignorado, duplicata

System.out.println(produtos);
```
- Ordena os elementos de forma `natural` ou por um `Comparator`.
- Também não permite duplicatas.
- Operações custam O(`log n`) devido à estrutura de árvore balanceada `Red-Black Tree`.

> Utilizado quando é necessário manter os dados ordenados automaticamente e fazer buscas ordenadas ou navegação `ceiling, floor, subSet, etc.`

### 10.3 Map

#### 10.3.1 HashMap
```java
Map<Integer, String> clientes = new HashMap<>();
clientes.put(1, "Maria");
clientes.put(2, "Marcos");
clientes.put(3, "Ana");

System.out.println(clientes.get(1)); // Acessa o valor associado à chave 1
```
- Estrutura baseada em tabela de hash.
- Não garante ordem das chaves ou valores.
- Permite null como chave e múltiplos null como valor.
- Operações básicas `put, get, remove` com complexidade média de `O`(`1`).

> Utilizado para armazenar grandes volumes de pares chave/valor onde ordem não é requisito e performance é prioridade.

#### 10.3.2 LinkedHashMap
```java
Map<String, Integer> estoque = new LinkedHashMap<>();
estoque.put("Água", 10);
estoque.put("Coca-Cola", 5);

System.out.println(estoque); // Ordem: Água, Coca-Cola
```
- Extende HashMap com uma lista duplamente ligada para manter a ordem de inserção.
- Performance semelhante ao HashMap, com leve overhead.
- Também permite null como chave.

> Utilizado quando se deseja previsibilidade na ordem de iteração (ex.: cache, logs estruturados).

#### 10.3.3 TreeMap
```java
Map<String, Integer> estoque = new TreeMap<>();
estoque.put("Coca-Cola", 5);
estoque.put("Água", 10);

System.out.println(estoque); // Ordenado alfabeticamente
```
- Implementado como uma árvore rubro-negra `Red-Black Tree`.
- Mantém as chaves ordenadas de forma natural ou via Comparator customizado.
- Não permite null como chave.
- Operações têm custo `O`(log `n`).

> Utilizado em aplicações que requerem ordenação automática das chaves (ex.: relatórios, estruturas de ranking, range queries).

---

## 11. Streams

Streams é uma forma moderna que utiliza `Programação Funcional` para realizar filtros, transformações e agregações em coleções, através de encadeamento de métodos, mantendo a estrutura original.

Funções Lambda
```java
// Função Lambda - Filtra nomes que começam com a letra "A"
nome -> nome.startsWith("A")
```

Filtra os nomes de funcionários que começam com a letra "A":
```java
List<String> funcionarios = List.of("Ana", "Bruno", "Carlos", "Amanda");

List<String> funcionariosLetraA = functionarios.stream()
                .filter(f -> f.startsWith("A"))
                .collect(Collectors.toList());

System.out.println(funcionarios); // Coleção original
System.out.println(funcionariosLetraA); // Nova coleção gerada com base na original
```

Transforma os valores de venda em comissão:
```java
List<Double> valorVendas = List.of(500.0, 1800.0, 6200.0);

List<Double> comissao = valorVendas.stream()
                .map(v -> v * 0.05)
                .collect(Collectors.toList());

System.out.println(valorVendas); // Coleção original
System.out.println(comissao); // Nova coleção gerada com base na original
```

Soma os valores de venda:
```java
List<Double> valorVendas = List.of(500.0, 1800.0, 6200.0);

double totalVendas = valorVendas.stream()
                .reduce(0.0, Double::sum);

System.out.println(valorVendas); // Coleção original
System.out.println(totalVendas); // Nova coleção gerada com base na original
```

---

## 12. Programação Orientada a Objetos

### 12.1. Classes x Objetos

- `Classe`: É um modelo que define o tipo de objeto, seus atributos e métodos.
- `Objeto`: É uma instância concreta e particular dessa classe, com valores específico para seus atributos.


Declaração de uma classe:
```java
public class Funcionario {
    ... // Restante do código
}
```

Instância da classe Funcionário, criando o objeto funcionário 1
```java
Funcionario funcionario1 = new Funcionario();
```

### 12.2. Atributos

- `Atributos`: São variáveis que armazenm informações ou dados específicos de um objeto de uma classe.

Declaração dos atributos de uma classe
```java
public class Funcionario {
    // Atributos de um Funcionário
    String nome;
    String cargo;
    double salario;

    ... // Restante do código
}
```

Definição de valores dos atributos do objeto funcionário 1
```java
Funcionario funcionario1 = new Funcionario();
// Valores dos atribuitos do funcionário 1
funcionario1.nome = "Ana";
funcionario1.cargo = "Gerente de Projetos";
funcionario1.salario = 9000.00;
```

### 12.3. Métodos

- `Métodos`: São funções que definem o comportamento ou as ações que os objetos de uma classe podem realizar.

Exemplos de métodos:
```java
// Não recebe argumento e retorna vazio (VOID)
public void exibeMensagem() {
    System.out.println("Seja bem-vindo!");
}

// Não recebe argumento e retorna um valor
public String retornaMensagem() {
    return "Seja bem-vindo!";
}

// Recebe argumentos e retorna vazio (VOID)
public void exibirSoma(int a, int b) {
    int r = a + b;
    System.out.println("Resultado: " + r);
}

// Recebe argumentos e retorna vazio (VOID)
public int retornaMultiplicacao(int a, int b) {
    return a * b;
}
```

No Java também possuímos os `Métodos Estáticos` ou `Métodos de Classe` que são associados a classe em vez de a uma instância específica da classe. Podem ser chamados diretamente através do nome da classe, sem a necessidade de criar um objeto da classe.

Exemplo:
```java
public class Utilitarios {

    // Método estático
    public static void exibirSaudacao() {
        System.out.println("Olá! Seja bem-vindo ao sistema.");
    }
}

Utilitarios.exibirSaudacao(); // Chamada direta sem instanciar
```

**Método Especial `main`**: 
```java
public class Main {
    // Método main é estático
    public static void main(String[] args) {
        ... // Restante do código
    }
}
```

**Curiosidades sobre o método `main`:**
- É o único método obrigatório para execução de uma aplicação.
- A JVM `Java Virtual Machine` procura por este método para iniciar o programa.
- Ele pode receber argumentos externos `via terminal, build scripts, etc.`
- Sua assinatura não pode ser alterada — caso contrário, a execução falha com erro Main method not found in class.
- Pode haver múltiplos métodos main em diferentes classes, mas a JVM executa apenas o especificado no ponto de partida.
- Não é usado em aplicações web, Android ou Java EE, que têm pontos de entrada específicos `ex: servlets, activities, etc.`

**Composição:**

| Elemento        | Significado                                                          |
| --------------- | -------------------------------------------------------------------- |
| `public`        | Acesso público — o Java Runtime precisa conseguir acessá-lo.         |
| `static`        | Não depende de instância da classe — executado diretamente pela JVM. |
| `void`          | Não retorna nada.                                                    |
| `main`          | Nome fixo reconhecido pela JVM como ponto de entrada.                |
| `String[] args` | Argumentos de linha de comando, caso sejam passados.                 |

Declaração dos métodos de uma classe
```java
public class Funcionario {
    String nome;
    String cargo;
    double salario;

    // Declaração dos métodos de uma classe
    public void exibirInformacoes() {
        System.out.println("Nome: " + nome);
        System.out.println("Cargo: " + cargo);
        System.out.println("Salário: R$ " + salario);
    }

    public void reajustarSalario(double percentual) {
        salario += salario * (percentual / 100);
        System.out.printf("Salário reajustado para: R$ " + salario);
    }
}
```

Chamada dos métodos do objeto funcionário 1
```java
Funcionario funcionario1 = new Funcionario();
funcionario1.nome = "Ana";
funcionario1.cargo = "Gerente de Projetos";
funcionario1.salario = 9000.00;
// Chamada dos métodos do objeto funcionário 1
funcionario1.exibirInformacoes();
funcionario1.reajustarSalario(5);
```

### 12.4. Encapsulamento
É um conceito fundamental para restringir os acessos diretos aos atributos de uma classe, a ideia é que seja fornecido métodos específicos para que o acesso seja feito. Garantindo que os dados importantes apenas a classe tenha o acesso para alterá-los.

**Benefícios:**
- Segurança.
- Controle.
- Manutenção.

Encapsulamento na prática
```java
public class Funcionario {
    // Todos os atributos são privados. Para que outras classes não tenham acesso diretamente aos atributos da classe, 
    // Garantindo maior controle e segurança dos dados.
    private String nome;
    private String cargo;
    private double salario;
    private int controleReajuste = 0;

    // Definindo um construtor personalizado.
    // Assim todo funcionário criado deverá ter como premissa um nome e o salário para que o objeto seja criado.
    public Funcionario(String nome, double salario) {
        this.nome = nome;
        this.salario = salario;
    }

    // Definição de métodos Getters(Leitura) e Setters(Escrita)
    public String getCargo() {
        return cargo;
    }

    public void setCargo(String cargo) {
        this.cargo = cargo;
    }

    public String getNome() {
        return nome;
    }

    public double getSalario() {
        return salario;
    }

    public void exibirInformacoes() {
        System.out.printf("%nFuncionário %s - Cargo %s - Salário R$ %.2f%n", nome, cargo, salario);
    }

    public void reajustarSalario(double percentual) {
        // Condicional para garantir que o reajuste de salário seja aplicado apenas uma vez
        if (controleReajuste >= 1) {
            System.out.println("Não pode fazer reajustes.");
        } else {
            controleReajuste++;
            salario += salario * (percentual / 100);
            System.out.printf("Salário reajustado para: R$ %.2f%n", salario);
        }
    }
}
```

Chamada com encapsulamento
```java
// Intância um objeto funcionário
// Considerando os atributos obrigatórios do construtor
Funcionario funcionario = new Funcionario("João", 8500.00);

// Chamada do método Setter para o atributo cargo
funcionario.setCargo("Desenvolvedor");

// Chamada dos métodos Getter para leitura dos atributos
System.out.println("Funcionário tem o nome: " + funcionario.getNome());
System.out.println("Funcionário tem o cargo: " + funcionario.getCargo());
System.out.println("Funcionário tem o salário: " + funcionario.getSalario());

// Chamada dos métodos
funcionario.reajustarSalario(5);
funcionario.reajustarSalario(10);
funcionario.exibirInformacoes();
```

### 12.5. Modificadores de acesso

| Modificador       | Visibilidade                                                   | Aplicável a         | Uso típico                                     |
|-------------------|----------------------------------------------------------------|----------------------|------------------------------------------------|
| `public`          | Visível por todas as classes de qualquer pacote                | Classes, métodos, atributos, construtores | APIs públicas, pontos de integração externa   |
| `protected`       | Visível no mesmo pacote **e** por subclasses (mesmo fora do pacote) | Métodos, atributos, construtores           | Extensibilidade controlada por herança        |
| *package-private* | Visível apenas dentro do mesmo pacote (**sem modificador**)    | Classes, métodos, atributos, construtores | Lógica interna entre classes do mesmo módulo  |
| `private`         | Visível apenas dentro da própria classe                        | Métodos, atributos, construtores           | Encapsulamento de detalhes de implementação   |


### 12.6. Herança
Permite que uma classe filha `Subclasse` dervive características e comportamentos da classe mãe `Superclasse`, assim derivando características e comportamentos dela.

SuperClasse Funcionario
```java
public class Funcionario {
    // Atributos que pertencem a SuperClasse Funcionario que serão herdados
    private String nome;
    private double salario;

    // Métodos que pertencem a SuperClasse Funcionario que serão herdados
    public Funcionario(String nome, double salario) {
        this.nome = nome;
        this.salario = salario;
    }

    public void exibirInformacoes() {
        System.out.printf("Funcionário %s - Salário R$ %.2f", nome, salario);
    }

    public void reajustarSalario(double percentual) {
        salario += salario * (percentual / 100);
        System.out.printf("\nNovo salário de %s é %.2f", nome, salario);
    }
}

```

Subclasse Desenvolvedor
```java
public class Desenvolvedor extends Funcionario { // Desenvolvedor é um Funcionário
    // Atributo específico da SubClasse Desenvolvedor
    private String stack;

    // Definição de um construtor com herança da SuperCalsse Funcionário
    public Desenvolvedor(String nome, double salario, String stack) {
        super(nome, salario);
        this.stack = stack;
    }
}
```

Chamada Desenvolvedor
```java
// Instância de um objeto desenvolvedor
// Note que considero os atributos de Funcionario + o atributo de desenvolvedor
Desenvolvedor desenvolvedor = new Desenvolvedor("Carla", 12000, "Backend Java");

// Como a classe Desenvolvedor é um Funcionario posso chamar os método definidos na classe Funcionario
desenvolvedor.exibirInformacoes();
```

SubClasse Gerente
```java
public class Gerente extends Funcionario { // Gerente é um Funcionário 
    // Atributo específico da SubClasse Gerente
    private double bonus;

    // Definição de um construtor com herança da SuperCalsse Funcionário
    public Gerente(String nome, double salario) {
        super(nome, salario);
    }

    // Métodos de atribuição específicos da SubClasse Gerente
    public double getBonus() {
        return bonus;
    }

    public void setBonus(double bonus) {
        this.bonus = bonus;
    }
}
```

Chamada Gerente
```java
// Instância de um objeto gerente
// Note que considero os atributos de Funcionario + o atributo de gerente
Gerente gerente = new Gerente("Mario", 15000);
gerente.setBonus(1000);

// Como a classe Gerente é um Funcionario posso chamar os método definidos na classe Funcionario
gerente.exibirInformacoes();
gerente.reajustarSalario(2);
```

> No Java não é possível que uma Subclasse herde de duas Superclasses ao mesmo tempo.

### 12.7. Polimorfismo

#### 12.7.1. Sobrescrita
É capacidade de uma `subclasse` fornecer uma implementação específica de um método já definido na sua `superclasse` ou `interface`.

Superclasse
```java
public class Funcionario {
    // Alterado para o modificador de acesso "protected"
    // Isso garante que as subclasses tenham acesso diretamente aos atributos da superclasse
    protected String nome;
    protected double salario;

    public Funcionario(String nome, double salario) {
        this.nome = nome;
        this.salario = salario;
    }

    // Método que será sobrescrito na subclasse
    public void exibirInformacoes() {
        System.out.printf("\nFuncionário %s - Salário R$ %.2f", nome, salario);
    }

    ...// Restante do código
}
```

Subclasse
```java
public class Desenvolvedor extends Funcionario {
    private String stack;

    public Desenvolvedor(String nome, double salario, String stack) {
        super(nome, salario);
        this.stack = stack;
    }

    // Sobrescreve o método da Superclasse na Subclasse
    @Override
    public void exibirInformacoes() {
        System.out.printf("\nDesenvolvedor %s - Salário R$ %.2f - Stack %s", super.nome, super.salario, stack);
    }
}
```

#### 12.7.2. Sobrecarga
É a definição de múltiplos métodos com o mesmo nome, mas com assinaturas diferentes dentro da mesma `classe` ou por `herança`).

```java
public class Funcionario {
    ... // Restante do código

    public void reajustarSalario(double percentual) {
        salario += salario * (percentual / 100);
        System.out.printf("\nNovo salário de %s é %.2f", nome, salario);
    }

    // Define o mesmo método com uma assinatura diferente.
    // Não recebe argumento
    public void reajustarSalario() {
        salario += 500;
        System.out.printf("\nSalário com dissídio de %s é %.2f", nome, salario);
    }
}
```

### 12.8. Classe Abstrata
É uma estrutura de código que serve como modelo base para outras classes.

```java
public abstract class Funcionario {
    ... // Restante do código
}
```
> Quando a Superclasse se torna abstrata ela não pode ser instânciada diretamente, pois ela serve apenas como um modelo para as Subclasses que herdam dela.

### 12.9. Métodos Abstratos
Um método abstrato é um método declarado na `Superclasse` mas não implementado, que existe exclusivamente dentro de `classes abstratas` ou `interfaces`, uma espécie de assinatura obrigando todas as `Subclasses` que a implementar esse método.

Superclasse
```java
public abstract class Funcionario {
    ... // Restante do código

    public abstract void calculaPLR();
}
```

Subclasse
```java
public class Desenvolvedor extends Funcionario {
    ... // Restante do código
    
    // Implementa o método abstrato definido na "Superclasse"
    @Override
    public void calculaPLR() {
        System.out.println("\nPLR do Desenvolvedor");
    }
}
```

### 12.10. Interface
É um `contrato` que define o que uma classe deve fazer, mas não como fazer.

Interface
```java
public interface Aprovador {
    // Assinatura do método
    void aprovarProjeto(String nomeProjeto);
}
```

Classe que implementa a interface
```java
package br.com.alura;

public class Gerente extends Funcionario implements Aprovador { // Implementa a interface "Aprovador"
    ... // Restante do código

    // Implementação do método da Interface
    @Override
    public void aprovarProjeto(String nomeProjeto) {
        System.out.printf("\nGerente %s aprovou o projeto: %s", super.nome, nomeProjeto);
    }
}
```

> Diferente de um método abstrato que obriga que todas as subclasses implementem o método, com uma interface é possível implementar esse contrato para subclasses específicas.

> É possível implementar várias interfaces em uma classe.