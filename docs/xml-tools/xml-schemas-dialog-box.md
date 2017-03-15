---
title: "XML Schemas Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# XML Schemas Dialog Box
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A caixa de diálogo **Esquemas XML** é usada para selecionar quais os esquemas de linguagem de definição de esquema XML \(XSD\) para associar a um documento XML.  Você pode selecionar um esquema de cache do esquema, ou especificar um esquema que não está localizado no cache.  Os esquemas selecionados são considerados parte de um conjunto de esquema.  O esquema é usado para o IntelliSense e também validação de documento XML.  
  
 Você pode acessar a caixa de diálogo **Esquemas XML** por qualquer um que clica no botão de **Esquemas** na janela propriedades do documento, ou selecionando **Esquemas** de menu de **XML** .  
  
## Lista UIElement  
 **Uso**  
 Selecione como o esquema XML deve ser usada.  
  
-   **Automático**.  Este esquema não está em uso pelo documento atual mas está disponível para a associação automática.  Se o documento XML declarar um namespace que corresponde `targetNamespace` deste esquema, o esquema será associado e é automaticamente encapsulado no conjunto de esquema.  
  
-   **Usar este esquema**.  Este esquema está sendo usado pelo documento atual.  Qualquer o usuário que solicitou explicitamente este esquema está usado clicando nessa coluna, ou o esquema foi associado automaticamente com base em `targetNamespace`correspondente.  
  
-   **Não usar os esquemas selecionados**.  Este esquema não é usado pelo documento atual, mesmo se o esquema tem `targetNamespace`correspondente.  Essa configuração pode ser útil para resolver conflitos quando há mais de uma versão do mesmo esquema no cache ou na solução de esquema.  
  
 **Namespace de Destino**  
 Exibe o namespace de destino associada com o esquema XML.  
  
 **Nome do Arquivo**  
 Exibe o nome do arquivo de esquema XML.  
  
 **Adicionar**  
 Abre a caixa de diálogo **Abrir Esquema XSD** , que permite que você selecionar esquemas adicionais para adicionar ao conjunto de esquema.  Quando você adiciona um esquema ao conjunto de esquema, o valor da coluna de **Uso** é definido como **Usar este esquema**.  
  
 **Remover**  
 Remove o esquema do dataset selecionado de esquema.  Remove o esquema de cache de memória do esquema, mas não no sistema de arquivos.  
  
## Consulte também  
 [XML Editor Components](../xml-tools/xml-editor-components.md)   
 [How to: Select the XML Schemas to Use](../xml-tools/how-to-select-the-xml-schemas-to-use.md)   
 [Schema Cache](../xml-tools/schema-cache.md)