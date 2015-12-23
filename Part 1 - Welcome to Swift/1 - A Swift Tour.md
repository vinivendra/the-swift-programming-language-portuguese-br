# Uma Excursão Rápida

A tradição sugere que o primeiro programa em uma nova linguagem deve imprimir as palavras "Olá, mundo!" na tela. Em Swift, isso pode ser feito em uma só linha:

````
print("Hello, world!")
````

Se você já escreveu código em C ou Objective-C, essa sintaxe é familiar - em Swift, essa linha de código é um programa completo. Você não precisa importar uma biblioteca separada para funcionalidades como entrada e saida ou manipulação de strings. Código escrito em escopo global é usado como o ponto de entrada para o programa, então você não precisa de uma função main(). Você também não precisa escrever pontos e vírgulas no fim de toda linha de código.

<!-- TODO: Existe uma tradução melhor para "string"? -->

Esta excursão te dá informação o suficiente para começar a escrever código em Swift ao te mostrar como completar uma variedade de tarefas de programação. Não se preocupe se não entender algo - tudo o que for introduzido nesta excursão será explicado em detalhe no resto deste livro.

> NOTA

> Em um Mac, descarregue o Playground e clique duas vezes no arquivo para abri-lo no Xcode:
https://developer.apple.com/go/?id=swift-tour
<!-- TODO: Esse link deve ser atualizado para uma versão em português do Playground, quando estiver completo. -->


## Valores Simples

Use `let` para criar uma constante e `var` para criar uma variável. O valor de uma constante não precisa ser conhecido em tempo de compilação, mas deve-se atribuir um valor a essa constante exatamente uma vez. Isso significa que você pode usar constantes para nomear um valor que você determina uma vez mas utiliza em muitos lugares.

````
var minhaVariável = 42
minhaVariável = 50
let minhaConstante = 42
````

Uma constante ou variável precisa ser do mesmo tipo que o valor que você quer atribuir a ela. Apesar disso, você não precisa sempre escrever o tipo explicitamente. Fornecer um valor quando você cria uma constante ou variável deixa o cpmpilador inferir seu tipo. No exemplo acima, o compilador infere que `minhaVariável` é um inteiro porque seu valor inicial é um inteiro.

Se o valor inicial não fornece informação suficiente (ou sse não existe um valor inicial), especifique o tipo escrevendo ele depois da variável, separado por dois pontos.

````
let inteiroImplícito = 70
let doubleImplícito = 70.0
let doubleExplícito: Double = 70
````

> EXPERIÊNCIA

> Crie uma constante com tipo explícito `Float` e valor `4`.

Valores nunca são convertidos explicitamente para outro tipo. Se você precisa converter um valor para um tipo diferente, crie explicitamente uma instância do tipo desejado.

````
let rótulo = "A largura é "
let largura = 94
let rótuloDaLargura = rótulo + String(largura)
````

> EXPERIÊNCIA
> Tente remover a conversão para `String` da última linha. Qual erro aparece?

