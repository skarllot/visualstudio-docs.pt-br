---
title: "Testes de unidade de aplicativos do C++ existentes com Gerenciador de Testes | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7d08de69-c32e-4f0b-89aa-75347b15fb82
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "mlearned"
manager: "douge"
---
# Testes de unidade de aplicativos do C++ existentes com Gerenciador de Testes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

É recomendável que, antes de alterar um aplicativo existente, você certifique\-se de que ele tenha uma boa cobertura com testes de unidade.  Isso permite que as alterações não introduziu bugs de confiança.  Se o aplicativo ainda não tiver testes de unidade, você pode adicioná\-los usando as técnicas demonstradas neste tópico.  Este tópico descreve como adicionar testes de unidade para código existente do Visual C\+\+, começando a decisão de como testar seu código e, em seguida, criar, gravar e por fim, executando os testes.  
  
## Decidir como testar seu código  
 Abra o projeto C\+\+ existente e inspecioná\-la para decidir como deseja adicionar os testes de unidade.  Você talvez queira usar algumas ferramentas de modelagem que ajudam você a ver dependências no código e ajudá\-lo a entender como as partes interagem.  Para obter mais informações, consulte [Visualizar código](../modeling/visualize-code.md).  
  
 É recomendável que você separe suas alterações em pequenas tarefas.  Antes de cada alteração pequena, escrever testes de unidade para aspectos do comportamento permanecerá o mesmo.  Esses testes continuará depois que a alteração foi feita.  Por exemplo, se você pretende alterar uma função de classificação para que ele classifica uma lista de pessoas por sobrenome, em vez de por nome, você pode escrever um teste de unidade que verifica se todos os nomes de entrada são exibidos na saída.  Depois de ter feito a alteração, talvez queira adicionar novos testes de unidade para o novo comportamento.  
  
 Se for prático, vários ou todos os seus testes de unidade devem usar apenas as funções que são exportadas.  Mas se você estiver alterando apenas uma pequena parte de todo o aplicativo, em seguida, você pode usar funções que não são exportadas.  Por exemplo, convém testes que chamam funções internas ou testes que definir e obtém os valores das variáveis internas.  
  
 Há várias maneiras de testar o código do produto, dependendo se ele expõe as interfaces que você deseja testar.  Escolha uma das seguintes maneiras:  
  
 **Os testes de unidade usará somente funções que são exportadas a partir de código sob teste:**  
 Adicione um projeto de teste separada.  No projeto de teste, adicione uma referência ao projeto sob teste.  
  
 Vá para o procedimento [para fazer referência a funções exportadas do projeto de teste](#projectRef).  
  
 **O código em teste é criado como um arquivo .exe:**  
 Adicione um projeto de teste separada.  Vincule\-o ao arquivo de objeto de saída.  
  
 Vá para o procedimento [para vincular os testes para os arquivos de objeto ou biblioteca](#objectRef).  
  
 **Os testes de unidade devem usar dados e funções privadas, e o código em teste pode ser criado como uma biblioteca estática:**  
 Altere o projeto sob teste para que ele seja compilado em um arquivo. lib.  Adicione um projeto de teste separado que referencia o projeto sob teste.  
  
 Essa abordagem tem a vantagem de permitir que seus testes usar membros privados, mas ainda manter os testes em um projeto separado.  No entanto, talvez não seja adequado para alguns aplicativos em que você deve ter uma biblioteca de vínculo dinâmico \(. dll\).  
  
 Vá para o procedimento [para alterar o código em teste para uma biblioteca estática](#staticLink).  
  
 **Os testes de unidade devem usar dados e funções privadas, e o código deve ser criado como uma biblioteca de vínculo dinâmico \(DLL\):**  
 Adicione testes de unidade no mesmo projeto como o código do produto.  
  
 Vá para o procedimento [adicionar testes de unidade no mesmo projeto](#sameProject).  
  
## Criar testes  
  
###  <a name="staticLink"></a> Para alterar o código em teste para uma biblioteca estática  
  
-   Se os testes devem usar membros que não são exportados por um projeto de teste, e o projeto sob teste é criado como uma biblioteca dinâmica, considere a possibilidade de convertê\-la em uma biblioteca estática.  
  
    1.  No Solution Explorer, no menu de atalho do projeto sob teste, escolha **propriedades**.  Abre a janela de propriedades do projeto.  
  
    2.  Escolha **Propriedades de configuração**, **geral**.  
  
    3.  Definir **tipo de configuração** para **biblioteca estática \(. lib\)**.  
  
 Continue com o procedimento [para vincular os testes para os arquivos de objeto ou biblioteca](#objectRef).  
  
###  <a name="projectRef"></a> Para fazer referência a funções exportadas do projeto de teste  
  
-   Se um projeto sob teste exporta as funções que você deseja testar, você pode adicionar uma referência ao projeto de código do projeto de teste.  
  
    1.  Crie um projeto de teste do C\+\+.  
  
        1.  No **arquivo** menu, escolha **novo**, **projeto**, **Visual C\+\+, teste**, **o projeto de teste de unidade C\+\+**.  
  
    2.  No Solution Explorer, no menu de atalho do projeto de teste, escolha **referências**.  Abre a janela de propriedades do projeto.  
  
    3.  Selecione **Propriedades comuns**, **estrutura e referências**, e, em seguida, escolha o **Adicionar nova referência** botão.  
  
    4.  Selecione **projetos**, e, em seguida, o projeto a ser testado.  
  
         Escolha o botão **Adicionar**.  
  
    5.  Nas propriedades do projeto de teste, adicione o local do projeto sob teste para os diretórios de inclusão.  
  
         Escolha **Propriedades de configuração**, **diretórios VC \+ \+**, **diretórios de inclusão**.  
  
         Escolha **Editar**, e em seguida, adicione o diretório de cabeçalho do projeto sob teste.  
  
 Vá para [escrever testes de unidade](#addTests).  
  
###  <a name="objectRef"></a> Para vincular os testes para os arquivos de objeto ou da biblioteca  
  
-   Se o código sob teste não exporta as funções que você deseja testar, você pode adicionar a saída **.obj** ou **.lib** arquivo para as dependências do projeto de teste.  
  
    1.  Crie um projeto de teste do C\+\+.  
  
        1.  No **arquivo** menu, escolha **novo**, **projeto**, **Visual C\+\+, teste**, **o projeto de teste de unidade C\+\+**.  
  
    2.  No Solution Explorer, no menu de atalho do projeto de teste, escolha **propriedades**.  Abre a janela de propriedades do projeto.  
  
    3.  Escolha **Propriedades de configuração**, **vinculador**, **entrada**, **dependências adicionais**.  
  
         Escolha **Editar**, e adicione os nomes da **.obj** ou **.lib** arquivos.  Não use os nomes de caminho completo.  
  
    4.  Escolha **Propriedades de configuração**, **vinculador**, **geral**, **diretórios de bibliotecas adicionais**.  
  
         Escolha **Editar**, e adicione o caminho do diretório de **.obj** ou **.lib** arquivos.  O caminho é geralmente dentro da pasta de compilação do projeto sob teste.  
  
    5.  Escolha **Propriedades de configuração**, **diretórios VC \+ \+**, **diretórios de inclusão**.  
  
         Escolha **Editar**, e em seguida, adicione o diretório de cabeçalho do projeto sob teste.  
  
 Vá para [escrever testes de unidade](#addTests).  
  
###  <a name="sameProject"></a> Para adicionar testes de unidade no mesmo projeto  
  
1.  Modificar as propriedades do projeto do código de produto para incluir os cabeçalhos e os arquivos de biblioteca que são necessários para o teste de unidade.  
  
    1.  No Solution Explorer, no menu de atalho do projeto sob teste, escolha Propriedades.  Abre a janela de propriedades do projeto.  
  
    2.  Escolha **Propriedades de configuração**, **diretórios VC \+ \+**.  
  
    3.  Edite os diretórios de inclusão e biblioteca:  
  
        |||  
        |-|-|  
        |**Diretórios de Inclusão**|**$\(VCInstallDir\)UnitTest\\include;$\(IncludePath\)**|  
        |**Diretórios de Biblioteca**|**$\(VCInstallDir\)UnitTest\\lib;$\(LibraryPath\)**|  
  
2.  Adicione um arquivo de teste de unidade C\+\+:  
  
    -   No Solution Explorer, no menu de atalho do projeto, escolha **Add**, **Novo Item**, e, em seguida, escolha **o teste de unidade C\+\+**.  
  
 Vá para [escrever testes de unidade](#addTests).  
  
##  <a name="addTests"></a> Escrever testes de unidade  
  
1.  Em cada arquivo de código de teste de unidade, adicione uma `#include` instrução para os cabeçalhos do projeto sob teste.  
  
2.  Adicione métodos e classes de teste para os arquivos de código de teste de unidade.  Por exemplo:  
  
    ```cpp  
    #include "stdafx.h"  
    #include "CppUnitTest.h"  
    #include "MyProjectUnderTest.h"  
    using namespace Microsoft::VisualStudio::CppUnitTestFramework;  
    namespace MyTest  
    {  
      TEST_CLASS(MyTests)  
      {  
      public:  
          TEST_METHOD(MyTestMethod)  
          {  
              Assert::AreEqual(MyProject::Multiply(2,3), 6);  
          }  
      };  
    }  
    ```  
  
 Para obter mais informações, consulte [Unit testing native code with Test Explorer](http://msdn.microsoft.com/pt-br/8a09d6d8-3613-49d8-9ffe-11375ac4736c).  
  
## Executar testes  
  
1.  Sobre o **exibição** menu, escolha **outras janelas**, **Gerenciador de testes**.  
  
2.  No Gerenciador de Testes, escolha **Executar Tudo**.  
  
 Para obter mais informações, consulte [Início rápido: desenvolvimento baseado em testes com o Gerenciador de Testes](../test/quick-start-test-driven-development-with-test-explorer.md).