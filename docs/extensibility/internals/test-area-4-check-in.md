---
title: "Área de teste 4: Fazer Check-In | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
caps.latest.revision: 11
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
ms.openlocfilehash: 72f3d93e573ae08d3ff20b6ad158fb88bc44faf4
ms.lasthandoff: 02/22/2017

---
# <a name="test-area-4-check-in"></a>Área de teste 4: Fazer Check-In
Essa área de plug-in de teste de controle de origem aborda a enviar itens atualizados para o armazenamento de versão por meio de **Check-In** comando.  
  
## <a name="command-menu-access"></a>Acesso ao Menu comando  
 O seguinte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] caminhos de menu do ambiente de desenvolvimento integrado são usados nos casos de teste.  
  
##### <a name="check-in"></a>Fazer Check-in:  
 **Arquivo**, **controle de origem**, **Check-In**.  
  
 **File**, **Check In**.  
  
 Menu de atalho, **Check-In**.  
  
## <a name="common-expected-behavior"></a>Comportamento esperado comuns  
  
-   Projetos e arquivos adicionados a uma solução ou projeto sob controle de origem são exibidos no **Check-In** caixa de diálogo e o **check-ins pendentes** janela.  
  
-   Após o check-in, os itens adicionados aparecem no controle de origem.  
  
-   Após o check-in, itens atualizados são corretamente com controle de versão no repositório.  
  
## <a name="test-cases"></a>Casos de teste  
 Estes são os casos de teste específicos para a área de teste de check-in.  
  
### <a name="case-4a-modified-items"></a>Caso 4a: modificou itens  
 Descreve como usar a verificação em ação para atualizar um arquivo sob controle de origem que foi modificada.  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Modificar um arquivo de texto que foi feito check-out, check-in de arquivos somente (**Check-In** caixa de diálogo)|1.  Crie um novo projeto com um arquivo de texto.<br />2.  Adicione a solução ao controle de origem.<br />3.  Check-out e modificar o arquivo de texto.<br />4.  Check-in por meio da caixa de diálogo Check-In (**arquivo**, **controle de origem**, **Check-In**).|Comportamento esperado comuns.|  
|Modificar um arquivo de texto que foi feito check-out, Check-in de arquivos somente (**check-ins pendentes** janela)|1.  Crie um novo projeto com um arquivo de texto.<br />2.  Adicione a solução ao controle de origem.<br />3.  Check-out e modificar o arquivo de texto.<br />4.  Check-in por meio de **check-ins pendentes** janela.|Comportamento esperado comuns.|  
  
### <a name="case-4b-adding-files"></a>Caso 4b: adicionando arquivos  
 Ao adicionar um arquivo a um projeto ou um item a uma solução, o projeto ou solução deve alterar também. Assim, o arquivo pai também fez check-out e deve fazer check-in para concluir a adição.  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Adicionar um arquivo de texto e fazer check-in tudo (**Check-In** caixa de diálogo)|1.  Crie um novo projeto.<br />2.  Adicione a solução ao controle de origem.<br />3.  Adicione um arquivo de texto para o projeto.<br />4.  Aceite o check-out do projeto se solicitado.<br />5.  Selecione a solução em **Solution Explorer**.<br />6.  Check-in do **Check-In** caixa de diálogo.|Comportamento esperado comuns.|  
|Adicionar um arquivo de texto e fazer check-in tudo (**check-ins pendentes** janela)|1.  Crie um novo projeto.<br />2.  Adicione a solução ao controle de origem.<br />3.  Adicione um arquivo de texto para o projeto.<br />4.  Aceite o check-out do projeto se solicitado.<br />5.  Check-in de solução de **check-ins pendentes** janela.|Comportamento esperado comuns|  
  
### <a name="case-4c-adding-projects"></a>Caso c 4: Adicionando projetos  
 Ao adicionar um projeto a uma solução, a solução deve alterar também. Assim, o arquivo de solução também é extraído e deve fazer check-in para concluir a adição.  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Adicionar um projeto a uma solução sob controle de origem em branco (**Check-In** caixa de diálogo)|1.  Crie uma solução em branco.<br />2.  Adicione a solução ao controle de origem.<br />3.  Adicione um novo projeto.<br />4.  Aceite o check-out da solução se solicitado.<br />5.  Check-in do **Check-In** caixa de diálogo.|Comportamento esperado comuns.|  
|Adicionar um projeto a uma solução sob controle de origem em branco (**check-ins pendentes** janela)|1.  Crie uma solução em branco.<br />2.  Adicione a solução ao controle de origem.<br />3.  Adicione um novo projeto.<br />4.  Aceite o check-out da solução se solicitado.<br />5.  Check-in de solução de **check-ins pendentes** janela.|Comportamento esperado comuns.|  
  
## <a name="see-also"></a>Consulte também  
 [Guia de teste para Plug-ins de controle de origem](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
