---
title: "Autos e janela locais | Microsoft Docs"
ms.custom: ""
ms.date: "12/10/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "hero-article"
f1_keywords: 
  - "vs.debug.autos"
  - "vs.debug.locals"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "janelas variáveis do depurador"
  - "depuração [Visual Studio], janelas variáveis"
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Autos e janela locais
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O **Autos** janela \(durante a depuração, **CTRL \+ ALT \+ V, A**, ou **Debug \/ Windows \/ automóveis**\) e o **locais** janela \(durante a depuração, **CTRL \+ ALT \+ V, L**, ou **Debug \/ Windows \/ locais**\) são muito úteis quando você deseja ver valores de variáveis durante a depuração. O **locais** janela exibe as variáveis que são definidas no escopo local, que geralmente é a função ou método que está sendo executado. O **Autos** janela exibe as variáveis usadas ao redor da linha atual \(o local onde o depurador é interrompido\). Exatamente quais variáveis exibido é diferente em diferentes idiomas. Ver o que as variáveis que aparecem na janela Autos? abaixo.  
  
 Se você precisar de mais informações sobre depuração básica, consulte [Introdução ao depurador](../debugger/getting-started-with-the-debugger.md).  
  
## Examinando objetos nas janelas Autos e locais  
 Matrizes e objetos são exibidos nas janelas Autos e locais como controles de árvore. Clique na seta à esquerda do nome da variável para expandir a exibição para mostrar campos e propriedades. Aqui está um exemplo de um [FileStream](../Topic/FileStream%20Class.md) objeto o **locais** janela:  
  
 ![Locals&#45;FileStream](../debugger/media/locals-filestream.png "Locals\-FileStream")  
  
## Quais variáveis são exibidos na janela Autos?  
 Você pode usar o **Autos** janela no código c\#, Visual Basic e C\+\+. O **Autos** janela não oferece suporte a JavaScript ou F \#.  
  
 Em c\# e Visual Basic, o **Autos** janela exibirá qualquer variável usada na linha atual ou anterior. Por exemplo, se você declara quatro variáveis e defini\-los da seguinte maneira:  
  
```c#  
public static void Main() { int a, b, c, d; a = 1; b = 2; c = 3; d = 4; }  
```  
  
 Se você definir um ponto de interrupção na linha `c = 3`; e executar o depurador quando a execução parar o **Autos** janela terá esta aparência:  
  
 ![Autos&#45;CSharp](../debugger/media/autos-csharp.png "Autos\-CSharp")  
  
 Observe que o valor de `c` é 0, porque a linha `c = 3` ainda não foi executado.  
  
 Em C\+\+ a **Autos** janela exibe variáveis usadas pelo menos três linhas antes da linha atual \(a linha na qual a execução é interrompida\). Se você declarar seis variáveis:  
  
```cpp  
void main() { int a, b, c, d, e, f; a = 1; b = 2; c = 3; d = 4; e = 5; f = 6; }  
```  
  
 Se você definir um ponto de interrupção na linha `e = 5;` e executar o depurador quando a execução parar o **Autos** janela terá esta aparência:  
  
 ![Autos&#45;Cplus](../debugger/media/autos-cplus.png "Autos\-Cplus")  
  
 Observe que a variável não foi inicializada porque o código na linha `e = 5;` ainda não foi executado.  
  
 Você também pode ver os valores de retorno das funções e métodos em determinadas circunstâncias. Consulte [Exibição de valores de retorno de chamadas de método](#bkmk_returnValue) abaixo.  
  
##  <a name="bkmk_returnValue"></a> Exibição de valores de retorno de chamadas de método  
 No código .NET e C\+\+, você pode examinar valores de retorno ao passar sobre ou de uma chamada de método. Essa funcionalidade é útil quando o resultado de uma chamada de método não é armazenado em uma variável local, por exemplo, quando um método é usado como um parâmetro ou valor de retorno de outro método.  
  
 O código c\# a seguir adiciona os valores de retorno das duas funções:  
  
```c#  
static void Main(string[] args) { int a, b, c, d; a = 1; b = 2; c = 3; d = 4; int x = sumVars(a, b) + subtractVars(c, d); } private static int sumVars(int i, int j) { return i + j; } private static int subtractVars(int i, int j) { return j - i; }  
  
```  
  
 Definir um ponto de interrupção na int `x = sumVars(a, b) + subtractVars(c, d);` linha.  
  
 Iniciar a depuração e quando a execução é interrompida no ponto de interrupção primeiro, pressione **F10 \(ignorar\)**. Você verá o seguinte no **Autos** janela:  
  
 ![AutosReturnValueCSharp2](../debugger/media/autosreturnvaluecsharp2.png "AutosReturnValueCSharp2")  
  
## Por que são valores de variáveis, às vezes, vermelho nas janelas variáveis locais e Autos?  
 Você pode perceber que o valor de uma variável, às vezes, é vermelho a **locais** e **Autos** windows. Esses são os valores de variáveis que foram alterados desde a última avaliação. A alteração pode ser de uma sessão de depuração anterior, ou porque o valor foi alterado na janela.  
  
## Alterando o formato numérico de uma janela variável  
 O formato numérico padrão é decimal, mas você pode alterá\-lo em hexadecimal. Clique dentro de um **locais** ou **Autos** window e selecione **exibição Hexadecimal**. A alteração afeta todas as janelas do depurador.  
  
## Editar um valor em uma janela variável  
 Você pode editar os valores da maioria das variáveis que aparecem no **Autos**, **locais**, **inspeção**, e **QuickWatch** windows. Para obter informações sobre **inspeção** e **QuickWatch** windows, consulte [Inspeção e Windows QuickWatch](../debugger/watch-and-quickwatch-windows.md). Clicar duas vezes o valor que você deseja alterar e adicionar o novo o valor.  
  
 Você pode inserir uma expressão para um valor, por exemplo `a + b`. O depurador aceita a expressões de linguagem mais válidas.  
  
 No código C\+\+ nativo, você talvez precise qualificar o contexto de um nome de variável. Para obter mais informações, consulte [Operador de contexto \(C\+\+\)](../debugger/context-operator-cpp.md).  
  
 No entanto, tenha cuidado ao alterar valores. Aqui estão alguns problemas possíveis:  
  
-   Avaliar algumas expressões pode alterar o valor de uma variável ou afetar o estado do programa. Por exemplo, avaliar `var1 = ++var2` altera o valor de `var1` e `var2`.  
  
     Expressões que alteram dados devem ter [efeitos colaterais](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)), que pode produzir resultados inesperados se você não estiver ciente deles. Certifique\-se de que compreender as conseqüências de uma alteração antes de você fazê\-lo.  
  
-   Editar valores de ponto flutuante pode resultar em imprecisões secundárias devido a conversão binário\-decimal de componentes fracionários. Mesmo uma edição aparentemente inofensiva pode resultar em alterações para alguns dos bits menos significativos na variável de ponto flutuante.  
  
## Barra de ferramentas do local de depuração  
 Você pode usar o **local de depuração** barra de ferramentas para selecionar a função desejada, thread ou processo. Defina um ponto de interrupção e iniciar a depuração. \(Se você não vir essa barra de ferramentas, você pode habilitá\-la clicando em uma parte vazia da área da barra de ferramentas. Você deve ver uma lista das barras de ferramentas; Selecione **local de depuração**\). Quando o ponto de interrupção é atingido, a execução pára e você pode ver a barra de ferramentas do local de depuração, que é a linha inferior do gráfico a seguir:  
  
 ![DebugLocationToolbar](../debugger/media/debuglocationtoolbar.png "DebugLocationToolbar")  
  
 Você também pode alterar o contexto para chamadas de função diferentes, threads ou processos clicando duas vezes o elemento de **pilha de chamadas** janela, o **Threads** janela, ou o **processos** janela.  
  
## Consulte também  
 [Janelas do depurador](../debugger/debugger-windows.md)