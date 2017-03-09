---
title: "Números de versão para assemblies satélite principais e localizados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
caps.latest.revision: 12
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: a41d725b9f58d0f434c3f5169d76988b675aa312
ms.lasthandoff: 02/22/2017

---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>Números de versão para assemblies principal e satélite localizados
A classe <xref:System.Resources.SatelliteContractVersionAttribute> fornece suporte ao controle de versão de um assembly principal que usa recursos localizados por meio do gerenciador de recursos. A aplicação de <xref:System.Resources.SatelliteContractVersionAttribute> ao assembly principal de um aplicativo permite atualizar e reimplantar o assembly sem atualizar seus assemblies satélites. Por exemplo, é possível usar a classe <xref:System.Resources.SatelliteContractVersionAttribute> com um service pack que não introduz novos recursos sem recompilar e reimplantar os assemblies satélites. Para que os recursos localizados fiquem disponíveis, a versão do contrato satélite do assembly principal deve corresponder à classe <xref:System.Reflection.AssemblyVersionAttribute> dos assemblies satélites. É necessário especificar um número de versão exato em <xref:System.Resources.SatelliteContractVersionAttribute>; caracteres curinga como “*” não são permitidos. Para obter mais informações, consulte [Recuperando recursos](http://msdn.microsoft.com/Library/eca16922-1c46-4f68-aefe-e7a12283641f).  
  
## <a name="updating-assemblies"></a>Atualizando assemblies  
 A classe <xref:System.Resources.SatelliteContractVersionAttribute> permite atualizar um assembly principal sem a necessidade de atualizar o assembly satélite, ou vice-versa. Quando o assembly principal é atualizado, seu número de versão do assembly é alterado. Se você desejar continuar usando os assemblies satélite existentes, altere o número de versão do assembly principal, mas não altere o número de versão do contrato satélite. Por exemplo, na primeira versão, a versão do assembly principal pode ser 1.0.0.0. A versão do contrato satélite e a versão do assembly satélite também serão 1.0.0.0. Se você precisar atualizar um service pack do assembly principal, é possível alterar a versão do assembly para 1.0.0.1, mantendo a versão do contrato satélite e a versão do assembly satélite como 1.0.0.0.  
  
 Se precisar atualizar um assembly satélite mas não o assembly principal, altere <xref:System.Reflection.AssemblyVersionAttribute> do assembly satélite. Juntamente com o assembly satélite, você precisará enviar um assembly de política que afirma que o novo assembly satélite é compatível com o assembly satélite antigo. Para obter mais informações sobre políticas, consulte [Como o tempo de execução localiza assemblies](http://msdn.microsoft.com/Library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).  
  
 O código a seguir mostra como definir a versão do contrato satélite. O código pode ser colocado em um script de build ou no arquivo AssemblyInfo.vb ou AssemblyInfo.cs.  
  
```vb#  
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>  
  
```  
  
```c#  
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]  
```  
  
## <a name="see-also"></a>Consulte também  
 [Como o tempo de execução localiza assemblies](http://msdn.microsoft.com/Library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34)   
 [Definindo atributos de assembly](http://msdn.microsoft.com/Library/36a98a81-b5b5-4c19-912a-11f91eff7f4e)   
 [Security and Localized Satellite Assemblies](../ide/security-and-localized-satellite-assemblies.md)  (Assemblies satélite de segurança e localizados)  
 [Localizando aplicativos](../ide/localizing-applications.md)   
 [Globalizando e localizando aplicativos](../ide/globalizing-and-localizing-applications.md)
