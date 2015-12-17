
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


# Valores Simples

Use `let` para criar uma constante e `var` para criar uma variável. O valor de uma constante não precisa ser conhecido em tempo de compilação, mas deve-se associar um valor a essa constante exatamente uma vez. Isso significa que você pode usar constantes para nomear um valor que você determina uma vez mas utiliza em muitos lugares.

````
var minhaVariável = 42
minhaVariável = 50
let minhaConstante = 42
````

Uma constante ou variável precisa ser do mesmo tipo que o valor que você quer associar a ela. Apesar disso, você não precisa sempre escrever o tipo explicitamente. Fornecer um valor quando você cria uma constante ou variável deixa o cpmpilador inferir seu tipo. No exemplo acima, o compilador infere que `minhaVariável` é um inteiro porque seu valor inicial é um inteiro.

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

Se a informação sobre o tipo puder ser inferida, você pode escrever um vetor vazio como `[]` e um dicionário vazio como `[:]` - por exemplo, quando você associa um novo valor a uma variável ou passa um argumento para uma função.

````
listaDeCompras = []
profissões = [:]
````
