---
title: "Walkthrough: Using XSLT IntelliSense | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 079d95ac-2eaf-4ae1-9cd3-2c81a961a942
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Walkthrough: Using XSLT IntelliSense
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Essa explicação passo a passo demonstra como usar IntelliSense do XSLT para completar automaticamente o valor de alguns atributos.  
  
### Para usar o IntelliSense no atributo de nome de elementos xsl:with\-param e xsl:call\-template  
  
1.  Crie um novo arquivo XSLT e copie no seguinte código:  
  
    ```  
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
    <!-- These 2 elements effectively assign  
         $messages = resources/en.xml/<messages>,  
         then $messages is used in the "localized-message" template.  -->  
    <xsl:param name="lang">en</xsl:param>  
    <xsl:variable name="messages"  
          select="document(concat('resources/', $lang, '.xml'))/messages"/>   
  
    <xsl:template name="msg23" match="msg23">  
    </xsl:template>  
  
    <xsl:template name="localized-message">  
      <xsl:param name="msgcode"/>  
      <!-- Show message string. -->  
      <xsl:message terminate="yes">  
        <xsl:value-of select="$messages/message[@name=$msgcode]"/>  
      </xsl:message>  
    </xsl:template>  
    </xsl:stylesheet>  
    ```  
  
2.  Insira o cursor após `<xsl:template name="msg23" match="msg23">` e pressione ENTER.  Inicie digitando o elemento `xsl:call-template` a seguir:  
  
    ```  
    <xsl:call-template name="localized-message">  
    </xsl:call-template>  
    ```  
  
     A lista de nomes de modelo aparece no atributo `name=""` do elemento `xsl:call-template` à medida que você digita.  
  
3.  Insira o cursor após `<xsl:call-template name="localized-message">` e pressione ENTER.  Inicie digitando o elemento `xsl:with-param` a seguir:  
  
    ```  
    <xsl:with-param name="msgcode">msg23</xsl:with-param>  
    ```  
  
     A lista de nomes de parâmetro aparece no atributo `name=""` do elemento `xsl:with-param`.  
  
### Para usar o IntelliSense no atributo do modo de um elemento xsl:apply\-templates  
  
1.  Crie um novo arquivo XSLT e copie no seguinte código:  
  
    ```  
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
      <xsl:template match="/">  
        <HTML>  
          <BODY>  
            <TABLE>  
              <xsl:apply-templates select="customers/customer">  
                <xsl:sort select="state"/>  
                <xsl:sort select="name"/>  
              </xsl:apply-templates>  
            </TABLE>  
          </BODY>  
        </HTML>  
      </xsl:template>  
      <xsl:template match="customer">  
        <TR>  
          <xsl:apply-templates select="name" />  
          <xsl:apply-templates select="address" />  
          <xsl:apply-templates select="phone" />  
        </TR>  
      </xsl:template>  
      <xsl:template match="name">  
        <TD STYLE="font-size:14pt font-family:serif">  
          <xsl:apply-templates />  
        </TD>  
      </xsl:template>  
      <xsl:template match="address">  
        <TD>  
          <xsl:apply-templates />  
        </TD>  
      </xsl:template>  
      <xsl:template match="phone">  
        <TD>  
          <xsl:apply-templates />  
        </TD>  
      </xsl:template>  
      <xsl:template match="phone" mode="accountNumber">  
        <xsl:param name="Area_Code"/>  
        <TD STYLE="font-style:italic">  
          1-<xsl:value-of select="."/>-001  
        </TD>  
      </xsl:template>  
    </xsl:stylesheet>  
    ```  
  
2.  Insira o cursor após `<xsl:apply-templates select="phone" />` e pressione ENTER.  Inicie digitando o elemento `xsl: apply-templates` a seguir:  
  
    ```  
    <xsl:apply-templates select="phone"  mode="accountNumber">  
    ```  
  
     A lista de modos de modelo aparece no atributo `mode=""` do elemento `xsl:apply-templates`.  
  
### Para usar o IntelliSense nos atributos stylesheet\-prefix e result\-prefix de um elemento xsl:namespace\-alias  
  
1.  Crie um novo arquivo XSLT e copie no seguinte código:  
  
    ```  
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate"  
    version="1.0">  
      <xsl:param name="browser" select="'InternetExplorer'"/>  
      <xsl:template match="/">  
        <alt:stylesheet>  
          <xsl:choose>  
            <xsl:when test="$browser='InternetExplorer'">  
              <alt:import href="IERoutines.xsl"/>  
              <alt:template match="/">  
                <div>  
                  <alt:call-template name="showTable"/>  
                </div>  
              </alt:template>  
            </xsl:when>  
            <xsl:otherwise>  
              <alt:import href="OtherBrowserRoutines.xsl"/>  
              <alt:template match="/">  
                <div>  
                  <alt:call-template name="showTable"/>  
                </div>  
              </alt:template>  
            </xsl:otherwise>  
          </xsl:choose>  
        </alt:stylesheet>  
      </xsl:template>  
    </xsl:stylesheet>  
    ```  
  
2.  Insira o cursor após `<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate" version="1.0">` e pressione ENTER.  Inicie digitando o elemento `xsl:namespace-alias` a seguir:  
  
    ```  
    <xsl:namespace-alias stylesheet-prefix="alt" result-prefix="xsl"/>  
    ```  
  
     Observe como a lista de prefixos apareceu nos atributos `stylesheet-prefix` e `result-prefix` do elemento de `xsl:namespace-alias`.  
  
## Consulte também  
 [XML Editor IntelliSense Features](../xml-tools/xml-editor-intellisense-features.md)