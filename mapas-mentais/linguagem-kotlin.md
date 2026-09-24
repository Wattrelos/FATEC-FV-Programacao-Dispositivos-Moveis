---
markmap:
  colorFreezeLevel: 2
  initialExpandLevel: 2
  maxWidth: 380
---

# 📱 Programação Mobile: Linguagem Kotlin

## 💎 1. Visão Geral e Características

### 📜 Origem e Trajetória
- **Criação e Liderança**
  - Desenvolvida pela **JetBrains** (2011) e mantida sob licença open-source (Apache 2.0)
  - Batizada em homenagem à **Ilha de Kotlin**, próxima a São Petersburgo
- **Adoção Oficial pelo Google**
  - **Google I/O 2017**: Anúncio do suporte oficial para desenvolvimento Android
  - **Google I/O 2019**: Consolidação da abordagem **"Kotlin-First"** (linguagem prioritária para novos projetos móveis)

### 🚀 Vantagens Estruturais
- **Sintaxe Concisa e Expressiva**
  - Redução drástica de código repetitivo (*boilerplate*) em relação ao Java
  - **Ganho de Produtividade**: Cerca de **67% dos desenvolvedores profissionais** relatam aumento real de produtividade
- **Segurança de Código (*Null Safety*)**
  - Sistema de tipos nativo projetado para eliminar exceções de ponteiro nulo (`NullPointerException`)
  - **Maior Estabilidade**: Aplicativos Android em Kotlin apresentam até **20% menos probabilidade de falhas (*crashes*)**
- **Interoperabilidade Total na JVM**
  - Compila para **Java Bytecode** e executa nativamente na Máquina Virtual Java (**JVM**)
  - **Compatibilidade Bidirecional 100%**: Código Kotlin pode chamar classes Java e vice-versa no mesmo projeto
  - Reutilização direta de todo o ecossistema de bibliotecas e frameworks Java existentes

### 🌐 Versatilidade e Ecossistema
- **Multiplataforma (Kotlin Multiplatform - KMP)**
  - Compartilhamento de lógica de negócio e modelos entre Android, iOS, Desktop (Windows, macOS, Linux) e Web
- **Aplicações Além do Mobile**
  - **Backend & APIs**: Construção de microsserviços modernos com **Ktor** e suporte oficial no **Spring Boot**
  - **Big Data & Pipelines**: Criação de fluxos distribuídos de processamento de dados (Apache Spark / Flink)
  - **Machine Learning**: Modelos preditivos, computação numérica e análise estatística

---

## ⚙️ 2. Estrutura Básica de Código

### 🏁 Ponto de Entrada (Função Principal)
- **Declaração da Função `main`**
  - `fun main() { ... }`: Ponto de entrada padrão e simplificado a partir do Kotlin 1.3
  - `fun main(args: Array<String>) { ... }`: Assinatura clássica quando há necessidade de capturar argumentos de linha de comando
- **Palavra-chave `fun`**
  - Identificador obrigatório para declarar funções, métodos e sub-rotinas

### 📤 Comandos de Saída no Terminal
- **Funções Nativas de Exibição**
  - `println("texto")`: Exibe o conteúdo na saída padrão e adiciona **quebra de linha automática** ao final
  - `print("texto")`: Exibe o conteúdo na saída padrão **mantendo o cursor na mesma linha**
- **Caracteres de Escape Essenciais**
  - `\n`: Quebra de linha manual (*new line*)
  - `\t`: Tabulação horizontal (*tab*)
  - `\"` e `\'`: Escape de aspas para inclusão literal no texto
  - `\$`: Escape do caractere de cifrão para evitar interpolação indevida

### 🔤 Interpolação de Strings (*String Templates*)
- **Injeção de Variáveis**
  - `$variavel`: Insere o valor diretamente no texto (`println("Bem-vindo, $usuario!")`)
