---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.IO.FileLoadException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Classe FileLoadException"
ms.assetid: 6b4519e3-4d29-4031-8aec-c2735b4ee16d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.IO.FileLoadException
Um <xref:System.IO.FileLoadException> exceção é lançada quando um assembly gerenciado é encontrado, mas não pode ser carregado.  
  
## Dicas associadas  
 **Certifique\-se de que o arquivo é um assembly válido do .NET Framework.**  
 Essa exceção é lançada se o arquivo não é um assembly válido do .NET Framework. Para obter mais informações, consulte <xref:System.Reflection.Assembly>.  
  
 **Verifique se que um assembly ou módulo não foi carregado duas vezes com duas evidências diferentes.**  
 Evidência é o conjunto de informações que constituem a entrada para decisões de diretiva de segurança, como quais permissões pode ser concedido ao código. Para obter mais informações, consulte <xref:System.EnterpriseServices.Internal.Publish.GacRemove%2A> e <xref:System.Reflection.Assembly.Evidence%2A>  
  
 **Se usar os métodos RegisterAssembly ou UnregisterAssembly, verifique se que o nome do assembly não é mais longo que os caracteres MAX\_PATH.**  
 Comprimento do nome do assembly não pode exceder MAX\_PATH. Para obter mais informações, consulte <xref:System.EnterpriseServices.Internal.IComSoapPublisher.RegisterAssembly%2A> e <xref:System.EnterpriseServices.Internal.IComSoapPublisher.UnRegisterAssembly%2A>.  
  
 **Se carregar um assembly satélite, verifique se que o CultureInfo especificado corresponde ao CultureInfo do arquivo.**  
 Assemblies satélites contêm recursos localizados que contêm código executável não localizável e recursos para uma única cultura que servem como o padrão ou cultura neutra. Para obter mais informações, consulte <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A>.  
  
## Consulte também  
 <xref:System.IO.FileLoadException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)