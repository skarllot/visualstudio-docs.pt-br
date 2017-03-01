---
title: "Modos de exibição únicos e multi-guia | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: 22
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
ms.openlocfilehash: 464270ec43f788200de8c0c04d4325776f262a5e
ms.lasthandoff: 02/22/2017

---
# <a name="single-and-multi-tab-views"></a>Modos de exibição únicos e multi-guia
Um editor pode criar diferentes tipos de modos de exibição. Um exemplo é uma janela do editor de código, o outro é um designer de formulários.  
  
 Uma exibição de várias guias é um modo de exibição que tem várias guias. Por exemplo, o editor de HTML possui duas guias na parte inferior: **Design** e **fonte**, cada uma exibição lógica. O modo de exibição de design exibe uma página da web processada, enquanto o outro exibe o HTML que compõe a página da web.  
  
## <a name="accessing-physical-views"></a>O acesso a visualizações físicas  
 Modos de exibição físicos hospedam objetos de exibição de documento, cada um representando uma exibição dos dados no buffer, como código ou um formulário. Da mesma forma, cada objeto de exibição de documento tem uma exibição física (identificado por algo conhecido como uma cadeia de caracteres de exibição física) e, em geral, uma única exibição lógica.  
  
 Em alguns casos, no entanto, uma exibição física pode ter dois ou mais modos de exibição lógicos. Alguns exemplos são um editor que tem uma janela dividida com modos de exibição lado a lado ou um designer de formulários que tem um modo de exibição de design/GUI e um modo de exibição de código behind-o formulário.  
  
 Para habilitar o editor acessar todos os modos de exibição físicos disponíveis, você deve criar uma cadeia de caracteres de exibição física exclusivo para cada tipo de objeto de exibição de documento que pode criar sua fábrica de editor. Por exemplo, o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] fábrica de editor pode criar documento objetos de exibição para uma janela de código e uma janela de designer de formulários.  
  
## <a name="creating-multi-tabbed-views"></a>Criando modos de exibição de várias guias  
 Embora um objeto de exibição de documento deve ser associado uma exibição física por meio de uma cadeia de caracteres de exibição física exclusivo, você pode colocar várias guias no modo de exibição físico para ativar a visualização de dados de maneiras diferentes. Nessa configuração de várias guias, todas as guias estão associadas com a mesma cadeia de caracteres de exibição física, mas cada guia é fornecido uma GUID de exibição lógica diferente.  
  
 Para criar um modo de exibição de várias guias para um editor, implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView>da interface e, em seguida, associar uma exibição lógica diferente GUID (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) com cada guia criar.</xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID> </xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView>  
  
 O editor de HTML do Visual Studio é um exemplo de um editor com um modo de exibição de multi-guia. Ele tem **Design** e **fonte** guias. Para habilitar isso, uma exibição lógica diferente está associada a cada guia `LOGICALVIEWID_TextView` para o **Design** guia e `LOGICALVIEWID_Code` para o **fonte** guia.  
  
 Especificando o modo de exibição lógico apropriado, um VSPackage pode acessar o modo de exibição que corresponde a uma finalidade específica, como criação de um formulário, edição de código ou depurar o código. No entanto, uma das janelas deve ser identificada pela cadeia de caracteres nula e isso deve corresponder ao modo de exibição lógico primário (`LOGVIEWID_Primary`).  
  
 A tabela a seguir lista os valores do modo de exibição lógico disponível e seu uso.  
  
