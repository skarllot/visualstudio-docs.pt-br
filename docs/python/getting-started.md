---
title: "Começar a trabalhar com o Python no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9087b19-275b-4cc1-8d0c-f9c4356c9ce8
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 0b87d25195b8e288252e6c53279897d1edff93bd
ms.lasthandoff: 03/10/2017

---

# <a name="getting-started-with-python-in-visual-studio"></a>Introdução ao Python no Visual Studio

Depois de instalar o Visual Studio com a carga de trabalho do Python (Visual Studio 2017) ou com as Ferramentas Python para Visual Studio (Visual Studio 2015 e anterior), você estará pronto para conhecer a experiência de desenvolvimento do Python.

Neste passo a passo, você cria um novo aplicativo vazio do Python, escolhe um ambiente do Python com o qual trabalhará e, em seguida, começa a escrever o código para ver o IntelliSense em funcionamento. Depois, você trabalhará brevemente com a janela interativa REPL para criar mais códigos, concluirá o programa e o executará por si próprio e no depurador.

> [!Note]
> Este passo a passo examina a experiência do Python no Visual Studio 2017; outras versões serão semelhantes, mas poderão ser diferentes nos detalhes.

## <a name="create-a-new-python-project"></a>Criar um novo projeto do Python

O suporte do Python no Visual Studio inclui diversos [modelos de projeto](python-projects.md) para você começar com diferentes tipos de projetos, incluindo aplicativos Web que usam as estruturas Bottle, Flask e Django, juntamente com os Serviços de Nuvem do Azure. No entanto, para as finalidades deste passo a passo, começaremos com um projeto vazio.

1. No Visual Studio, selecione **Arquivo > Novo Projeto**, que abrirá a caixa de diálogo **Novo Projeto**. Essa é a localização em que é possível procurar e selecionar um modelo e especificar a pasta na qual o projeto será criado.

1. Os modelos do Python podem ser encontrados em **Modelos > Outras Linguagens > Python** à esquerda ou apenas pesquisando “Python”:

    ![Nova caixa de diálogo mostrando os projetos do Python](media/getting-started-new-project.png)

1. Selecione o modelo “Aplicativo Python”, especifique uma pasta para o projeto e selecione **OK**. (Se desejar criar um repositório local para o projeto imediatamente, selecione também a opção **Adicionar ao controle do código-fonte**).

    > [!Tip]
    > O modelo “Com base em um código existente do Python” permite criar rapidamente um projeto do Visual Studio com base em uma pasta que já contém o código do Python, em vez de criar um novo projeto vazio e importar o código existente para ele.

1. Após alguns momentos, você verá o projeto aberto na janela Gerenciador de Soluções do Visual Studio. Nessa janela, é possível procurar os arquivos e as pastas do projeto, bem como gerenciar ambientes.

    ![Gerenciador de Soluções com um projeto do Python](media/getting-started-solution-explorer-1.png)

1. Expanda o nó **Ambientes do Python** e você verá qual interpretador do Python é o padrão atual desse projeto. Se você também expandir o nó desse interpretador, verá uma lista de bibliotecas disponíveis nesse ambiente:

    ![Gerenciador de Soluções mostrando o ambiente do Python](media/getting-started-solution-explorer-2.png)