- **Avaliação de Expressões**
  - `${expressao}`: Executa cálculos, operadores ou chamadas de métodos dentro da string (`println("Total: ${qtd * preco}")`)
  - Substitui concatenações manuais complexas com operador `+`, gerando código mais legível e limpo

### 📥 Entrada de Dados no Console (*Console Input*)
- **Função `readLine()` (Legado / Padrão)**
  - Captura uma linha completa digitada pelo usuário no terminal
  - **Retorno Anulável (`String?`)**: Pode retornar `null` caso ocorra o fim inesperado do fluxo de dados (EOF)
- **Função `readln()` (Kotlin 1.6+)**
  - Padrão moderno e conciso: lê a entrada e garante retorno direto de **`String` não-nula**
  - Lança `ReadAfterEOFException` se nenhuma linha estiver disponível
- **Função `readlnOrNull()`**
  - Alternativa moderna e segura: retorna `String?` explicitamente sem lançar exceções caso atinja EOF
- **Conversão e Tratamento da Entrada**
  - **Conversão Direta**: `val idade = readln().toInt()`
  - **Conversão Segura com Elvis**: `val preco = readLine()?.toDoubleOrNull() ?: 0.0`

---

## 📦 3. Variáveis, Constantes e Tipagem

### 🏷️ Tipos de Declaração
- **`val` (*Value* - Referência Imutável)**
  - Variável de **somente leitura**: o valor atribuído na inicialização não pode ser alterado
  - Equivalente ao modificador `final` do Java; é a **boa prática recomendada** por padrão no Kotlin
- **`var` (*Variable* - Referência Mutável)**
  - Variável convencional cujo conteúdo pode ser reatribuído livremente durante o ciclo de vida
- **`const val` (Constante de Compilação)**
  - Valor imutável determinado em tempo de compilação; restrito a tipos primitivos e `String`
  - Deve ser declarada no escopo de nível superior (*top-level*) ou dentro de um `object` / `companion object`

### 🎯 Sistema de Tipagem
- **Tipagem Estática e Forte**
  - Todas as variáveis têm tipos definidos e validados rigorosamente em tempo de compilação
  - Bloqueia operações incompatíveis sem coerção ou conversão explícita
- **Inferência de Tipo (*Type Inference*)**
  - O compilador deduz automaticamente o tipo com base no valor atribuído:
    - `val ano = 2026` $\rightarrow$ Tipo inferido como `Int`
    - `val versao = 1.9` $\rightarrow$ Tipo inferido como `Double`
    - `val ativo = true` $\rightarrow$ Tipo inferido como `Boolean`
- **Declaração Explícita de Tipo**
  - Sintaxe canônica: `val identificador: Tipo = valor` (ex: `val curso: String = "Mobile"`)

---

## 🔢 4. Sistema de Tipos de Dados

### 🧩 Paradigma Unificado
- **Tudo é Objeto**
  - No código Kotlin não existe separação sintática entre tipos primitivos e objetos empacotadores (*wrappers*)
  - O desenvolvedor manipula métodos e propriedades diretamente em tipos como `Int` e `Double`
  - Em tempo de compilação, o compilador otimiza o código para tipos primitivos puros na JVM para máximo desempenho

### 🔢 Tipos Numéricos Inteiros
- **`Byte`**: 8 bits de largura (-128 a 127)
- **`Short`**: 16 bits de largura (-32.768 a 32.767)
- **`Int`**: 32 bits de largura (-2.147.483.648 a 2.147.483.647) — **tipo padrão** para literais inteiros
- **`Long`**: 64 bits de largura; indicado obrigatoriamente pelo sufixo `L` (ex: `val bytes = 8000000000L`)

### 💧 Tipos Numéricos Fracionários
- **`Float`**: 32 bits (precisão simples); requer obrigatoriamente o sufixo `F` ou `f` (ex: `val pi = 3.1415f`)
- **`Double`**: 64 bits (precisão dupla) — **tipo padrão** para literais com casas decimais (ex: `val nota = 9.5`)

