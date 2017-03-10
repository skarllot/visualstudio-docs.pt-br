---
title: "Registrando servi&#231;os | Microsoft Docs"
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
  - "Serviços de registro"
ms.assetid: c4ebac40-0374-4dda-948e-06fdda0e9c81
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# Registrando servi&#231;os
Para oferecer suporte a carregamento sob demanda, um provedor de serviços deve registrar seus serviços globais com [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Durante o desenvolvimento, provedores de serviço gerenciado registrar serviços e substituições de serviço adicionando atributos ao código\-fonte para pacotes e, em seguida, criar os pacotes no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Isso executa o utilitário RegPkg.exe do assembly resultante, registrar o pacote e preparação para implantação. Para obter mais informações, consulte [Como: registrar um serviço](../misc/how-to-register-a-service.md).  
  
 Provedores de serviço não gerenciado devem registrar os serviços prestados com [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nos serviços de seção ou o serviço substitui a seção do registro do sistema. O fragmento de arquivo. reg a seguir mostra como o serviço, SVsTextManager, pode ser registrado:  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}] @="{F5E7E720-1401-11d1-883B-0000F87579D2}" "Name"="SVsTextManager"  
```  
  
 No exemplo acima, o número de versão é a versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], como 7.1 ou 8.0, a chave {F5E7E71D\-1401\-11d1\-883B\-0000F87579D2} é o identificador de serviço \(SID\) do serviço, SVsTextManager, e o valor padrão {F5E7E720\-1401\-11d1\-883B\-0000F87579D2} é o GUID do Gerenciador de texto VSPackage, que fornece o serviço do pacote.  
  
## Serviços remotos e Threads em segundo plano  
 Serviços que você fornece não estão automaticamente disponíveis remotamente ou threads em segundo plano. Para disponibilizá\-las, você deve criar e registrar uma biblioteca de tipos.  
  
 Do código não gerenciado que usa o Visual Studio biblioteca \(. VSL\), você pode registrar a biblioteca de tipos desta forma:  
  
```  
#define VSL_REGISTER_TYPE_LIB TRUE #include <VSLPackageDllEntryPoints.cpp>  
```  
  
 No código gerenciado, você pode adicionar uma etapa de pós\-compilação como este:  
  
```  
regasm /tlb MyAssembly.dll  
```  
  
## Consulte também  
 [Usando e fornecer serviços](../extensibility/using-and-providing-services.md)   
 [Conceitos básicos do serviço](../extensibility/internals/service-essentials.md)