1. Se você estiver usando o Visual Studio 2015 ou anterior, não terá um interpretador do Python instalado por padrão. Consulte [Selecionando e instalando um interpretador do Python](python-environments.md#selecting-and-installing-python-interpreters) para obter esse processo.

### <a name="going-deeper"></a>Aprofundando-se

- [Projetos do Python no Visual Studio](python-projects.md).
- [Modelos de projeto Web](template-web.md)
- [Modelo de projeto Web Django](template-django.md)
- [Modelo de serviço de nuvem do Azure](template-azure-cloud-service.md)

## <a name="writing-and-running-code"></a>Escrevendo e executando um código

1. Depois de criar um novo projeto do “Aplicativo Python”, um arquivo vazio padrão chamado `PythonApplication1.py` é aberto no editor do Visual Studio. Para renomeá-lo, clique com o botão direito do mouse no arquivo, no Gerenciador de Soluções, selecione **Renomear** e altere o nome para `hello.py`.

1. Comece digitando `print("Hello world")` e observe como o Visual Studio IntelliSense exibe opções de preenchimento automático durante a digitação. A opção contornada na lista suspensa é o preenchimento padrão usado ao pressionar a tecla Tab. Isso pode ser muito útil quando instruções ou identificadores mais longos estão envolvidos.

    ![Pop-up de preenchimento automático do IntelliSense](media/getting-started-coding-1.png)

1. O IntelliSense mostra diferentes informações, dependendo da instrução que está sendo usada, da função que está sendo chamada e assim por diante. Com a função `print`, digitar `(` para fazer a chamada exibe informações de uso completas dessa função e até mesmo coloca em negrito o argumento atual que você precisa fornecer (**valor**, conforme mostrado aqui):

    ![Pop-up de preenchimento automático do IntelliSense em uma função](media/getting-started-coding-2.png)

1. Preencha a instrução para que ela corresponda ao seguinte:

  ```python
  print("Hello world")
  ```

1. Para executar o código, selecione o botão **Iniciar** na barra de ferramentas mostrada abaixo, pressione F5 ou selecione o item de menu **Depurar > Iniciar Depuração**.

    ![Botão Iniciar na barra de ferramentas de depuração](media/getting-started-coding-3.png)

    > [!Note]
    > Se você receber uma mensagem no Visual Studio 2015 ou anterior informando que não há nenhum interpretador, consulte [Selecionando e instalando um interpretador do Python](python-environments.md#selecting-and-installing-python-interpreters), já que nenhum está instalado por padrão.

1. O Visual Studio executará o código usando o ambiente padrão do projeto e mostrará os resultados em uma janela de comando. Pressione uma tecla para fechar essa janela e encerrar a sessão de depuração.

    ![Botão Iniciar na barra de ferramentas de depuração](media/getting-started-coding-4.png)

1. Além de instruções e funções, o IntelliSense fornece preenchimentos para instruções `import`. Isso ajuda você a descobrir com facilidade quais módulos estão disponíveis no ambiente e os membros disponíveis nesse módulo. No editor, exclua a linha `print` e comece a digitar `import`. Você verá uma lista de módulos aparecer:

    ![IntellSense mostrando os módulos disponíveis para uma instrução de importação](media/getting-started-coding-5.png)

1. Preencha a linha digitando ou selecionando `sys`.

1. Na próxima linha, digite `from` para ver uma lista de módulos novamente:

    ![IntellSense mostrando os módulos disponíveis para uma instrução From](media/getting-started-coding-6.png)

1. Selecione ou digite `math` e continue digitando com um espaço e `import`, o que exibe os membros do módulo:

    ![IntellSense mostrando membros do módulo](media/getting-started-coding-7.png)

1. Conclua com a importação dos membros `sin`, `cos` e `radians`, observando os preenchimentos automáticos disponíveis para cada um. Quando terminar, o código deverá ser exibido da seguinte maneira:

  ```python
  import sys  
  from math import sin, cos, radians          
  ```

> [!Tip]
> Os preenchimentos trabalham com subcadeias de caracteres durante a digitação, encontrando a correspondência de partes de palavras, letras no início de palavras e até mesmo caracteres ignorados. Consulte [Editando o código – Preenchimentos](code-editing.md#completions) para obter detalhes.

Na próxima etapa, trabalharemos com a janela interativa REPL escrever um código que podemos testar imediatamente sem executar o depurador.

### <a name="going-deeper"></a>Aprofundando-se

- [Edição de código](code-editing.md)
- [Código de formatação](code-formatting.md)
- [Código de refatoração](code-refactoring.md)
- [Usando o PyLint](code-pylint.md)


## <a name="using-the-interactive-repl-window"></a>Usando uma janela interativa REPL

A janela interativa do Visual Studio para Python oferece uma experiência avançada de leitura-avaliação-impressão-loop, que reduz consideravelmente o ciclo comum de edição-build-depuração. Ela é semelhante à experiência REPL da linha de comando do Python, mas fornece alguns recursos adicionais, como você verá aqui.

1. Abra a janela interativa selecionando **Exibir > Outras Janelas > Janelas Interativas do Python** no menu principal do Visual Studio. A janela é aberta com o prompt comum >>> REPL do Python. Observe que é possível usar o menu suspenso na barra de ferramentas para alterar o ambiente a qualquer momento:

    ![Janela interativa do Python](media/getting-started-interactive-1.png)

1. Insira algumas instruções (como `print("hello")`) e expressões (como `123/567`) para ver resultados imediatos:

    ![Resultados imediatos da janela interativa do Python](media/getting-started-interactive-2.png)

1. Ao começar a escrever uma instrução de várias linhas, como uma definição de função, a janela interativa mostra o prompt … para continuar as linhas, que, ao contrário do REPL de linha de comando, fornece o recuo automático:

    ![Janela interativa do Python com continuação de instrução](media/getting-started-interactive-3.png)

1. A janela interativa fornece um histórico completo de tudo o que foi inserido e é uma melhoria do REPL de linha de comando com itens de histórico de várias linhas. Por exemplo, com facilidade, é possível cancelar toda a definição da função `f` acima como uma única unidade e alterar o nome para `make_double`, em vez de recriar a função linha por linha.

1. Outro recurso muito útil é a capacidade de enviar rapidamente várias linhas de código de uma janela do editor para a janela interativa, na qual é possível trabalhar com o código no ágil ambiente REPL, em vez de escrever outro código para ser executado no depurador. Para ver isso, comece adicionando o seguinte código ao arquivo hello.py que está aberto no editor:

  ```python
  def make_dot_string(x):  
      return ' ' * int(10 * cos(radians(x)) + 10) + 'o'
  ```

1. Selecione todo o código em hello.py (incluindo as instruções `import`), clique com o botão direito do mouse e selecione **Enviar para Interativa** (Ctrl+Enter). O código é imediatamente colado na janela interativa e executado. Como o código define uma função, é possível testar essa função rapidamente chamando-a algumas vezes:

    ![Enviando o código para a janela interativa](media/getting-started-interactive-4.png)

1. O comando **Enviar para Interativa** permite colar várias linhas de código (como algo encontrado na Internet) na janela interativa de forma eficaz, o que não pode ser feito diretamente. Por exemplo, copie o código abaixo e tente colar (Ctrl+V) na janela interativa e você verá que nada acontece. Porém, é possível colá-lo no editor, selecioná-lo e usar o comando **Enviar para Interativa** para vê-lo ser executado.

  ```python
  for i in range(360):
      s = make_dot_string(i)  
      print(s) 
  ```

    ![Colando várias linhas de código usando o comando Enviar para Interativa](media/getting-started-interactive-5.png)

1. Como a definição de função está novamente no histórico do REPL como uma única unidade, é fácil voltar e fazer as alterações desejadas e, em seguida, testar a função novamente.

1. Quando estiver satisfeito com o código escrito, é possível selecioná-lo na janela interativa, clicar com o botão direito do mouse, selecionar **Copiar Código** e colá-lo no editor. O recurso especial do comando **Copiar Código** é que ele omite automaticamente qualquer saída, bem como o texto de prompt >>> e ... Por exemplo, ao usar o comando com a seleção mostrada abaixo:

  ![Comando Copiar Código da janela interativa](media/getting-started-interactive-6.png)

  somente o seguinte será colado:

  ```python
  make_dot_string(180)
  make_dot_string(135)
  for i in range(360):
      s = make_dot_string(i)  
      print(s) 
  ```

1. Por fim, a janela interativa fornece uma série de metacomandos que permitem carregar arquivos, redefinir o ambiente sem perder o histórico e inserir comentários durante o processo. Consulte [Janelas Interativas – metacomandos](interactive-repl.md#meta-commands) para obter detalhes.

### <a name="going-deeper"></a>Aprofundando-se

- [Usando a Janela interativa](interactive-repl.md)
- [Usando o IPython REPL](interactive-repl-ipython.md)

## <a name="running-code-in-the-debugger"></a>Executando o código no depurador

Além de gerenciar projetos, fornecer uma experiência avançada de edição e a janela interativa, o Visual Studio fornece seu suporte completo de depuração para o código do Python.

1. Edite o código no arquivo hello.py para que ele corresponda ao seguinte:

  ```python  
  from math import sin, cos, radians  
  import sys  
    
  def make_dot_string(x):  
      return ' ' * int(10 * cos(radians(x)) + 10) + 'o'  
    
  def main():  
      for i in range(360 * 5):
          s = make_dot_string(i)  
          print(s)  
            
  main()
  ```  

1. Verifique se o código funciona corretamente selecionando **Iniciar** na barra de ferramentas, pressionando F5 ou selecionando o comando de menu **Depurar > Iniciar Depuração**. Isso executa o código no depurador, mas como não temos nenhum ponto de interrupção definido, você simplesmente o verá imprimindo um padrão de onda para algumas iterações. Pressionar qualquer tecla fechará a janela de saída neste ponto.

    > [!Tip]
    > Para fechar a janela de saída automaticamente quando o programa for concluído, substitua a chamada `main()` pelo seguinte código:
    >
    > ```python    
    > if __name__ == "__main__":  
    >     sys.exit(int(main() or 0))      
    > ```

1. Defina um ponto de interrupção na primeira linha da função `main` clicando na margem esquerda cinza próxima a essa linha ou colocando o cursor na linha e usando o comando *Depurar > Ativar/Desativar Ponto de Interrupção** (F9). Um ponto vermelho será exibido na margem cinza para indicar o ponto de interrupção (conforme indicado pela seta azul abaixo):

    ![Configurando um ponto de interrupção](media/getting-started-debugging-1.png)

1. Inicie o depurador novamente e você verá que a execução do código é interrompida na linha com o ponto de interrupção. Aqui é possível ver a pilha de chamadas e examinar as variáveis locais na janela Locais:

    ![Experiência de interface do usuário do ponto de interrupção para o Python](media/getting-started-debugging-2.png)

1. Execute algumas iterações do loop `for` em etapas, linha por linha, usando F10, o comando **Depurar > Executar em Etapas** ou o botão de barra de ferramentas Executar em Etapas. Isso significa que o depurador executará cada chamada a `make_dot_string`, mas não interromperá dentro dessa função (a menos que você defina um ponto de interrupção).

1. Na barra de ferramentas, os três botões de execução em etapas mostrados abaixo são, da esquerda para a direita: Intervir, Depuração Parcial e Depuração Circular:

    ![Botões da barra de ferramentas de execução em etapas](media/getting-started-debugging-3.png)

1. Intervenha em `make_dot_string` agora usando o comando Intervir (F11). Você verá que intervirá do loop `for` nessa função. Uma nova execução em etapas retornará para o loop `for`, mas se houver linhas adicionais na função, você deverá executá-las em etapas individualmente. Se você estiver em uma função e desejar executar o restante de suas linhas e retornar ao código de chamada, use Depuração Circular (Shift+F11).

1. Para continuar executando o código até chegar ao próximo ponto de interrupção (ou até que o programa seja encerrado), pressione F5 novamente ou selecione o botão de barra de ferramentas **Continuar** ou **Depurar > Continuar**. Como há um ponto de interrupção no loop `for`, você interromperá na próxima iteração.

1. A execução em etapas de centenas de iterações de um loop pode ser entediante e, portanto, é possível adicionar uma condição ao ponto de interrupção definido anteriormente para que ele seja interrompido somente quando o valor `i` exceder determinado valor, digamos 1600. Para fazer isso, clique com o botão direito do mouse no ponto vermelho do ponto de interrupção e selecione **Condição...**. Na janela Configurações do Ponto de Interrupção exibida, insira `i > 1600` como a expressão e selecione **Fechar**. Agora pressione F5 para continuar e você verá o programa ser executado por alguns instantes antes de ser interrompido novamente. 

    ![Configurando uma condição de ponto de interrupção](media/getting-started-debugging-4.png)

1. Para concluir o programa, é possível ativar/desativar o ponto de interrupção novamente e pressionar F5. O Visual Studio retorna para o modo de edição quando a depuração é concluída.

### <a name="going-deeper"></a>Aprofundando-se

- [Depuração](debugging.md).
- Consulte também [Depuração no Visual Studio](../debugger/debugging-in-visual-studio.md) para obter a documentação completa dos recursos de depuração do Visual Studio.

## <a name="next-steps"></a>Próximas etapas

Além dos links em “Aprofunde-se” fornecidos anteriormente, os seguintes tópicos abordam recursos adicionais da experiência do Python no Visual Studio:

- Para ver como o Visual Studio se conecta a um Serviço de Aplicativo do Azure, consulte [Publicando um aplicativo Web do Python no Azure](publishing-to-azure.md)
- Para aprender a gerenciar diferentes ambientes globalmente e em projetos individuais, incluindo ambientes virtuais, consulte [Ambientes do Python](python-environments.md).
- O Visual Studio fornece a capacidade de depurar o aplicativo em servidores remotos, conforme explicado em [Depuração remota de plataforma cruzada](debugging-cross-platform-remote.md) e [Depuração remota do Azure](debugging-azure-remote.md).
- É possível avaliar o desempenho do código do Python usando a [Criação de Perfil do Visual Studio](profiling.md).
- Os testes de unidade escritos no Python integram diretamente com o Gerenciador de Testes do Visual Studio, conforme discutido em [Testes de unidade](unit-testing.md).

