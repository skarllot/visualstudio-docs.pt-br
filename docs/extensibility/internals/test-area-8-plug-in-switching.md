---
title: "Teste área 8: Alternância de plug-in | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 806a334b551a56a9244fc58cc2a4bad4ab3d7fb2
ms.lasthandoff: 02/22/2017

---
# <a name="test-area-8-plug-in-switching"></a>Teste área 8: Alternância de plug-in
O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) tem a interface do usuário (UI) para alterar o plug-in de controle de origem atual. Essa área de teste fornece casos de teste para o processo de pegar o plug-in para usar a solução para controle de origem.  
  
## <a name="command-menu-access"></a>Acesso ao Menu comando  
 O seguinte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] caminhos de menu do ambiente de desenvolvimento integrado são usados nos casos de teste.  
  
-   Controle de origem atual plug-in: **ferramentas** -> **opções** -> **controle de origem** -> **plug-in Selection**.  
  
-   Alterar origem ligação de controle: **arquivo** -> **controle de origem** -> **Change Source Control**...  
  
## <a name="common-expected-behavior"></a>Comportamento esperado comuns  
 É possível alterar o plug-in de uma solução de controle de origem sem sair do Visual Studio ou o recarregamento da solução. Além disso, o plug-in de controle de origem atual muda automaticamente para aquele usado por uma solução quando essa solução é carregada.  
  
## <a name="test-cases"></a>Casos de teste  
 Estes são os casos de teste específicos para a área plug-in de teste de comutação.  
  
### <a name="case-8a-automatic-change"></a>Caso 8a: alterações automáticas  
  
#### <a name="expected-behavior"></a>Comportamento esperado  
 Quando um usuário carrega uma solução sob controle de origem, a solução é carregada automaticamente e o plug-in de controle de origem apropriada é selecionada como atual.  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Alteração de plug-in de controle de origem automática|1.  Selecione plug-in em teste atuais (**ferramentas** -> **opções** -> **controle de origem** -> **plug-in Selection**.)<br />2.  Crie um novo projeto.<br />3.  Adicione a solução ao controle de origem.<br />4.  Selecione outro plug-in (por exemplo, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />5.  Aceite solicitação de solução de descarregamento.<br />6.  Reabra a solução no disco.|Solução for aberta.<br /><br /> Plug-in em teste é o plug-in de controle de origem atual.|  
  
### <a name="case-8b-solution-based-change"></a>Caso 8b: alteração de solução  
  
#### <a name="expected-behavior"></a>Comportamento esperado  
 A solução pode ter seu plug-in de controle de origem associado alterado.  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Alteração do plug-in para uma solução|1.  Selecione plug-in em teste atuais (**ferramentas** -> **opções** -> **controle de origem** -> **plug-in Selection**).<br />2.  Crie um novo projeto e solução.<br />3.  Adicione a solução ao controle de origem.<br />4.  Desacoplar a solução do controle de origem (usando o **Change Source Control** caixa de diálogo).<br />5.  Selecione outro plug-in (por exemplo, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />6.  Recarregue a solução do disco se descarregado.<br />7.  Adicione a solução ao controle de origem.<br />8.  Desacoplar a solução do controle de origem (usando **Change Source Control** caixa de diálogo).<br />9. Selecione plug-in em teste novamente.<br />10. Recarregue a solução a partir do disco se descarregado.<br />11. Vincular a solução no local original (usando o **Change Source Control** caixa de diálogo).|Solução é adicionada ao controle de origem usando selecionado plug-in.|  
  
## <a name="see-also"></a>Consulte também  
 [Guia de teste para Plug-ins de controle de origem](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
