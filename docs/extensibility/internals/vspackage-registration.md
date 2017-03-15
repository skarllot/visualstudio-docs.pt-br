---
title: Registro de VSPackage | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: 18
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
ms.openlocfilehash: bebd023d8cbecf97f75570bf57ed2cd4462ffe92
ms.lasthandoff: 02/22/2017

---
# <a name="vspackage-registration"></a>Registro de VSPackage
Os VSPackages deverá avisar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que eles estão instalados e devem ser carregado. Esse processo é realizado gravando informações no registro. Esse é um trabalho típico de um instalador.  
  
> [!NOTE]
>  É uma prática aceita durante o desenvolvimento de VSPackage para usar o auto-registro. No entanto, [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] parceiros não podem fornecer seus produtos usando o auto-registro como parte da instalação.  
  
 Entradas de registro em um pacote do Windows Installer geralmente são feitas na tabela de registro. Você também pode registrar extensões de arquivo da tabela de registro. No entanto, o Windows Installer fornece suporte interno por meio do identificador programático (ProgId), classe, extensão e tabelas do verbo. Para obter mais informações, consulte [tabelas de banco de dados](http://msdn.microsoft.com/library/aa368259\(VS.85\).aspx).  
  
 Certifique-se de que as entradas do registro estão associadas com o componente que é apropriado para sua estratégia de lado a lado escolhida. Por exemplo, entradas do registro para um arquivo compartilhado devem ser associadas com o componente do Windows Installer do arquivo. Da mesma forma, entradas do registro para um arquivo específico da versão devem ser associadas com o componente do arquivo. Caso contrário, instalar ou desinstalar o VSPackage para uma versão do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pode interromper o VSPackage em outras versões. Para obter mais informações, consulte [suporte a várias versões do Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  A maneira mais fácil de gerenciar o registro é usar os mesmos dados nos mesmos arquivos de registro do desenvolvedor e o registro durante a instalação. Por exemplo, algumas ferramentas de desenvolvimento de instalador podem consumir o arquivo no formato. reg no momento da compilação. Se os desenvolvedores mantêm arquivos. reg para seu próprio desenvolvimento diário e depuração, esses mesmos arquivos podem ser incluídos no instalador automaticamente. Se você não pode compartilhar automaticamente dados de registro, você deve garantir que a cópia do instalador dos dados de registro é atual.  
  
## <a name="registering-unmanaged-vspackages"></a>Registrando os VSPackages não gerenciados  
 Os VSPackages não gerenciados (incluindo aqueles gerados pelo modelo de pacote do Visual Studio) usar arquivos. rgs do estilo ATL para armazenar informações de registro. O formato de arquivo. rgs é específico para ATL e geralmente não pode ser utilizado como-é uma ferramenta de criação de instalação. Informações de registro para o instalador de VSPackage devem ser mantidas separadamente. Por exemplo, os desenvolvedores podem manter arquivos no formato. reg em sincronia com. rgs as alterações de arquivo. Os arquivos. reg podem ser mesclados com RegEdit para o trabalho de desenvolvimento ou consumidos por um instalador.  
  
## <a name="registering-managed-vspackages"></a>Registrando VSPackages gerenciados  
 A ferramenta RegPkg lê os atributos de registro de um VSPackage gerenciado e a gravar as informações diretamente para o registro ou gravar os arquivos no formato. reg que podem ser consumidos por um instalador.  
  
> [!NOTE]
>  A ferramenta RegPkg não é redistribuível e não pode ser usada para registrar um VSPackage no sistema do usuário.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Por que os VSPackages não deve se registrar no momento da instalação  
 Os VSPackage instaladores não devem depender de auto-registro. A princípio, manter os valores de registro do VSPackage apenas o VSPackage próprio parece ser uma boa ideia. Considerando que os desenvolvedores precisam os valores de registro disponíveis para o trabalho de rotina e de teste, faz sentido para evitar manter uma cópia separada dos dados do registro do instalador. O instalador pode depender de VSPackage para gravar valores do registro.  
  
 Embora seja ideal em teoria, auto-registro possui várias falhas que o tornam adequado para a instalação de VSPackage:  
  
-   Suporte corretamente a instalação, desinstalação, reversão da instalação e reversão de desinstalação requer a criação de quatro ações personalizadas para cada VSPackage gerenciado que registra automaticamente chamando RegPkg.  
  
-   Sua abordagem ao suporte lado a lado pode exigir que você crie quatro ações personalizadas que invocam RegSvr32 ou RegPkg para todas as versões com suporte do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Uma instalação com módulos registrados automaticamente não pode ser revertida com segurança porque há uma maneira de dizer se as chaves automaticamente registradas são usadas por outro aplicativo ou recurso.  
  
-   DLLs automaticamente registrados, às vezes, vinculam a DLLs auxiliares que não existem ou estão na versão errada. Por outro lado, o Windows Installer pode registrar DLLs usando as tabelas de registro sem dependência no estado atual do sistema.  
  
-   Código de auto-registro pode ser negado acesso aos recursos de rede, como bibliotecas de tipo, se um componente estiver especificado como executado a partir da origem tanto listado na tabela SelfReg. Isso pode causar a instalação do componente falha durante uma instalação administrativa.  
  
## <a name="see-also"></a>Consulte também  
 [O Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Registro do pacote gerenciado](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
