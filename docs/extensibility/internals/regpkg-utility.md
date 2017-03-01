---
title: "Utilitário de RegPkg | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 12
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
ms.openlocfilehash: 5975f2c27d5e99a9b5e44e6e0177c235823cfad7
ms.lasthandoff: 02/22/2017

---
# <a name="regpkg-utility"></a>Utilitário de RegPkg
> [!NOTE]
>  É a melhor maneira de registrar pacotes no Visual Studio usando arquivos. pkgdef. Isso possibilita a implantação de extensão sem precisar acessar o registro do sistema, que é um requisito para a implantação do VSIX. Pkgdef arquivos são criados usando o [CreatePkgDef utilitário](../../extensibility/internals/createpkgdef-utility.md). Para obter mais informações sobre implantação de pacote do Visual Studio, consulte [envio extensões do Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 O utilitário RegPkg.exe registra um VSPackage com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e prepará-lo para implantação. Esse utilitário é usado em segundo plano durante o desenvolvimento de VSPackage. Ele é executado como parte do processo de compilação para que você pode compilar e executar um VSPackage no hive experimental.  
  
 RegPkg pode gerar scripts de registro do sistema em vários formatos. Você pode incorporar esses scripts em projetos de implantação, como arquivos de conjunto de ferramentas XML do Windows Installer ou projetos. msi.  
  
 RegPkg.exe normalmente está localizado em \< *caminho de instalação do SDK do Visual Studio*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg segue esta sintaxe:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root:root  
 Executa o registro em especificado  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]raiz.  
  
 /regfile:filename  
 Cria um arquivo. reg em vez de atualizar o registro.  Não pode ser usado com /vrgfile ou /rgsfile ou /wixfile.  
  
 /rgsfile:filename  
 Cria um arquivo. rgs em vez de atualizar o registro.  Não pode ser usado com /vrgfile ou /regfile ou /wixfile.  
  
 /vrgfile:filename  
 Cria um arquivo .vrg em vez de atualizar o registro.  Não pode ser usado com /regfile ou /rgsfile ou /wixfile.  
  
 /rgm  
 Cria um arquivo .rgm além do arquivo rgs.  Deve ser combinada com /rgsfile.  
  
 /wixfile:filename  
 Cria um arquivo compatível com o conjunto de ferramentas XML do Windows Installer em vez de atualizar o registro.  Não pode ser usado com /regfile ou /rgsfile ou /vrgfile.  
  
 /codebase  
 Registro de força com base de código em vez de Assembly.  
  
 /assembly  
 Registro de força com Assembly em vez de base de código.  
  
 /unregister  
 Cancela o registro deste pacote.  Não pode ser usado  
  
 com /regfile ou /vrgfile ou /rgsfile ou /wixfile.  
  
## <a name="see-also"></a>Consulte também  
 [Liberar um produto](../../misc/releasing-a-visual-studio-integration-product.md)   
 [Solucionando problemas de registro de pacote RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
