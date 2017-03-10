---
title: "How to: Use the XML Schema Designer with XML Literals | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Use the XML Schema Designer with XML Literals
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico descreve como exibir um esquema associado com um literal XML em um projeto Visual Basic.  
  
### Para criar um novo projeto de aplicativo de console do Visual Basic  
  
1.  Inicie o Visual Studio 2010.  
  
2.  No menu **Arquivo**, selecione **Novo** e selecione **Projeto**.  A caixa de diálogo **Novo Projeto** é exibida.  Para **Tipos de projeto**, **Outras linguagens,** e selecione **Visual Basic**.  Para **Modelos**, aplicativo de console.  No tipo `XMLLiterals` no campo de **Nome** e local de projeto em **Local** coloque.  Clique em **OK**.  
  
     O novo poject é criado.  O projeto de XMLLiterals contém um arquivo de origem Visual Basic, Module1.vb.  
  
### Para adicionar um arquivo XSD existente ao projeto  
  
1.  Abra um novo arquivo de texto no bloco de notas. `` Copie o código de exemplo de esquema XML de [Purchase Order Schema](../xml-tools/sample-xsd-file-simple-schema.md) e colá\-la no arquivo.  
  
2.  Salve o arquivo em qualquer local com o nome PurchaseOrderSchema.xsd.  
  
3.  No Solution Explorer, clique com o botão direito do mouse no nome do projeto, selecione **Adicionar**, selecione **Item Existente...** A caixa de diálogo **Adicionar Item Existente** aparece.  Navegue até o arquivo de PurchaseOrderSchema.xsd, selecioná\-lo, e clique em **Adicionar**.  
  
     O projeto de XMLLiterals agora contém dois arquivos: Module1.vb e PurchaseOrderSchema.xsd.  
  
### Para adicionar código Visual Basic com uma literal XML, com base no arquivo XSD incluído no projeto  
  
1.  Substitua o código no arquivo Module1.vb com o seguinte código:  
  
    ```  
    Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">  
  
    Module Module1  
        Sub Main()  
  
            Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">  
                                 <ns:ShipTo country="US">  
                                     <ns:name>name1</ns:name>  
                                     <ns:street>street1</ns:street>  
                                     <ns:city>city1</ns:city>  
                                     <ns:state>state1</ns:state>  
                                     <ns:zip>1</ns:zip>  
                                 </ns:ShipTo>  
                                 <ns:BillTo country="US">  
                                     <ns:name>name1</ns:name>  
                                     <ns:street>street1</ns:street>  
                                     <ns:city>city1</ns:city>  
                                     <ns:state>state1</ns:state>  
                                     <ns:zip>1</ns:zip>  
                                 </ns:BillTo>  
                             </ns:PurchaseOrder>  
  
        End Sub  
    End Module  
    ```  
  
2.  Clique com o botão direito do mouse em qualquer nó XML em um literal XML ou uma importação do namespace XML e selecione **Mostrar no esquema Explorer**.  
  
     XML Schema Explorer lado a lado é exibido com um arquivo Visual Basic que possui a literal XML assotiated com o esquema XML.