---
title: Atrasada o carregamento de documentos | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 6
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
ms.openlocfilehash: b5d2f48a46fe95cc8fd05d1c0ee7694ee875d969
ms.lasthandoff: 02/22/2017

---
# <a name="delayed-document-loading"></a>Atraso de carregamento de documentos
Quando um usuário reabre uma solução do Visual Studio, a maioria dos documentos associados não é carregada imediatamente. O quadro de janela de documento é criado em um estado pendente inicialização e um documento de espaço reservado (chamado de um quadro de stub) é colocado na tabela de documento em execução (RDT).  
  
 Sua extensão pode fazer com que os documentos do projeto para ser carregado desnecessariamente consultando elementos nos documentos antes de serem carregados. Isso pode aumentar o espaço de memória geral para o Visual Studio.  
  
## <a name="document-loading"></a>Carregamento de documentos  
 O quadro de stub e o documento são totalmente inicializados quando o usuário acessa o documento, por exemplo, selecionando a guia do quadro da janela. O documento também pode ser inicializado por uma extensão que solicita os dados do documento, acessando o RDT diretamente para obter os dados de documentos ou acessando o RDT indiretamente por fazer uma das seguintes chamadas:  
  
-   Método show do quadro da janela: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>  
  
-   O método GetProperty do quadro de janela <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>em qualquer uma das seguintes propriedades:</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID></xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID></xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID></xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID></xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID></xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID></xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
 Se sua extensão de usar código gerenciado, você não deve chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A>, a menos que você tiver certeza de que o documento não está no estado pendente de inicialização ou o documento seja totalmente inicializada...</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> Isso ocorre porque esse método sempre retorna o documento objeto de dados, criando-se necessário. Em vez disso, você deve chamar um dos métodos na interface IVsRunningDocumentTable4.  
  
 Se sua extensão usa C++, você pode passar `null` para os parâmetros que você não deseja.  
  
 Você pode evitar o carregamento de documentos desnecessários chamando um dos métodos a seguir antes de você perguntar para as propriedades relevantes: antes de você pedir outras propriedades.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>usando <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.</xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> Esse método retorna um <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>objeto que inclui um valor para <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>se o documento ainda não foi inicializado.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> </xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>  
  
 Você pode saber quando um documento foi carregado por assinatura do evento RDT que é gerado quando um documento está totalmente inicializado. Há duas possibilidades:  
  
-   Se o coletor de eventos implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, você pode assinar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>  
  
-   Caso contrário, você pode assinar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>  
  
 Este é um cenário de acesso do documento hipotético. Uma extensão que deseja exibir algumas informações sobre como abrir documentos do Visual Studio, por exemplo Editar Bloquear contagem e algo sobre os dados do documento. Enumera os documentos usando o RDT <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, em seguida, chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A>para cada documento para recuperar os dados de documento e a contagem de bloqueio editar.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> Se o documento estiver no estado pendente inicialização, solicitar dados de documento faz com que ele desnecessariamente sejam inicializados.  
  
 Uma maneira mais eficiente de fazer isso é usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A>para obter a contagem de bloqueio de edição e, em seguida, use <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>para determinar se o documento foi inicializado.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> Se os sinalizadores não incluem <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, o documento já foi inicializado e solicita os dados de documentos com <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A>não faz com que qualquer inicialização desnecessária.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> </xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> Se os sinalizadores de incluir <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, a extensão deve evitar solicita os dados do documento até que o documento seja inicializado.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> Isso pode ser detectado no manipulador de eventos OnAfterAttributeChange(Ex).  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Testando extensões para ver se eles forçam a inicialização  
 Não há nenhuma indicação visível para indicar se um documento foi inicializado, portanto, pode ser difícil saber se a extensão está forçando a inicialização. Você pode definir uma chave do registro que facilita a verificação, pois faz com que o título de cada documento que não está totalmente inicializado para que o texto `[Stub]` no título.  
  
 Em **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad]**, defina **StubTabTitleFormatString** para **{0} [Stub]**.
