---
title: "Pr&#225;ticas recomendadas para testes de IU codificados | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "testes de IU codificados, práticas recomendadas"
ms.assetid: d5aef766-a24c-4f1f-ac9b-e5462b6627d4
caps.latest.revision: 39
caps.handback.revision: 39
ms.author: "mlearned"
manager: "douge"
---
# Pr&#225;ticas recomendadas para testes de IU codificados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico descreve as práticas recomendadas a seguir ao desenvolver testes de UI codificados.  
  
 **Requisitos**  
  
-   O Visual Studio Enterprise  
  
## Práticas recomendadas  
 Use as diretrizes a seguir para criar um teste de IU codificado flexível.  
  
-   Use o **Coded UI Test Builder** sempre que possível.  
  
-   Não modifique o `UIMap.designer.cs` arquivo diretamente.  Se você fizer isso, as alterações para o arquivo serão substituídas.  
  
-   Crie seu teste como uma sequência de métodos gravados.  Para obter mais informações sobre como registrar um método, consulte [Criando testes de UI codificados](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
-   Cada método gravado deve agir em uma única página, um formulário ou uma caixa de diálogo.  Crie um novo método de teste para cada nova página, um formulário ou uma caixa de diálogo.  
  
-   Quando você cria um método, use um nome de método significativo em vez do nome padrão.  Um nome significativo ajuda a identificar a finalidade do método.  
  
-   Quando possível, limite cada método gravado para ações de menos de 10.  Essa abordagem modular torna mais fácil substituir um método se altera a interface do usuário.  
  
-   Criar cada declaração usando o **Coded UI Test Builder**, que adiciona automaticamente um método de asserção para o `UIMap.Designer.cs` arquivo.  
  
-   Se a interface do usuário \(IU\) for alterada, registrar novamente os métodos de teste ou os métodos de asserção ou regravar seções afetadas de um método de teste existente.  
  
-   Criar um separado <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> arquivo para cada módulo no seu aplicativo em teste.  Para obter mais informações, consulte [Testando um aplicativo grande com vários mapas de interface do usuário](../test/testing-a-large-application-with-multiple-ui-maps.md).  
  
-   No aplicativo de teste, use nomes significativos quando você criar os controles de interface do usuário.  Isso dá mais significado e a facilidade de uso para os nomes de controle gerado automaticamente.  
  
-   Se você estiver criando asserções codificando com a API, crie um método para cada declaração na parte de <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> classe que está na `UIMap.cs` arquivo.  Chame esse método do seu método de teste para executar a asserção.  
  
-   Se você estiver codificando diretamente com a API, use as propriedades e métodos nas classes geradas no `UIMap.Designer.cs` tanto quanto possível do arquivo em seu código.  Essas classes tornará seu trabalho mais fácil e mais confiável e ajudarão você a ser mais produtivo.  
  
 Testes de UI codificados adaptar\-se automaticamente a muitas alterações na interface do usuário.  Se, por exemplo, um elemento de interface do usuário foi alterado de posição ou cor, na maioria das vezes o teste de IU codificado ainda os encontre o elemento correto.  
  
 Durante uma execução de teste, os controles de interface do usuário estão localizados pela estrutura de teste usando um conjunto de propriedades de pesquisa que são aplicadas a cada classe de controle nas definições criado pelo **Construtor de teste de IU codificado** no `UIMap.Designer.cs` arquivo.  As propriedades de pesquisa contém pares nome\-valor da propriedade nomes e valores de propriedade que podem ser usados para identificar o controle, como o <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A>, e <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> Propriedades do controle.  Se as propriedades de pesquisa são as mesmas, teste de IU codificado encontrará com êxito o controle na interface do usuário.  Se as propriedades de pesquisa forem alteradas, testes de UI codificados tem um algoritmo de correspondência inteligente que se aplica a heurística para localizar controles e do windows na interface do usuário.  Quando a interface do usuário é alterada, você poderá modificar as propriedades de pesquisa de elementos identificados anteriormente para certificar\-se de que eles estão localizados.  
  
## O que fazer se a interface do usuário for alterado  
 Interfaces de usuário alterar com freqüência durante o desenvolvimento.  Aqui estão algumas maneiras de reduzir o efeito dessas alterações:  
  
-   Localize o método gravado que faz referência a esse controle e use o **Coded UI Test Builder** para registrar as ações para esse método.  Você pode usar o mesmo nome do método para substituir as ações existentes.  
  
-   Se um controle tiver uma declaração que não é mais válida:  
  
    -   Exclua o método que contém a declaração.  
  
    -   Remova a chamada para esse método de método de teste.  
  
    -   Adicionar uma nova declaração arrastando o botão de fios para o controle da interface do usuário, abra o mapa de interface do usuário e adicionar a nova declaração.  
  
 Para obter mais informações sobre como gravar testes de IU codificados, consulte [Usar automação de interface do usuário para testar código](../test/use-ui-automation-to-test-your-code.md).  
  
## O que fazer se um processo em segundo plano precisa concluir antes de continuar o teste  
 Talvez seja necessário aguardar até que um processo seja concluído antes de continuar com a próxima ação de interface do usuário.  Para fazer isso, você pode usar <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> deve aguardar antes do teste continua como no exemplo a seguir.  
  
```  
// Set the playback to wait for all threads to finish  
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;  
  
// Press the submit button  
this.UIMap.ClickSubmit();  
  
// Reset the playback to wait only for the UI thread to finish  
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;  
```  
  
## Consulte também  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting>   
 [Usar automação de interface do usuário para testar código](../test/use-ui-automation-to-test-your-code.md)   
 [Criando testes de UI codificados](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Testando um aplicativo grande com vários mapas de interface do usuário](../test/testing-a-large-application-with-multiple-ui-maps.md)   
 [Configurações e plataformas compatíveis para testes de IU codificados e gravações de ações](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)