### 🔠 Caracteres e Cadeias de Texto
- **`Char`**
  - Representa um único caractere Unicode delimitado por **aspas simples** (ex: `'A'`, `'9'`, `'\n'`)
  - Não pode ser atribuído diretamente a um número inteiro (diferente do comportamento em C e Java)
- **`String`**
  - Sequência de caracteres imutável delimitada por **aspas duplas** (ex: `"Kotlin"`)
  - Suporta *Raw Strings* delimitadas por três aspas duplas (`"""..."""`) preservando quebras de linha e sem exigir escape

### ⚖️ Tipo Lógico e Superclasses
- **`Boolean`**: Representa valores lógicos binários (`true` ou `false`)
- **`Number`**: Superclasse abstrata base herdada por todos os tipos numéricos
- **`Any`**: Raiz da hierarquia de classes em Kotlin (equivalente conceitual ao `Object` em Java)

### 🔄 Conversão Explícita de Tipos
- **Ausência de Conversão Implícita (*No Implicit Widening*)**
  - O Kotlin **não promove números automaticamente** para tipos maiores para evitar bugs silenciosos de precisão
  - Exemplo: passar uma variável `Int` para um parâmetro `Long` exige conversão deliberada
- **Métodos Nativos de Conversão**
  - `toByte()`, `toShort()`, `toInt()`, `toLong()`, `toFloat()`, `toDouble()`, `toChar()`, `toString()`
- **Parse Seguro de Texto para Número**
  - `toIntOrNull()` e `toDoubleOrNull()`: convertem `String` para número retornando `null` em caso de erro, prevenindo falhas do tipo `NumberFormatException`

---

## 🛡️ 5. Segurança contra Nulos (*Null Safety*)

### 🎯 O Problema da Referência Nula
- **Eliminação do "Billion Dollar Mistake"**
  - Sistema de tipos concebido para erradicar falhas em tempo de execução causadas por `NullPointerException` (NPE)
  - Diferencia de forma estrita variáveis que podem aceitar valor nulo das que são estritamente não-nulas

### ❓ Tipos Não-Nulos vs. Nulos
- **Tipo Não-Nulo (Padrão da Linguagem)**
  - `var cidade: String = "Campinas"`
  - O compilador bloqueia sumariamente qualquer tentativa de atribuição como `cidade = null`
- **Tipo Nulo (*Nullable*)**
  - `var complemento: String? = null`
  - Indicado obrigatoriamente pelo sufixo de interrogação (`?`) junto ao tipo

### 🧰 Operadores Especializados
- **Operador de Chamada Segura (*Safe Call* `?.`)**
  - Executa o membro ou método apenas se a referência for diferente de nulo:
  - `val tamanho = complemento?.length` (retorna `null` caso `complemento` seja nulo, sem gerar falhas)
- **Operador Elvis (`?:`)**
  - Fornece um valor padrão de substituição caso a expressão à esquerda resulte em nulo:
  - `val enderecoFinal = complemento ?: "Sem complemento"`
- **Operador de Asserção Não-Nula (`!!`)**
  - Força a conversão de um tipo anulável para não-nulo (`complemento!!.uppercase()`)
  - **Atenção**: Dispara `NullPointerException` caso o valor seja nulo; deve ser evitado na rotina
- **Operador de Conversão Segura (*Safe Cast* `as?`)**
  - Tenta realizar o cast de tipo e retorna `null` caso a conversão seja incompatível, evitando a exceção `ClassCastException`

---

## 🔀 6. Estruturas de Controle Expressivas

### 🎛️ Condicionais como Expressões
- **`if / else` com Retorno de Valor**
  - No Kotlin, o bloco `if / else` pode ser empregado diretamente como expressão avaliada:
  - `val resultado = if (media >= 6.0) "Aprovado" else "Recuperação"`
  - Torna obsoleto o operador ternário tradicional (`? :`), inexistente na sintaxe do Kotlin

