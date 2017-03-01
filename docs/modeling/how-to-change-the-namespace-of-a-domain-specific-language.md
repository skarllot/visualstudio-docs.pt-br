---
title: "Como: alterar o Namespace de uma linguagem específica do domínio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 19
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b7419766b4c195c3bcef2aa45e886004a89fb5ec
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Como alterar o namespace de uma linguagem específica do domínio
Você pode alterar o namespace de uma linguagem específica do domínio. Você deve fazer a alteração no **Gerenciador de DSL**, nas propriedades do projeto pacote Dsl e nas informações de assembly.  
  
### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Para alterar o namespace de uma linguagem específica do domínio  
  
1.  Em **Gerenciador de DSL**, clique o **Dsl** nó.  
  
2.  No **propriedades** janela, alterar o **Namespace** propriedade.  
  
3.  Salve a solução e transformar os modelos.  
  
4.  Sobre o **projeto** menu, clique em **Dsl propriedades**.  
  
     As propriedades de seu projeto são exibidas.  
  
5.  Clique o **aplicativo** guia.  
  
6.  Alterar o **namespace padrão** propriedade para o novo nome de namespace.  
  
7.  Se você também quiser alterar o nome do assembly, altere o **propriedade de nome do Assembly.**  
  
8.  Se você tiver alterado o nome do Assembly, abra DslPackage\Package.tt e atualize esta linha:  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. Se você tiver gravado um código personalizado, certifique-se de alterar as referências de namespace e classe nos arquivos de código.  
  
10. Redefina a instância Experimental do Visual Studio.  
  
    1.  Excluir **\Users\\***{seu nome}***\AppData\Local\Microsoft\VisualStudio\\\*Exp**  
  
    2.  No Windows **iniciar** menu, escolha **todos os programas**, **SDK do Microsoft Visual Studio 2010**, **ferramentas**, **redefinir a instância Experimental**.  
  
11. Sobre o **criar** menu, escolha **recompilar solução**.  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica do domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
