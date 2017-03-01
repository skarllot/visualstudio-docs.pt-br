---
title: Componente de gerenciamento | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 13
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
ms.openlocfilehash: d6ca710cbd582a4f23a23aa0fb14aa6c526490ff
ms.lasthandoff: 02/22/2017

---
# <a name="component-management"></a>Gerenciamento de componente
Unidades de tarefas no Windows Installer são chamadas de componentes do Windows Installer (às vezes chamados WICs ou apenas componentes). Um GUID que identifica cada WIC, que é a unidade básica de instalação e para instalações que usam o Windows Installer de contagem de referência.  
  
 Embora você possa usar vários produtos para criar seu instalador VSPackage, esta discussão pressupõe o uso de arquivos do Windows Installer (. msi). Ao criar seu instalador, você deve gerenciar corretamente implantação de arquivos para que a contagem de referência correto ocorre em todos os momentos. Consequentemente, diferentes versões do produto não interferir ou quebrará uns aos outros em uma combinação de instalar e desinstalar cenários.  
  
 No Windows Installer, a contagem de referência ocorre no nível do componente. Você deve organizar cuidadosamente os recursos — arquivos, entradas do registro e assim por diante — em componentes. Existem outros níveis de organização, como produtos, recursos e módulos — que podem ajudar em cenários diferentes. Para obter mais informações, consulte [Noções básicas do Windows Installer](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Diretrizes de criação de instalação lado a lado  
  
-   Arquivos do autor e chaves do registro que são compartilhadas entre as versões em seus próprios componentes.  
  
     Isso permite que você facilmente consumi-los na próxima versão. Por exemplo, as bibliotecas de tipos que são registradas globalmente, arquivo extensões, outros itens registrados em HKEY_CLASSES_ROOT e assim por diante.  
  
-   Agrupe os componentes compartilhados em módulos de mesclagem separada.  
  
     Isso ajuda você autor corretamente para lado a lado no futuro.  
  
-   Instale arquivos compartilhados e chaves do registro usando os mesmos componentes do Windows Installer entre versões.  
  
     Se você usar um componente diferente, arquivos e entradas do registro são desinstaladas quando um VSPackage com controle de versão é desinstalado, mas o VSPackage outro ainda está instalado.  
  
-   Não misture itens com controle de versão e compartilhados no mesmo componente.  
  
     Isso torna impossível instalar itens compartilhados em um local global e itens com controle de versão para locais isolados.  
  
-   Não tiver chaves do registro compartilhado que apontam para arquivos com controle de versão.  
  
     Nesse caso, as chaves pré-compartilhadas serão substituídas quando outro VSPackage com controle de versão está instalada. Depois de remover a segunda versão, o arquivo ao qual a chave está apontando desapareceu.  
  
## <a name="see-also"></a>Consulte também  
 [Escolhendo entre os VSPackages compartilhados e controle de versão](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Cenários de instalação de VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)
