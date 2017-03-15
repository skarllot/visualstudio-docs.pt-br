---
title: Plug-ins de controle de origem | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: 17
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
ms.openlocfilehash: 27b72b071e4186e7c53d604c1eae83a794faf683
ms.lasthandoff: 02/22/2017

---
# <a name="source-control-plug-ins"></a>Plug-ins de controle de origem
A seção de referência do SDK de plug-in de controle de origem contém a especificação de interface completa que permite que os sistemas de controle de origem sejam integrados com [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Especifica a sintaxe e semântica das várias funções e tipos de dados que o plug-in de controle de origem deve implementar a interface com o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o ambiente de desenvolvimento integrado (IDE).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)  
 Lista as funções que devem ser implementadas pelo plug-in de controle de origem para estar de acordo com a API de plug-in de controle de origem.  
  
 [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md)  
 Descreve as funções que o plug-in de controle de origem usa para passar informações para o IDE, embora alguns comandos são executados.  
  
 [Enumeradores](../extensibility/enumerators.md)  
 Lista os tipos de dados de enumerador na API de plug-in controle de origem que o plug-in de controle de origem deve saber sobre.  
  
 [Sinalizadores de recurso](../extensibility/capability-flags.md)  
 Descreve o `SCC_CAP_xxx` sinalizadores, que são indicar recursos do provedor.  
  
 [Sinalizadores de bit usados pelos comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)  
 Sinalizadores de listas que são úteis no contexto de comandos específicos.  
  
 [Códigos de erro](../extensibility/error-codes.md)  
 Lista os valores comuns de erro retornados por funções como `SCCTRN`.  
  
 [Cadeias de caracteres usadas como chaves para localizar um controle da fonte de plug-in](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 Descreve as chaves para acessar o registro para localizar o controle de origem plug-in.  
  
 [MSSCCPRJ. Arquivos SCC](../extensibility/mssccprj-scc-file.md)  
 Descreve um arquivo do lado do cliente que contém informações opacas para o IDE, mas que é usado pelo plug-in de controle de origem para localizar a solução ou projeto no controle de versão.  
  
 [Práticas recomendadas para implementar um plug-in de controle de origem](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Fornece um conjunto de lembretes técnicas importantes para lembrar enquanto você estiver implementando a API de plug-in de controle de origem.  
  
 [Restrições em comprimentos de cadeia de caracteres](../extensibility/restrictions-on-string-lengths.md)  
 Descreve as limitações na API de plug-in de controle de origem em comprimentos de cadeias de caracteres usadas em várias funções.  
  
 [Glossário](../extensibility/source-control-plug-in-glossary.md)  
 Fornece termos úteis e suas definições para ler a documentação do SDK de plug-in de controle de origem.  
  
 [Como: desativar avisos de compatibilidade para Plug-ins de controle de origem](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Descreve como desabilitar avisos.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Exemplo de plug-in de controle de origem](http://msdn.microsoft.com/en-us/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 Fornece um exemplo de funcionalidade de plug-in de controle do código-fonte.  
  
 [Guia de teste para Plug-ins de controle de origem](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Descreve os procedimentos de teste relacionados a um plug-in de controle de origem.  
  
 [Criando um controle da fonte de plug-in](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Discute como criar um plug-in de controle de origem que fornece funcionalidade de controle do código-fonte enquanto você estiver usando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interface de usuário de controle de origem (UI).  
  
 [Referência SDK do Visual Studio](../extensibility/visual-studio-sdk-reference.md)  
 Apresenta uma lista de tópicos de referência.
