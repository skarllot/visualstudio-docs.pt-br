---
title: "Obter descri&#231;&#245;es dos campos na janela de propriedades | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Janela de propriedades, descrições do campo"
ms.assetid: 7d92bb6a-b9b9-4cd8-99e9-b5ee129b52a3
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Obter descri&#231;&#245;es dos campos na janela de propriedades
Na parte inferior da **propriedades** janela, uma área de descrição exibe informações relacionadas ao campo de propriedade selecionada. Esse recurso é ativado por padrão. Se você quiser ocultar o campo de descrição, clique o **propriedades** janela e clique em **Descrição**. Isso também remove a marca de seleção ao lado de **Descrição** título na janela do menu. Você pode exibir o campo novamente, seguindo as mesmas etapas para ativar\/desativar **Descrição** novamente.  
  
 As informações no campo Descrição vem de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Cada método de interface, coclass e assim por diante podem ter um não localizado `helpstring` atributo na biblioteca de tipos. O **propriedades** janela recupera a cadeia de caracteres de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.  
  
### Para especificar cadeias de caracteres de ajuda localizado  
  
1.  Adicionar o `helpstringdll` à instrução library na biblioteca de tipos de atributo \(`typelib`\).  
  
    > [!NOTE]
    >  Esta etapa é opcional se a biblioteca de tipos está em um arquivo de biblioteca \(. olb\) do objeto.  
  
2.  Especifique `helpstringcontext` atributos para as cadeias de caracteres. Você também pode especificar `helpstring` atributos.  
  
     Esses atributos são distintos de `helpfile` e `helpcontext` atributos que estão contidos nos tópicos de Ajuda do arquivo. chm real.  
  
 Para recuperar as informações de descrição a ser exibida para o nome da propriedade realçado, o **propriedades** janela chamadas <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> para a propriedade selecionada, especificando o desejado `lcid` atributo para a cadeia de caracteres de saída. Internamente, <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> encontra o arquivo. dll especificado no `helpstringdll` atributo e chamadas `DLLGetDocumentation` nesse arquivo. dll com o contexto especificado e `lcid` atributo.  
  
 A assinatura e a implementação de `DLLGetDocumentation` são:  
  
```  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 O `DLLGetDocumentation` função deve ser uma exportação definida no arquivo. def para a DLL.  
  
 Internamente, é criado um arquivo. olb que é realmente uma DLL. Essa DLL contém um recurso, o arquivo de biblioteca \(. tlb\) de tipo e uma função exportada, `DLLGetDocumentation`.  
  
 No caso de arquivos. olb, o `helpstringdll` atributo é opcional, pois ele é o mesmo arquivo que contém o próprio arquivo. tlb.  
  
 Para obter cadeias de caracteres aparecerão no **descrições** painel, portanto, o mínimo que você precisa fazer é especificar o `helpstring` atributo na biblioteca de tipos. Se você quiser que essas cadeias de caracteres a ser localizada, você precisa especificar o `helpstringdll` atributo \(opcional\) e o `helpstringcontext` atributo \(obrigatório\) e implementar `DLLGetDocumentation`.  
  
 Não existem interfaces adicionais que precisam ser implementados ao obter localizadas informações por meio do idl `helpstringcontext` atributo e `DLLGetDocumentation`.  
  
 Outra maneira de obter o nome localizado e a descrição de uma propriedade está implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Para obter mais informações relacionadas à implementação desse método, consulte [Interfaces e os campos da janela de propriedades](../extensibility/internals/properties-window-fields-and-interfaces.md).  
  
## Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Interfaces e os campos da janela de propriedades](../extensibility/internals/properties-window-fields-and-interfaces.md)   
 [Estendendo propriedades](../extensibility/internals/extending-properties.md)   
 [helpstringdll](/visual-cpp/windows/helpstringdll)   
 [helpstring](/visual-cpp/windows/helpstring)   
 [helpstringcontext](/visual-cpp/windows/helpstringcontext)   
 [helpcontext](/visual-cpp/windows/helpcontext)   
 [helpfile](/visual-cpp/windows/helpfile)   
 [lcid](/visual-cpp/windows/lcid)