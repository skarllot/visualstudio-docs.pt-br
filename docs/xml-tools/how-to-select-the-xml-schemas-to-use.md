---
title: "How to: Select the XML Schemas to Use | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Select the XML Schemas to Use
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O editor XML fornece um cache de esquema %InstallDir% localizado no diretório \\ \\ esquemas XML.  O cache de esquema inclui esquemas XML conhecidos que são usados para validação do IntelliSense e de documento XML.  
  
 A propriedade do documento de **Esquemas** é usada para selecionar um ou vários esquemas do idioma da definição de esquema XML \(XSD\) para usar.  Permite que você selecionar esquemas de cache do esquema, ou especifica um esquema que não está localizado no cache.  
  
 Os esquemas que você especifica são salvos no arquivo oculto opções de usuário de solução \(.sln\), junto com quaisquer propriedades restantes de documento XML.  Como resultado, você não tem que digitar novamente esses valores na próxima vez que você abrir a solução.  
  
> [!NOTE]
>  O editor pode validar usando um esquema embutido, ou um esquema referenciado pelo atributo de `xsd:schemaLocation` .  Para obter mais informações, consulte [XML Document Validation](../xml-tools/xml-document-validation.md).  
  
### Para selecionar um esquema XML de cache do esquema  
  
1.  Abrir um arquivo no editor XML.  
  
2.  Na janela propriedades do documento, clique no botão no campo de **Esquemas** .  
  
     A caixa de diálogo **Esquemas XML** é exibida.  A caixa de diálogo lista todos os esquemas com uma extensão .xsd no cache de esquema \(incluindo os esquemas referenciados no arquivo de catalog.xml\), e também qualquer esquema que está na solução atual, aberta no Visual Studio, referenciado em um atributo de `xsd:schemaLocation` , ou referenciado na propriedade de **Esquemas** .  
  
3.  Selecione os esquemas para usar a validação seguindo um destes procedimentos:  
  
    -   Selecione um esquema listado na caixa de diálogo **Esquemas XML** , clique na coluna de **Uso** , selecione **Usar este esquema**.  
  
     \-ou\-  
  
    -   Selecione vários esquemas listados na caixa de diálogo **Esquemas XML** , clique com o botão direito do mouse e selecione **Usar este esquema**.  
  
4.  Clique em **OK**.  
  
     A lista de esquemas selecionados é copiada de volta para a propriedade de documento de **Esquemas** .  
  
### Para adicionar um esquema XML para o cache de esquema  
  
1.  Na janela propriedades do documento, clique no botão no campo de **Esquemas** .  
  
2.  Clique em **Adicionar**.  
  
     Isso abre a caixa de diálogo **Abrir Esquema XSD** .  
  
3.  Procurar e selecione os esquemas para adicionar ao cache de esquema.  
  
4.  Clique em **Abrir**.  
  
     Os esquemas adicionados ao esquema armazenam em cachê e é o valor da coluna de **Use** são definidos como **Usar este esquema**.  
  
### Para excluir um esquema XML de cache do esquema  
  
1.  Na janela propriedades do documento, clique no botão no campo de **Esquemas** .  
  
2.  Selecione o esquema para remover e então clique em **Remover**.  
  
     O esquema é removido do cache de memória do esquema, mas não é removido do sistema de arquivos.  
  
    > [!NOTE]
    >  Se você ainda tiver uma referência para o esquema através de um atributo de `schemaLocation` , ou `targetNamespace` correspondente em **Remover** não funcionará nesta situação devido à associação automática.  Nesse caso é recomendável que você marca o esquema como **Não usar os esquemas selecionados** na coluna de **Use** .  
  
## Consulte também  
 [Schema Cache](../xml-tools/schema-cache.md)   
 [XML Schemas Dialog Box](../xml-tools/xml-schemas-dialog-box.md)   
 [XML Editor](../xml-tools/xml-editor.md)