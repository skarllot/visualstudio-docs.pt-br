---
title: 'Como: acessar o esquema de cores e fontes internas | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 23
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: f646bb0a1606bd5944c945c5db89083fa265afbd
ms.lasthandoff: 04/05/2017

---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>Como: acessar o esquema de cores e fontes internas
O ambiente de desenvolvimento integrado (IDE) do Visual Studio tem um esquema de fontes e cores que está associado com a janela do editor. Você pode acessar esse esquema por meio de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>  
  
 Para usar o esquema de cores e fontes internas, um VSPackage deve:  
  
-   Defina uma categoria para usar com o serviço de fontes e cores padrão.  
  
-   Registre a categoria com o servidor de fontes e cores padrão.  
  
-   Informe o IDE que uma janela específica usa as categorias e itens de exibição interna usando o `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` e `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interfaces.  
  
 O IDE usa a categoria resultante como um identificador para a janela. Nome da categoria é exibido no **Mostrar configurações de:** caixa suspensa no **fontes e cores** página de propriedades.  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Para definir uma categoria usando cores e fontes internas  
  
1.  Crie um GUID arbitrário.  
  
     Esse GUID é usado para identificar exclusivamente uma categoria**.** Esta categoria reutiliza a especificação de cores e fontes de padrão do IDE.  
  
    > [!NOTE]
    >  Ao recuperar dados de fontes e cores com o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>ou outras interfaces, VSPackages usar esse GUID para fazer referência a informações internas.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
  
2.  Nome da categoria deve ser adicionado a uma tabela de cadeia de caracteres dentro do arquivo de recursos (. rc) do VSPackage, para que ele pode ser localizado conforme necessário, quando exibido no IDE.  
  
     Para obter mais informações, consulte [adicionando ou excluindo uma cadeia de caracteres](/cpp/windows/adding-or-deleting-a-string).  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>Para registrar uma categoria usando cores e fontes internas  
  
1.  Construa um tipo especial de entrada de registro de categoria no seguinte local:  
  
     [HKLM\Software\Microsoft. \Visual Studio\\*\<versão do Visual Studio >*\FontAndColors\\*\<categoria >*]  
  
     *\<Categoria >* é o nome da categoria não localizada.  
  
2.  Preencha o registro para usar as fontes de estoque e o esquema de cores com quatro valores:  
  
    |Nome|Tipo|Dados|Descrição|  
    |----------|----------|----------|-----------------|  
    |Categoria|REG_SZ|GUID|Um GUID arbitrária que identifica uma categoria que contém o esquema de fonte e cor estoque.|  
    |Pacote|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> Esse GUID é usada por todos os VSPackages que usam as configurações de fonte e cor padrão.|  
    |NameID|REG_DWORD|ID|A ID de recurso de um nome de categoria localizável o VSPackage.|  
    |ToolWindowPackage|REG_SZ|GUID|O GUID do VSPackage que implementa o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
  
3.  
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>Para iniciar o uso de cores e fontes fornecidas pelo sistema  
  
1.  Criar uma instância do `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` interface como parte da implementação e a inicialização da janela.  
  
2.  Chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A>método para obter uma instância do `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interface correspondente à atual <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>instância.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A>  
  
3.  Chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>duas vezes.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>  
  
    -   Chame uma vez com `VSEDITPROPID_ViewGeneral_ColorCategory`como um argumento.  
  
    -   Chame uma vez com `VSEDITPROPID_ViewGeneral_FontCategory` como um argumento.  
  
     Isso define e expõe os serviços de fontes e cores padrão como uma propriedade da janela.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir inicia o uso de cores e fontes internas.  
  
```  
CComVariant vt;  
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);  
if (spPropCatContainer != NULL){  
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;  
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,   
                                                          &spPropContainer))){  
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Usando fontes e cores](../extensibility/using-fonts-and-colors.md)   
 [Obtendo informações de cores para coloração de texto e fonte](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Acessando configurações de cor e fonte armazenado](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Visão geral de cor e de fonte](../extensibility/font-and-color-overview.md)
