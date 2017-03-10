---
title: "CA1704: os identificadores do recurso devem ter a ortografia correta | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1704"
  - "IdentifiersShouldBeSpelledCorrectly"
helpviewer_keywords: 
  - "CA1704"
  - "IdentifiersShouldBeSpelledCorrectly"
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1704: os identificadores do recurso devem ter a ortografia correta
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldBeSpelledCorrectly|  
|CheckId|CA1704|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra|  
  
## Causa  
 O nome de um identificador contiver uma ou mais palavras que não são reconhecidos pela biblioteca de SPELLING CHECKER da Microsoft.  Esta regra não verifica construtores ou membros especial nomeados como obtém e definem acessadores da propriedade.  
  
## Descrição da Regra  
 Esta regra analisa o identificador em tokens e verifique a ortografia de cada token.  O algoritmo de análise executa as transformações a seguir:  
  
-   Letras maiúsculas iniciará um novo token.  Por exemplo, MyNameIsJoe ao gerencie tokens “my”, “name”, “é”, “Joe”.  
  
-   Para várias letras maiúsculas, a letra maiúscula a última inicia um novo token.  Por exemplo, GUIEditor gerencie tokens da GUI “”, “publicador”.  
  
-   Os apóstrofos à esquerda e à direita são removidos.  Por exemplo, “remetente gerencie tokens” a “remetente”.  
  
-   Os sublinhados significa ao final de um token e serão removidos.  Por exemplo, Hello\_world gerencie tokens “hello world”, “”.  
  
-   Os E comercial inseridos são removidos.  Por exemplo, o formato&gerencie tokens “para formatar”.  
  
 Por padrão, a versão em inglês \(en\) de SPELLING CHECKER é usada.  Nenhum outro dicionário de idioma está atualmente disponível.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, corrigir a ortografia de palavras ou adicionar a palavra a um dicionário personalizado chamado CustomDictionary.xml.  Coloque o dicionário no diretório de instalação da ferramenta, o diretório do projeto, ou no diretório associado com a ferramenta no perfil do usuário \(dados de%USERPROFILE%\\Application \\…\).  Para aprender a adicionar o dicionário personalizado a um projeto em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], consulte [Como personalizar o dicionário de análise do código](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)  
  
-   Adicionar palavras que não deveriam causar uma violação no dicionário\/palavras\/caminho reconhecido.  
  
-   Adicionar palavras que deveriam causar uma violação no dicionário\/palavras\/caminho não reconhecido.  
  
-   Adicionar palavras que devem ser sinalizadas como obsoletas no dicionário\/palavras\/caminho substituído.  Consulte o tópico relacionado [CA1726: usar termos preferenciais](../code-quality/ca1726-use-preferred-terms.md)da regra para obter mais informações.  
  
-   Adicionar exceções às regras de uso de maiúsculas e minúsculas do acrônimo o caminho do dicionário\/acrônimos\/CasingExceptions.  
  
 O seguinte é um exemplo da estrutura de um arquivo de dicionário personalizado.  
  
```  
<Dictionary>  
   <Words>  
      <Unrecognized>  
         <Word>cb</Word>  
      </Unrecognized>  
      <Recognized>  
         <Word>stylesheet</Word>  
         <Word>GotDotNet</Word>  
      </Recognized>  
      <Deprecated>  
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>  
      </Deprecated>  
   </Words>  
   <Acronyms>  
      <CasingExceptions>  
         <Acronym>CJK</Acronym>  
         <Acronym>Pi</Acronym>  
      </CasingExceptions>  
   </Acronyms>  
</Dictionary>  
```  
  
## Quando Suprimir Alertas  
 Suprima um aviso desta regra apenas se as palavras por estar escrito incorretamente intencionalmente e as palavras se aplicam a um conjunto limitado de biblioteca.  As palavras estar escrito corretamente reduzir a curva de aprendizagem que é necessária para novas bibliotecas de software.  
  
## Regras Relacionadas  
 [CA2204: os literais do recurso devem ter a ortografia correta](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
 [CA1703: as cadeias de caracteres do recurso devem ter a ortografia correta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
 [CA1709: os identificadores do recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: os identificadores não devem conter sublinhados](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1726: usar termos preferenciais](../code-quality/ca1726-use-preferred-terms.md)  
  
## Consulte também  
 [Como personalizar o dicionário de análise do código](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)