### 🎯 Estrutura `when` (Substituto Moderno do `switch`)
- **Controle Flexível sem Falhas de Escopo**
  - Não requer instruções manuais de parada (`break`)
  - Suporta múltiplos valores no mesmo caso: `0, 1 -> "Binário"`
  - Suporta testes de intervalo: `in 1..10 -> "Entre 1 e 10"`
  - Suporta validação de tipos em tempo de execução com *Smart Cast*: `is String -> item.length`
  - Pode ser utilizado tanto como instrução de controle quanto como expressão com retorno de valor

### 🔁 Laços de Repetição e Intervalos (*Ranges*)
- **Operadores de Intervalo**
  - `1..5`: Intervalo fechado contendo 1, 2, 3, 4 e 5
  - `1 until 5`: Intervalo aberto no topo contendo 1, 2, 3 e 4
  - `5 downTo 1 step 2`: Contagem regressiva com passo definido (produz 5, 3 e 1)
- **Estruturas de Laço**
  - `for (elemento in colecao)`: Itera uniformemente sobre intervalos, vetores ou listas
  - `while` e `do..while`: Execuções condicionadas com teste no início ou no fim do bloco

### 📦 Orientação a Objetos Moderna
- **`data class` (Classes de Dados)**
  - Declaração em uma única linha para modelar entidades de domínio: `data class Aluno(val id: Int, val nome: String)`
  - Gera automaticamente os métodos `equals()`, `hashCode()`, `toString()`, `copy()` e desestruturação de componentes

---

## 🛠️ 7. Ambiente de Desenvolvimento e Execução

### 💻 Compilador de Linha de Comando (*Command Line Compiler*)
- **Compilador `kotlinc`**
  - Ferramenta oficial para compilação e execução direta via terminal sem necessidade de IDE
  - Geração de pacote executável: `kotlinc arquivo.kt -include-runtime -d programa.jar`
  - Execução via JVM: `java -jar programa.jar`
- **Console Interativo REPL**
  - Executar o comando `kotlinc` sem parâmetros abre o terminal interativo para testar trechos de código em tempo real

### 🌐 Ferramentas e Compiladores Online
- **Kotlin Playground (`play.kotlinlang.org`)**
  - Ambiente web oficial para prototipação, teste de sintaxe e compartilhamento direto de códigos
  - Permite validar algoritmos e exercícios sem instalação de software local
- **OnlineGDB**
  - Compilador online com suporte integral a Kotlin, terminal interativo e passagem de argumentos de linha de comando (*CLI arguments*)

### 🏢 IDEs Profissionais
- **IntelliJ IDEA (JetBrains)**
  - Ambiente oficial de referência; versão gratuita *Community* inclui suporte nativo completo para depuração, testes e refatoração
- **Android Studio (Google)**
  - IDE oficial para desenvolvimento de aplicativos Android construída sob a plataforma IntelliJ
  - Integra emuladores de dispositivos, depuradores visuais e perfilamento de desempenho

### ⚙️ Ferramentas de Automação de Build (*Build Tools*)
- **Gradle**
  - Sistema de automação padrão para projetos Android e ecossistema Kotlin moderno
  - Configurado via `build.gradle.kts` (Kotlin DSL) ou Groovy, gerenciando dependências externas e tarefas de compilação
- **Maven**
  - Ferramenta consagrada de gerenciamento via `pom.xml`, totalmente compatível com projetos Kotlin

### ⚡ Concorrência e Segundo Plano: Corrotinas (*Coroutines*)
- **Processamento Assíncrono Leve**
  - Abordagem oficial do Kotlin para tarefas assíncronas e concorrentes
  - Permite efetuar chamadas de rede (APIs), consultas a bancos locais (SQLite/Room) e processamentos pesados sem travar a interface visual (UI Thread) do aplicativo móvel