Existe um jeito ainda mais fácil de incluir valores em strings: escreva o valor em parênteses e coloque uma barra invertida (`\`) antes dos parênteses. Por exemplo:

````
let maçãs = 3
let laranjas = 5
let resumoDeMaçãs = "Eu tenho \(maçãs) maçãs."
let resumoDeFrutas = "Eu tenho \(maçãs + laranjas) pedaços de fruta.
````

> EXPERIÊNCIA
> Use `\()` para incluir um cálculo de ponto flutuante em uma string e para incluir o nome de alguém em um cumprimento.

Crie vetores e dicionários usando colchetes (`[]`), e acesse seus elementos escrevendo o índice ou a chave em conchetes. É permitido colocar uma vírgula após o último elemento.

<!-- Essas traduções não são literais, vão de acordo com as referências externas citadas: o vetor é baseado em uma lista de compras do livro Cidades de Papel, de John Green, e o dicionário é baseado na série Firefly. -->
````
var listaDeCompras = ["bagres", "água", "tulipas", "tinta azul"]
listaDeCompras[1] = "garrafa d'água"

var profissões = [
    "Malcolm": "Capitão",
    "Kaylee": "Mecânica",
]
profissões["Jayne"] = "Relações Públicas"
````

Para criar um vetor vazio ou um dicionário vazio, use a sintaxe de inicializadores.

````
let vetorVazio = [String]()
let dicionárioVazio = [String: Float]()
````

Se a informação sobre o tipo puder ser inferida, você pode escrever um vetor vazio como `[]` e um dicionário vazio como `[:]` - por exemplo, quando você atribui um novo valor a uma variável ou passa um argumento para uma função.

````
listaDeCompras = []
profissões = [:]
````

## Fluxo de Controle

Use `if`  e `switch` para criar condicionais, e use `for-in`, `for`, `while` e `repeat-while` para criar laços. Parênteses em torno da condição ou da variável do laço são opcionais. Chaves em torno do corpo são necessárias.

````
let pontuaçõesIndividuais = [75, 43, 103, 87, 12]
var pontuaçãoDoTime = 0
for pontuação in pontuaçõesIndividuais {
    if pontuação > 50 {
        pontuaçãoDoTime += 3
    } else {
        pontuaçãoDoTime += 1
    }
}
print(pontuaçãoDoTime)
````

Em um `if`, a condição deve ser uma expressão booleana - isso significa que código como `if pontuação { ... }` é um erro, não uma comparação implícita com zero.

Você pode usar `if` e `let` juntos para trabalhar com valores que podem estar faltando. Esses valores são representados como opcionais. Um valor opcional contém ou um valor ou `nil` para indicar a ausência de um valor. Escreva um ponto de interrogação (`?`) depois do tipo de um valor para marcar o valor como opcional.

````
var stringOpcional: String? = "Olá"
print(stringOpcional == nil)

var nomeOpcional: String? = "John Appleseed"
var cumprimento = "Olá!"
if let nome = nomeOpcional {
    cumprimento = "Olá, \(nome)"
}
````

> EXPERIÊNCIA
> Mude `nomeOpcional` para `nil`. Qual cumprimento você obtém? Adicione uma cláusula `else` que atribui um cumprimento diferente se `nomeOpcional` for `nil`.

Se o valor opcional for `nil`, a condição é falsa e o código em chaves é pulado. Caso contrário, o valor opcional é desembrulhado e atribuído à constante que segue o `let`, o que torna o valor desembrulhado disponível dentro do bloco de código.

Outro jeito de lidar com valores opcionais é fornecendo um valor padrão usando o operador `??`. Se o valor opcional estiver ausente, o valor padrão é usado no lugar.

````
let apelido: String? = nil
let nomeCompleto: String = "John Appleseed"
let cumprimentoInformal = "Oi \(apelido ?? nomeCompleto)"
````

Comandos `switch` aceitam qualquer tipo de dados e uma ampla variedade de operações de comparação - eles não são limitados a inteiros e testes de igualdade.

````
let vegetal = "pimenta vermelha"
switch vegetal {
case "aipo":
    print("Adicione algumas uvas passas.")
case "pepino", "agrião":
    print("Isso faz um bom sanduíche.")
case let x where x.hasSuffix("pimenta"):
    print("É uma \(x) quente?")
default:
    print("Tudo fica bom em uma sopa.")
}
````

> EXPERIÊNCIA
> Tente remover o caso `default`. Qual erro você obtém?

Note como `let` pode ser usado em um padrão para atribuir o valor que combinou com aquela parte padrão a uma constante.

Depois de executar o código dentro do caso escolhido, o programa sai do comando `switch`. A execução não continua para o próximo caso, então não é necessário sair explicitamente do `switch` no fim do código de cada caso.

Você usa `for-in` para percorrer itens em um dicionário, fornecendo um par de nomes para usar com cada par de chave e valor. Dicionários são uma coleção sem ordem, então suas chaves e valores são percorridos em ordem arbitrária.

````
let númerosInteressantes = [
    "Primos": [2, 3, 5, 7, 11, 13],
    "Fibonacci": [1, 1, 2, 3, 5, 8],
    "Quadrados": [1, 4, 9, 16, 25],
]
var maior = 0
for (tipo, números) in númerosInteressantes {
    for número in números {
        if número > maior {
            maior = número
        }
    }
}
print(maior)
````

> EXPERIÊNCIA
> Adicione uma nova variável para registrar qual é o tipo do maior número, além do seu valor.

Use `while` para repetir um bloco de código até que uma condição mude. A condição de um laço também pode estar no final, assegurando que o laço seja executado pelo menos uma vez.

````
var n = 2
while n < 100 {
    n = n * 2
}
print(n)

var m = 2
repeat {
    m = m * 2
} while m < 100
print(m)
````

Você pode manter um índice em um laço - usando ou `..<` para determinar a extensão de valores de um índice ou escrevendo explicitamente uma inicialização, uma condição e um incremento. Estes dois laços fazem a mesma coisa:

````
var primeiroLaço = 0
for i in 0..<4 {
    primeiroLaço += i
}
print(primeiroLaço)

var segundoLaço = 0
for var i = 0; i < 4; ++i {
    segundoLaço += i
}
print(segundoLaço)
````

Use `..<` para determinar uma extensão de valores que exclui seu valor superior, e use `...` para criar uma que o inclui.

<!-- TODO: Existe tradução melhor para closure? -->
## Funções e Closures

Use `func` para declarar uma função. Chame a função adicionando, depois de seu nome, uma lista de argumentos entre parênteses. Use `->` para separar, de um lado, os nomes e tipos dos parâmetros e, do outro, o valor de retorno da função.

````
func cumprimentar(nome: String, dia: String) -> String {
    return "Olá \(nome), hoje é \(dia)."
}
greet("Bob", dia: "terça-feira")
````

> EXPERIÊNCIA
> Remova o parâmetro `dia`. Adicione um parâmetro para incluir o especial do almoço de hoje no cumprimento.

Usa uma tupla para criar um valor composto - por exemplo, para retornan múltiplos valores de uma função. Os elementos de uma tupla podem ser referenciados ou por nome ou por número.

````
func calcularEstatisticas(pontuações: [Int]) -> (min: Int, max: Int, soma: Int) {
    var min = scores[0]
    var max = scores[0]
    var soma = 0

    for pontuação in pontuações {
        if pontuação > max {
            max = pontuação
        } else if pontuação < min {
            min = pontuação
        }
        soma += pontuação
    }

    return (min, max, soma)
}
let estatísticas = calcularEstatisticas([5, 3, 100, 3, 9])
print(estatísticas.sum)
print(estatísticas.2)
````

Funções também podem ter um número variável de argumentos, coletando eles em um vetor.

````
func somaDe(números: Int...) -> Int {
    var soma = 0
    for número in números {
        soma += número
    }
    return soma
}
somaDe()
somaDe(42, 597, 12)
````

> EXPERIÊNCIA
> Escreva uma função que calcule a média dos seus argumentos.

Funções podem ser aninhadas. Funções aninhadas têm acesso a variáveis que foram declaradas na função externa. Você pode usar funções aninhadas para organizar o código em uma função que for longa ou complexa.

````
func retornaQuinze() -> Int {
    var y = 10
    func adiciona() {
        y += 5
    }
    adiciona()
    return y
}
retornaQuinze()
````

Funções são um tipo de primeira classe. Isso significa que a função pode retornar outra função como seu valor.

````
func criarIncrementador() -> ((Int) -> Int) {
    func somaUm(number: Int) -> Int {
        return 1 + number
    }
    return somaUm
}
var incrementa = criarIncrementador()
incrementa(7)
````

Uma função pode receber outra como um de seus argumentos.

````
func temValoresVálidos(lista: [Int], condição: (Int) -> Bool) -> Bool {
    for item in lista {
        if condição(item) {
            return true
        }
    }
    return false
}
func menosDeDez(número: Int) -> Bool {
    return número < 10
}
var números = [20, 19, 7, 12]
temValoresVálidos(números, condição: menosDeDez)
````

Funções na verdade são um caso especial de closures: blocos de código que podem ser chamados mais tarde. O código em uma closure tem acesso a coisas como variáveis e funções que foram avaliadas no escopo em que a closure foi criada, mesmo se a closure estiver em um escopo diferente quando for executada - você já viu um exemplo disso em funções aninhadas. Você pode escrever uma closure sem nome ao colocá-la entre chaves (`{}`). Use `in` para separar tanto os argumentos quanto o tipo de retorno do corpo da closure.

````
números.map({
    (número: Int) -> Int in
    let resultado = 3 * número
    return resultado
})
````

> EXPERIÊNCIA
> Reescreva a closure para retornar zero para todos os números pares.    

<!-- Existe uma tradução boa de callback ou de delegate? -->

Você tem diversas opções para escrever closures mais concisamente. Quando o tipo de uma closure já é conhecido, como em um callback de um delegate, você pode omitir o tipo dos seus parâmetros, o seu tipo de retorno, ou ambos. Closures que consistirem de apenas um comando implicitamente retornam o valor deste comando.

````
let númerosMapeados = números.map({ número in 3 * número })
print(númerosMapeados)
````

Você pode se referir a parâmetros por número em vez de por nome - essa abordagem é especialmente útil em closures muito curtas. Uma closure passada como último argumento de uma função pode aparecer imediatamente depois dos parênteses. Quando uma closure é o único argumento de uma função, você pode omitir os parênteses.

````
let númerosOrdenados = números.sort { $0 > $1 }
print(númerosOrdenados)
````

## Objetos e Classes

Use `class` seguido do nome de uma classe para criar uma classe. A declaração de uma propriedade em uma classe é escrita do mesmo jeito que a declaração de uma constante ou uma variável, só que contexto de uma classe. Da mesma forma, declarações de métodos e funções são escritas da mesma maneira.

````
class FormaGeométrica {
    var númeroDeLados = 0
    func descriçãoSimples() -> String {
        return "Uma forma geométrica com \(númeroDeLados) lados."
    }
}
````

> EXPERIÊNCIA
> Adicione uma propriedade constante com `let`, e adicione um outro método que recebe um argumento.

Crie uma isntância de uma classe colocando parênteses depois do nome da classe. Use pontos para acessar as propriedades e métodos da instância.

````
var forma = FormaGeométrica()
forma.númeroDeLados = 7
var descriçãoDaForma = forma.descriçãoSimples()
````

Está faltando uma coisa importante nessa versão da classe FormaGeométrica: um inicializador para configurar a classe quando uma instância é criada. Use `init` para criar um.

````
class FormaNomeada {
    var númeroDeLados: Int = 0
    var nome: String

    init(nome: String) {
        self.nome = nome
    }

    func descriçãoSimples() -> String {
        return "Uma forma com \(númeroDeLados) lados."
    }
}
````

Perceba como `self` é usado para distinguir a propriedade `nome` do argumento `nome` passado para o inicializador. Os argumentos para o inicializador são passados como em uma chamada de função quando se cria uma instância de uma classe. É necessário atribuir valores a todas as propriedades - ou em sua declaração (como na propriedade de `númeroDeLados`) ou no inicializador (como em `nome`).

Use `deinit` para criar um des-inicializador se você precisar fazer algum tipo de limpeza antes que o objeto seja apagado da memória.

Subclasses incluem o nome de sua superclasse depois do seu próprio nome, separado por dois pontos. Não é necessário herdar de nenhuma classe raiz padrão, então você pode incluir ou omitir uma superclasse conforme necessário. Métodos em uma subclasse que substituem a implementação da superclasse são marcados com `override` - substituir um método por acidente, sem `override`, é detectado pelo compilador como um erro. O compilador também detecta métodos com `override` que não realmente substituem nenhum método na superclasse.

````
class Quadrado: FormaNomeada {
    var tamanhoDoLado: Double

    init(tamanhoDoLado: Double, nome: String) {
        self.tamanhoDoLado = tamanhoDoLado
        super.init(nome: nome)
        númeroDeLados = 4
    }

    func área() ->  Double {
        return tamanhoDoLado * tamanhoDoLado
    }

    override func descriçãoSimples() -> String {
        return "Um quadrado com lados de tamanho \(tamanhoDoLado)."
    }
}    
let teste = Quadrado(tamanhoDoLado: 5.2, nome: "meu quadrado de teste")
teste.área()
teste.descriçãoSimples()
````

> EXPERIÊNCIA
> Faça outra subclasse de `FormaNomeada` chamada `Círculo` qye rebeba um raio e um nome como parâmetros para o seu inicializador. Implemente um método `área()` e um método `descriçãoSimples()` na classe `Círculo`.

Além de propriedades simples que são armazenadas, propriedades podem usar procedimentos para obter ou alterar seu valor.

````
class TriânguloEquilátero: FormaNomeada {
    var tamanhoDoLado: Double = 0.0

    init(tamanhoDoLado: Double, nome: String) {
        self.tamanhoDoLado = tamanhoDoLado
        super.init(nome: nome)
        númeroDeLados = 3
    }

    var perímetro: Double {
        get {
            return 3.0 * tamanhoDoLado
        }
        set {
            tamanhoDoLado = newValue / 3.0
        }
    }

    override func descriçãoSimples() -> String {
        return "Um triângulo equilátero com lados de tamanho \(tamanhoDoLado)."
    }
}
var triângulo = TriânguloEquilátero(tamanhoDoLado: 3.1, nome: "um triângulo")
print(triângulo.perímetro)
triângulo.perímetro = 9.9
print(triângulo.tamanhoDoLado)
````

No procedimento de alteração (`set`) do valor do `perímetro`, o novo valor tem o nome implícito de `newValue`. Você pode fornecer um nome explícito em parênteses depois de `set`.

Perceba que o inicializador do `TriânguloEquilátero` tem três passos diferentes:

1. Atribuir valor a propriedades que a subclasse declara.
2. Chamar o inicializador da superclasse.
3. Mudar o valor de propriedades definidas pela superclasse. Quaisquer outras configurações que usem métodos ou procedimentos de obtenção e atribuição de propriedades podem ser alteradas a esse ponto.

Se você não precisa calcular o valor da propriedade mas precisa fornecer código que é executado antes e depois de atribuir um novo valor, use `willSet` e `didSet`, respectivamente. O código que você fornecer vai ser executado toda vez que um valor mudar fora de um inicializador. Por exemplo, a classe abaixo se assegura que o tamanho do lado do seu triângulo é sempre o mesmo que o tamanho do lado do seu quadrado.

````
class TriânguloEQuadrado {
    var triângulo: TriânguloEquilátero {
        willSet {
            quadrado.tamanhoDoLado = newValue.tamanhoDoLado
        }
    }
    var quadrado: Quadrado {
        willSet {
            triângulo.tamanhoDoLado = newValue.tamanhoDoLado
        }
    }
    init(tamanho: Double, nome: String) {
        quadrado = Quadrado(tamanhoDoLado: tamanho, nome: nome)
        triângulo = TriânguloEquilátero(tamanhoDoLado: tamanho, nome: nome)
    }
}
var triânguloEQuadrado = TriânguloEQuadrado(tamanho: 10, nome: "outra forma de teste")
print(triânguloEQuadrado.quadrado.tamanhoDoLado)
print(triânguloEQuadrado.triângulo.tamanhoDoLado)
triânguloEQuadrado.quadrado = Quadrado(tamanhoDoLado: 50, nome: "quadrado maior")
print(triânguloEQuadrado.triângulo.tamanhoDoLado)
````

Quando se estiver trabalhando com valores opcionais, você pode escrever `?` antes de operações como métodos, propriedades e indexações. Se o valor de `?` for `nil`, tudo depois do `?` é ignorado e o valor da expressão é `nil`. Caso contrário, o valor opcional é desembrulhado, e tudo depois do `?` é acionado em cima do valor desembrulhado. Em ambos os casos, o valor da expressão é um valor opcional.

````
let quadradoOpcional: Quadrado? = Quadrado(tamanhoDoLado: 2.5, nome: "quadrado opcional")
let tamanhoDoLado = quadradoOpcional?.tamanhoDoLado
````
