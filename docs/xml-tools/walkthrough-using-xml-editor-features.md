---
title: "Walkthrough: Using XML Editor Features | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Walkthrough: Using XML Editor Features
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

As etapas nessa explicação passo a passo mostram como criar um novo documento XML.  A explicação passo a passo também usa alguns dos recursos do editor XML que tornam valioso para criar XML.  
  
> [!NOTE]
>  Antes de iniciar a explicação passo a passo, salve o arquivo de hireDate.xsd \(incluído abaixo neste tópico\) para seu computador local.  
  
### Para criar um novo arquivo XML e associá\-la com um esquema XML  
  
1.  No menu de **Arquivo** , aponte para **Novo**, e clique **Arquivo**.  
  
2.  **Arquivo XML** Selecione no painel de **Modelos** e clique em **Abrir**.  
  
     Um novo arquivo é aberto no editor.  O arquivo contém uma declaração XML padrão, `<?xml version="1.0" encoding="utf-8">`.  
  
3.  Na janela de propriedades do documento, clique no botão procurar \(**...**\) no campo **Esquemas**.  
  
     A caixa de diálogo **Esquemas XSD** é exibida.  
  
4.  Clique em **Adicionar**.  
  
     A caixa de diálogo **Abrir Esquema XSD** é exibida.  
  
5.  Selecione o arquivo de hireDate.xsd e clique **Abrir**.  
  
6.  Clique em **OK**.  
  
     O esquema XML agora está associado com o documento XML.  O esquema XML é usado para validar o documento.  Também é usado pelo IntelliSense para preencher a lista de membros de elementos válidos.  
  
### Para adicionar dados  
  
1.  Tipo `<` no painel do editor.  
  
     A lista de membros exibe os itens possíveis:  
  
    -   **\! \-\-** para adicionar um comentário.  
  
    -   **\! DOCTYPE** para adicionar um tipo de documento.  
  
    -   **?** para adicionar uma instrução de processamento.  
  
    -   **funcionário** para adicionar o elemento raiz.  
  
2.  Selecione **\<\!\-** para adicionar um nó de comentário e pressione ENTER.  
  
     O editor insere uma marca de fim do comentário e colocar o cursor entre o início e marcas de comentário final.  
  
3.  Digite o arquivo XML de teste.  
  
4.  Em uma nova linha, digite `<`e selecione **funcionário** da lista de membros.  
  
     O editor adiciona o início de um elemento XML, `<employee`.  Neste momento você pode adicionar atributos para o elemento ou você pode fechar a tag de início digitando `>`.  
  
5.  Tipo `>` para a marca de fechamento.  
  
6.  O editor adiciona a marca de fim.  A marca de fim é adicionada com um a linha subescrita ondulada que indica um erro de validação.  A dica de ferramenta exibe a mensagem: O elemento “empregado” tem conteúdo incompleto.  'ID' esperado.  
  
7.  Digite `<` e **ID** a partir da lista de membros.  Digite `>`.  
  
     O editor adicione o elemento XML, `<ID></ID>`, e posicionar o cursor após a marca de início de identificação.  
  
8.  ABC de tipo.  
  
     O texto de ABC tem um a linha subescrita ondulada.  A dica de ferramenta exibe a mensagem: O elemento “identificação” tem um valor inválido de acordo com seu tipo de dados.  
  
9. Clique com o botão direito do mouse no elemento de identificação e selecione **Ir Para Definição**.  
  
     O editor abre o arquivo de hireDate.xsd em uma nova janela de documento e posicionar o cursor na definição de elemento do esquema de identificação.  
  
10. Retornar para o arquivo XML, e substitua o texto de ABC com os 123.  
  
     O sublinhado e o ToolTip ondulados são desmarcados no valor do elemento ID.  A dica de ferramenta para a marca de fim do funcionário agora exibe a mensagem: O elemento “empregado” tem conteúdo incompleto.  “Data de admissão esperada”.  
  
11. Coloque o cursor após a marca de fim de identificação, digite `<`, data de admissão select da lista de membros, e digite dentro `>`.  
  
     O editor adicione o elemento XML, `<hire-date></hire-date>`, e posicionar o cursor após a marca de início da data de admissão.  
  
12. Tipo em 2003\-01 \- 10 para o valor de data de admissão.  
  
### Para formatar o documento XML  
  
1.  Selecione o botão de **Formatar documento** da barra de ferramentas do editor XML.  
  
     O documento XML é reformatado.  
  
### Para salvar o documento XML  
  
1.  No menu de **Arquivo** , selecione **Salvar como**.  
  
     A caixa de diálogo **Salvar Arquivo Como** é exibida.  O nome de arquivo padrão é “XMLFile1”.  
  
2.  Digite o nome de arquivo e o local para o documento XML e clique **Salvar**.  
  
## hireDate.xsd Arquivo  
 O seguinte arquivo de esquema é usado por passo a passo.  
  
```  
<?xml version="1.0"?>  
<xs:schema attributeFormDefault="unqualified"  
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"  
     xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="employee">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="ID" type="xs:unsignedShort" />  
        <xs:element name="hire-date" type="xs:date" />  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## Consulte também  
 [XML Editor](../xml-tools/xml-editor.md)