|GUID DE LOGVIEWID|Uso recomendado|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|Modo de exibição padrão/primário da fábrica de editor.<br /><br /> Todas as fábricas devem oferecer suporte a esse valor. Este modo de exibição deve usar a cadeia de caracteres nula como sua cadeia de caracteres de exibição física. Pelo menos uma exibição lógica deve ser definida para esse valor.|  
|`LOGVIEWID_Debugging`|Modo de depuração. Normalmente, `LOGVIEWID_Debugging` mapeia para a mesma exibição da `LOGVIEWID_Code`.|  
|`LOGVIEWID_Code`|Exibição iniciado pela **Exibir código** comando.|  
|`LOGVIEWID_Designer`|Exibição iniciado pela **Exibir formulário** comando.|  
|`LOGVIEWID_TextView`|Exibição do editor de texto. Esta é a exibição que retorna <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, na qual você pode acessar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|  
|`LOGVIEWID_UserChooseView`|Solicita que o usuário escolha qual modo de exibição para usar.|  
|`LOGVIEWID_ProjectSpecificEditor`|Passados pelo **abrir com** caixa de diálogo<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Quando o usuário escolhe a entrada "(editor padrão do projeto)".|  
  
 Embora o modo de exibição lógico GUIDs são extensíveis, você pode usar somente os GUIDs de modo de exibição lógico definidos no seu VSPackage.  
  
 Durante o desligamento, o Visual Studio mantém o GUID da fábrica de editor e as cadeias de exibição física associadas à janela de documento para que ele pode ser usado para reabrir janelas de documento quando a solução é reaberta. Somente as janelas que estão abertas quando uma solução é fechada são mantidas no arquivo de solução (. sln). Esses valores correspondem do `VSFPROPID_guidEditorType` e `VSFPROPID_pszPhysicalView` valores passados a `propid` parâmetro no <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>  
  
## <a name="example"></a>Exemplo  
 Este trecho de código ilustra como o <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView>objeto é usado para acessar uma exibição que implemente `IVsCodeWindow`.</xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> Nesse caso, o <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>serviço é usado para chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>e solicitação `LOGVIEWID_TextView`, que obtém um ponteiro para um quadro de janela.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> </xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> Um ponteiro para o objeto de exibição do documento é obtido chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>e especificando um valor de `VSFPROPID_DocView`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Do objeto de exibição de documento, `QueryInterface` é chamado para `IVsCodeWindow`. A expectativa nesse caso é que um editor de texto é retornado, e então o objeto de exibição de documento retornado no <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>método é uma janela de código.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>  
  
```cpp#  
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)  
{  
  HRESULT hr;  
  if (NULL == szFile || !*szFile)  
    return E_INVALIDARG;  
  
  if (iLine == -1L)  
    return S_FALSE;  
  
  VSITEMID                  itemid;  
  VARIANT                   var;  
  RECT                      rc;  
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;  
  IVsCodeWindow *           pCodeWin    = NULL;  
  IVsTextView *             pTextView   = NULL;  
  IVsUIHierarchy *          pHierarchy  = NULL;  
  IVsWindowFrame *          pFrame      = NULL;  
  IUnknown *                pUnk        = NULL;  
  IVsHighlight *            pHighlight  = NULL;  
  
  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));  
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));  
  pFrame->Show();  
  VariantInit(&var);  
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));  
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }  
  pUnk = V_UNKNOWN(&var);  
  if (NULL != pUnk)  
  {  
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));  
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||  
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )  
    {  
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);  
      // uncover selection  
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));  
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));  
      UncoverSelectionRect(&rc);  
    }  
  }  
  
Error:  
  CLEARINTERFACE(pHighlight);  
  CLEARINTERFACE(pTextView);  
  CLEARINTERFACE(pCodeWin);  
  CLEARINTERFACE(pUnk);  
  CLEARINTERFACE(pFrame);  
  CLEARINTERFACE(pOpenDoc);  
  CLEARINTERFACE(pHierarchy);  
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);  
  return hr;  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Suporte a vários modos de exibição de documento](../extensibility/supporting-multiple-document-views.md)   
 [Como: anexar modos de exibição para dados de documentos](../extensibility/how-to-attach-views-to-document-data.md)   
 [Criar Designers e editores personalizados](../extensibility/creating-custom-editors-and-designers.md)
