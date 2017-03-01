---
title: "Como: suprimir notificações de alteração de arquivo | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 18
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
ms.openlocfilehash: c49b1e08ade7122828fdbecbab75a7c63f96a28e
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-suppress-file-change-notifications"></a>Como: suprimir notificações de alteração de arquivo
Quando o arquivo físico que representa o buffer de texto tiver sido alterado, uma caixa de diálogo exibe a mensagem **você deseja salvar as alterações para os seguintes itens?** Isso é conhecido como a notificação de alteração de arquivo. Se várias alterações forem ser para o arquivo, no entanto, essa caixa de diálogo exibindo repetidamente pode rapidamente se tornar irritante.  
  
 Programaticamente, você pode suprimir esta caixa de diálogo usando o procedimento a seguir. Fazendo isso, você pode recarregar um arquivo imediatamente sem a necessidade de avisar o usuário para salvar as alterações de cada vez.  
  
### <a name="to-suppress-file-change-notification"></a>Para suprimir a notificação de alteração de arquivo  
  
1.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>método para determinar qual objeto de buffer de texto está associado com o arquivo aberto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>  
  
2.  Direto a <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>objeto que está na memória para ignorar monitoramento de alterações no arquivo, obtendo o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>da interface do <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>objeto (dados de documentos) e, em seguida, Implementando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A>método com o `fIgnore` parâmetro definido como `true`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> </xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> </xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>  
  
3.  Chamar os métodos de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>e o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>interfaces para atualizar a memória de- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>objeto com as alterações de arquivo (por exemplo, quando um campo é adicionado ao seu componente).</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>  
  
4.  Atualize o arquivo no disco com as alterações sem considerar pendentes edições, que o usuário pode ter em andamento.  
  
     Dessa forma, quando você direcionar o <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>notificações de alteração de objeto para reiniciar o monitoramento de arquivo, o buffer de texto na memória reflete as alterações que você gerou, bem como todas as outras edições pendentes.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> O arquivo no disco reflete o código mais recente gerado por você e alterações feitas pelo usuário salvou anteriormente no código editado pelo usuário.  
  
5.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A>método para notificar o <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>objeto para reiniciar o monitoramento de notificações de alteração definindo o `fIgnore` parâmetro para `false`.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> </xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A>  
  
6.  Se você planeja fazer várias alterações no arquivo, como no caso de controle do código fonte (SCC), você deve informar o serviço de alteração de arquivo global para suspender temporariamente as notificações de alteração de arquivo.  
  
     Por exemplo, se você reescrever o arquivo e, em seguida, alterar o carimbo de hora, você deve suspender as notificações de alteração de arquivo, como as operações de reconfiguração e timestample cada contagem como o evento de alteração de um arquivo separado. Para habilitar a notificação de alteração de arquivo global em vez disso, você deve chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como suprimir a notificação de alteração de arquivo.  
  
```cpp#  
//Misc. helper classes  
  
CSuspendFileChanges::CSuspendFileChanges(  
    /* [in] */ const CString& strMkDocument,   
    /* [in] */ BOOL fSuspendNow /* = TRUE */)   
:  
    m_strMkDocument(strMkDocument),  
    m_fFileChangeSuspended(FALSE)  
{  
    if(fSuspendNow)  
        Suspend();  
}  
CSuspendFileChanges::~CSuspendFileChanges()  
{  
    Resume();  
}  
void CSuspendFileChanges::Suspend()  
{  
    USES_CONVERSION;  
  
    // Prevent suspend from suspending more than once.  
    if(m_fFileChangeSuspended)  
        return;  
  
    IVsRunningDocumentTable* pRDT =   
      _VxModule.GetIVsRunningDocumentTable();  
    ASSERT(pRDT);  
    if (!pRDT)  
        return;  
  
    CComPtr<IUnknown> srpDocData;  
    VSCOOKIE vscookie = VSCOOKIE_NIL;  
    pRDT->FindAndLockDocument(RDT_NoLock, T2COLE(m_strMkDocument),    
      NULL, NULL, &srpDocData, &vscookie);  
    if ( (vscookie == VSCOOKIE_NIL) || !srpDocData)  
        return;  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
    {  
        m_fFileChangeSuspended = TRUE;  
        srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, TRUE);   
        srpDocData->QueryInterface(IID_IVsDocDataFileChangeControl,   
          (void**)&m_srpIVsDocDataFileChangeControl);  
        if(m_srpIVsDocDataFileChangeControl)  
            m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(TRUE);  
    }  
}  
void CSuspendFileChanges::Resume()  
{  
    if(!m_fFileChangeSuspended)  
        return;  
  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
  
    srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, FALSE);   
    if(m_srpIVsDocDataFileChangeControl)  
        m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(FALSE);  
    m_fFileChangeSuspended = FALSE;  
    m_srpIVsDocDataFileChangeControl.Release();  
}  
// Misc. helper classes  
```  
  
## <a name="robust-programming"></a>Programação robusta  
 Se o seu caso envolve várias alterações no arquivo, como no caso do SCC, é importante continuar notificações de alteração de arquivo global antes de alertar os dados do documento para reiniciar o monitoramento de alterações do arquivo.
