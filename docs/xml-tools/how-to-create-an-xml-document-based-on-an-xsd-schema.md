---
title: "How to: Create an XML Document Based on an XSD Schema | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Create an XML Document Based on an XSD Schema
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O recurso **Gerar XML de Exemplo** gera um arquivo XML de exemplo com base no seu arquivo de esquema XML \(XSD\).  
  
 Você pode usar esta opção para os seguintes situações:  
  
-   Para entender o uso de várias construções no seu esquema.  
  
-   Para confirmar que o esquema faz o que é esperado dele.  
  
 O recurso **Gerar XML de Exemplo** está disponível somente nos elementos globais, e exige um conjunto de esquema XML válido.  
  
 Esse recurso normalmente gera documentos XML válidos.  No entanto, se o esquema contiver um ou mais dos seguintes, o exemplo poderá não ser válido:  
  
-   As restrições de identidade `xs:key`, `xs:keyref` e `xs:unique`.  
  
-   `xs:pattern` facetas.  
  
-   Enumerações do tipo `xs:QName`.  
  
-   Tipos `xs:ENTITY`, `xs:ENTITIES` e `xs:NOTATION`.  
  
 Além disso, observe que o conteúdo de `xs:base64Binary` será gerado apenas se as enumerações ocorrerem no esquema para esse tipo.  
  
### Para gerar um documento de instância XML baseado no arquivo XSD  
  
1.  Siga as etapas em [How to: Create and Edit an XSD Schema File](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  No [XML Schema Explorer](../xml-tools/xml-schema-explorer.md), clique com o botão direito do mouse no elemento global `PurchaseOrder`.  Selecione **Gerar o XML de Exemplo**.  
  
     Quando você selecionar essa opção, o arquivo PurchaseOrder.xml com o conteúdo XML de exemplo a seguir será gerado e aberto no Editor de XML:  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <PurchaseOrder OrderDate="1900-01-01" xmlns="http://tempuri.org/PurchaseOrderSchema.xsd">  
      <ShipTo country="US">  
        <name>name1</name>  
        <street>street1</street>  
        <city>city1</city>  
        <state>state1</state>  
        <zip>1</zip>  
      </ShipTo>  
      <ShipTo country="US">  
        <name>name2</name>  
        <street>street2</street>  
        <city>city2</city>  
        <state>state2</state>  
        <zip>-79228162514264337593543950335</zip>  
      </ShipTo>  
      <BillTo country="US">  
        <name>name1</name>  
        <street>street1</street>  
        <city>city1</city>  
        <state>state1</state>  
        <zip>1</zip>  
      </BillTo>  
    </PurchaseOrder>  
    ```  
  
## Consulte também  
 [Working with XML Data](../xml-tools/working-with-xml-data.md)