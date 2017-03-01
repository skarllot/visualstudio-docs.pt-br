---
title: "Práticas recomendadas para segurança no VSPackages | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 19
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c7ceb884ad060ea45c0fd204b5611ce284d3d2af
ms.lasthandoff: 02/22/2017

---
# <a name="best-practices-for-security-in-vspackages"></a>Práticas recomendadas de segurança em VSPackages
Para instalar o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] no seu computador, você deve estar executando em um contexto com credenciais administrativas. A unidade básica de segurança e a implantação de um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aplicativo é o [VSPackages](../../extensibility/internals/vspackages.md). Um VSPackage deve ser registrado com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], que também requer credenciais administrativas.  
  
 Os administradores têm permissões completas para gravar no registro e sistema de arquivos e para executar qualquer código. Você deve ter essas permissões para desenvolver, implantar ou instalar um VSPackage.  
  
 Assim que ele for instalado, um VSPackage é totalmente confiável. Devido a esse nível alto de permissão associada a um VSPackage, é possível instalar inadvertidamente um VSPackage com más intenções.  
  
 Os usuários devem garantir que eles instalam os VSPackages somente de fontes confiáveis. As empresas a desenvolver os VSPackages fortemente devem nomear e assiná-los garantir que o usuário que a violação é impedida. As empresas a desenvolver os VSPackages devem examinar suas dependências externas, como serviços da web e de instalação remota, avaliar e corrigir quaisquer problemas de segurança.  
  
 Para obter mais informações, consulte diretrizes para codificação segura para o .NET Framework ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>Consulte também  
 [Segurança do suplemento](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [Segurança DDEX](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)
