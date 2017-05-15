---
title: "Depuração usando o Visualizador de armazenamento | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 17
author: alancameronwills
ms.author: awills
manager: douge
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d39421df38cf47657c445822dd19b25ed2ea5ea2
ms.contentlocale: pt-br
ms.lasthandoff: 02/22/2017

---
# <a name="debugging-by-using-the-store-viewer"></a>Depurando por meio do Visualizador de Repositório
Com o Visualizador de armazenar, você pode examinar o estado de um *armazenar* usado pelo [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. O Visualizador de armazenar exibe todos os elementos de modelo de domínio que estão em uma loja específica, juntamente com propriedades de elemento e os links entre elementos.  
  
## <a name="opening-store-viewer"></a>Visualizador de repositório de abertura  
 Quando você está no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] experimentais de compilação, interrompa seu código em um ponto de interrupção em que uma instância do armazenamento contém informações sobre o modelo. Em seguida, abra o Visualizador de repositório, digitando o seguinte comando no **imediato** janela:  
  
```  
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);  
```  
  
> [!NOTE]
>  Você deve substituir `mystore` com o nome da sua instância de armazenamento. Além disso, se você adicionar o namespace ao seu código, você pode digitar o comando para exibir o Visualizador de armazenamento sem o namespace totalmente qualificado:  
>   
>  `using Microsoft.VisualStudio.Modeling.Diagnostics;`  
>   
>  `...`  
>   
>  `StoreViewer.Show(mystore);`  
  
 O `Show` método tem várias sobrecargas. Você pode especificar uma instância de uma loja ou uma partição como o parâmetro.  
  
 Como alternativa, você pode colocar a linha de código que mostra o Visualizador de repositório em qualquer lugar no seu código onde o parâmetro passado para o `Show` método está no escopo. Essa ação exibe o visualizador armazenar quando a linha de código é executado como um instantâneo do conteúdo do repositório.  
  
### <a name="using-store-viewer"></a>Usando o Visualizador de armazenamento  
 Quando abre o Visualizador de repositório, uma janela não restrita do Windows Forms é exibida, como mostra a ilustração a seguir.  
  
 ![](../modeling/media/storeviewer2.png "storeviewer2")  
Visualizador de Repositório  
  
 O Visualizador de repositório possui três painéis: o painel esquerdo, o painel superior direito e o painel inferior direito. O painel esquerdo é uma exibição de árvore dos tipos de `DomainDataDirectory` membro de um repositório. Se você expandir o nó da partição e clique em um elemento, as propriedades aparecem no painel superior direito. Se o elemento é vinculado a outros elementos, os elementos adicionais aparecem no painel inferior direito. Se você clicar duas vezes um elemento no painel inferior direito, o elemento é realçado no painel esquerdo.  
  
## <a name="see-also"></a>Consulte também  
 [Navegando por um modelo no código do programa e atualizando-o](../modeling/navigating-and-updating-a-model-in-program-code.md)
