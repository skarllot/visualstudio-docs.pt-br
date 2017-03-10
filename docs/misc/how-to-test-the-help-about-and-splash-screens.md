---
title: "Como: testar a Ajuda sobre e telas de abertura | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Caixa de diálogo sobre"
  - "VSPackages, telas de abertura"
  - "VSPackages, identidade Visual"
ms.assetid: 2b959fa4-56d3-44f4-8c2d-9ea2e6fb269d
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# Como: testar a Ajuda sobre e telas de abertura
Após implementar  **Ajuda sobre** e suporte de tela de abertura, você pode testar a sua implementação no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### Para testar a caixa de diálogo Ajuda sobre  
  
1.  Da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o prompt de comando, execute devenv. exe com o **\/setup** alternar.  Para executar no ambiente experimental, digite:  
  
     **devenv \/rootsuffix Exp \/setup**  
  
     **Nota** você precise repetir esta etapa apenas quando você altera o  **Ajuda sobre** informações de tela.  
  
2.  Execute [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] na mesma raiz do registro como mencionada anteriormente, mas sem a **\/setup** alternar:  
  
     **devenv \/rootsuffix Exp**  
  
3.  Sobre o  **Ajuda** menu, clique em  **Sobre o Microsoft Visual Studio**.  
  
     Seu nome VSPackage aparece no  **produtos instalados** lista.  
  
4.  Selecione seu VSPackage na lista.  
  
     As informações do produto VSPackage aparecem no  **detalhes do produto** caixa de texto.  
  
### Para testar a tela inicial  
  
1.  Executar devenv. exe com o **\/setup** alternar.  Para executar no ambiente experimental, digite:  
  
     **devenv \/rootsuffix Exp \/setup**  
  
     **Nota** você precise repetir esta etapa apenas quando você altera as informações da tela de abertura.  
  
2.  Execute [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] na mesma raiz do registro como foi mencionado anteriormente, mas com o **\/splash** alternar em vez da **\/setup** alternar.  
  
     **devenv \/rootsuffix Exp \/splash**  
  
     O VSPackage informações sobre o produto e o logotipo aparecem na tela de abertura.  
  
## Consulte também  
 [Marca de VSPackage](/visual-cpp/misc/vspackage-branding)