---
title: "Estado gr&#225;fico | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.graphics.statewindow"
ms.assetid: 97e7757e-c372-4626-8149-99a81367a0e1
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Estado gr&#225;fico
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A janela de estado no diagnóstico de gráficos do Visual Studio o ajuda a entender o estado de elementos gráficos está ativo no momento do evento atual, como uma chamada de desenho.  
  
## Noções básicas sobre a janela de estado  
 A janela de estado juntos coleta o estado que afeta o processamento e a apresenta hierarquicamente, em um único lugar.  Dependendo da versão do Direct3D seu aplicativo usa, as informações apresentadas na janela de estado podem ter diferenças.  
  
### Exibições de estado  
 Você pode exibir a tabela de estado de várias maneiras diferentes:  
  
|Exibir|Descrição|  
|------------|---------------|  
|Exibição de estado de entrada de API|Essa exibição apresenta o estado em um layout semelhante aos objetos Direct3D que compõem o estado.|  
|Modo de exibição lógico de estado de entrada|Essa exibição apresenta o estado em uma exibição lógica que não reflita o layout dos objetos Direct3D que compõem o estado.|  
|Exibição de estado de fixado|Em vez de uma hierarquia, o modo de exibição de estado fixos apresenta estado fixos itens em uma lista simples com nomes totalmente qualificados.  Essa exibição faz é possível exibir muitos itens de estado de diferentes pacotes de estado em um pequeno número de linhas.|  
  
##### Para alterar a exibição de estado  
  
-   Na janela do estado, no canto superior esquerdo logo abaixo do título, escolha o botão que corresponde ao estilo de exibição de estado que deseja usar.  
  
    -   **Mostrar exibição do estado de recebimento de API**  
  
    -   **Mostrar exibição de estado lógico**  
  
    -   **Mostrar exibição de estado fixos**  
  
> [!IMPORTANT]
>  Deve fixar o estado no **API mostrar o estado de entrada** ou **estado lógico Mostrar** modos de exibição para que ela seja exibida no **fixado Mostrar modo de exibição de estado**.  
  
### Formato de tabela de estado  
 A janela de estado apresenta várias colunas de informações.  
  
|Coluna|Descrição|  
|------------|---------------|  
|Nome|O nome do item de estado.  Se este item representa um pacote do estado, o item pode ser expandido para exibi\-la.<br /><br /> No **exibição de estado de entrada da API** e **exibição de estado lógico** afirma, nomes são recuados para mostrar a relação hierárquica entre estados.<br /><br /> No **fixado exibição de estado** estado, nomes totalmente qualificados são exibidos em uma lista plana.|  
|Valor|O valor do item de estado.|  
|Tipo|O tipo do item de estado.|  
  
### Estado alterado  
 Estado de elementos gráficos geralmente altera incrementalmente entre chamadas de desenho subseqüentes e vários tipos de problemas de renderização são causados quando o estado é alterado de forma incorreta.  Para ajudá\-lo a localizar qual estado foi alterado desde que a chamada de desenho anterior, estado foi alterado é marcado com um asterisco e exibido em vermelho, isso se aplica não apenas o estado em si, mas seu item de estado do pai, para que você pode identificar facilmente o estado alterado no nível mais alto e, em seguida, drill\-down até os detalhes.  
  
### Fixação de estado  
 Como muitos aplicativos processam objetos semelhantes em sequência, alterar um conjunto conhecido de estado, às vezes é útil fixar os estados de alteração no local para que você pode observar como eles mudam ao mudar de chamada de desenho para desenhar a chamada.  
  
 Isso também pode ser útil se você isola a origem do problema seja devido a uma alteração em um estado específico.  
  
##### Para fixar o estado em vigor  
  
1.  Na janela do estado, localize o estado que você está interessado.  Talvez seja necessário expandir o estado de nível superior para localizar os detalhes que você está interessado.  
  
2.  Posicione o cursor sobre o estado que você está interessado.  Um ícone de pino aparece à esquerda do item de estado.  
  
3.  Escolha o ícone de pino para fixar o item de estado em vigor.