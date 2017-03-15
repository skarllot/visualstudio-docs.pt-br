---
title: Anatomia de um pacote VSIX | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 15
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
ms.sourcegitcommit: 7278fb37984b92a6a07823c552db5c59a446d0d2
ms.openlocfilehash: 633db03670180ac83c5c936f66953fb38d4ebd67
ms.lasthandoff: 02/22/2017

---
# <a name="anatomy-of-a-vsix-package"></a>Anatomia de um pacote VSIX
Um pacote VSIX é um arquivo. VSIX que contém uma ou mais extensões do Visual Studio, juntamente com o Visual Studio usa para classificar e instalar as extensões de metadados. Esses metadados estão contidos no manifesto VSIX e arquivo [Content_Types]. XML. Um pacote VSIX também pode conter um ou mais arquivos de Extension.vsixlangpack para fornecer um texto de instalação localizada e pode conter pacotes VSIX adicionais para instalar dependências.  
  
 O formato de pacote VSIX segue o padrão Open Packaging Conventions (OPC). O pacote contém binários e arquivos de suporte, junto com um arquivo do [Content_Types]. XML e um arquivo. VSIX arquivo de manifesto. Um pacote VSIX pode conter a saída de vários projetos, ou até mesmo vários pacotes que têm suas próprias manifestos.  
  
> [!NOTE]
>  Os nomes dos arquivos incluídos em pacotes VSIX não devem incluir espaços nem caracteres reservados em identificadores de URI (Uniform Resource), como definido em [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>O manifesto VSIX  
 O manifesto VSIX contém informações sobre a extensão a ser instalado e segue o esquema VSX. Para obter mais informações, consulte [VSIX extensão esquema 1.0 referência](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Para um manifesto do VSIX de exemplo, consulte [PackageManifest elemento (elemento raiz, esquema de VSX)](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 O manifesto VSIX deve ser nomeado `extension.vsixmanifest` quando ele é incluído em um arquivo. VSIX.  
  
## <a name="the-content"></a>O conteúdo  
 Um pacote VSIX pode conter itens de caixa de ferramentas, modelos, os VSPackages ou qualquer outro tipo de extensão com suporte pelo Visual Studio.  
  
## <a name="language-packs"></a>Pacotes de Idiomas  
 Um pacote VSIX pode conter uma vez ou mais arquivos de Extension.vsixlangpack para fornecer texto localizado durante a instalação. Para obter mais informações, consulte [Localizando pacotes VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Dependências e referências  
 Um pacote VSIX pode conter outros pacotes VSIX como referências. Cada um desses outros pacotes deve incluir seu próprio manifesto VSIX.  
  
 Se um usuário tenta instalar uma extensão que tenha dependências, o instalador verifica se os assemblies necessários estão instalados no sistema do usuário. Se os assemblies necessários não forem encontrados, **extensões e atualizações** exibe uma lista dos assemblies ausentes.  
  
 Se o manifesto de extensão inclui um ou mais [referência](http://msdn.microsoft.com/en-us/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) elementos, **extensões e atualizações** compara o manifesto de cada referência para as extensões que estão instalados no sistema e instala a extensão referenciada se ele já não estiver instalado. Se uma versão anterior de uma extensão referenciada estiver instalada, a versão mais recente substitui-lo.  
  
 Se um projeto em uma solução multiprojeto inclui uma referência a outro projeto na mesma solução, o pacote VSIX inclui as dependências do projeto. Você pode substituir esse comportamento clicando-se a referência para o projeto interno e, no **propriedades** janela, definindo o **saída grupos incluídos na VSIX** propriedade `BuiltProjectOutputGroup`.  
  
 Para incluir as DLLs satélite de assemblies referenciados no pacote VSIX, adicione `SatelliteDllsProjectOutputGroup` para o **saída grupos incluídos na VSIX** propriedade.  
  
## <a name="installation-location"></a>Local de instalação  
 Durante a instalação, **extensões e atualizações** procura o conteúdo do pacote VSIX em uma pasta em % LocalAppData%\Microsoft\VisualStudio\14.0\Extensions.  
  
 Por padrão, a instalação se aplica apenas ao usuário atual, pois % LocalAppData % é um diretório específico do usuário. No entanto, se você definir o [AllUsers](http://msdn.microsoft.com/en-us/ac817f50-3276-4ddb-b467-8bbb1432455b) elemento do manifesto para `True`, a extensão será instalada em... \\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions e estará disponível para todos os usuários do computador.  
  
## <a name="contenttypesxml"></a>[Content_Types]. XML  
 Arquivo [Content_Types]. XML identifica os tipos de arquivo no arquivo. VSIX expandido. O Visual Studio usa esse arquivo durante a instalação do pacote, mas não instala o arquivo propriamente dito. Para obter mais informações sobre esse arquivo, consulte [a estrutura do arquivo [Content_types]. XML](the-structure-of-the-content-types-dot-xml-file.md).  
  
 Um arquivo do [Content_Types]. XML é necessária, o Open Packaging Conventions (OPC) padrão. Para obter mais informações sobre OPC, consulte [OPC: um novo padrão de empacotamento seus dados](http://go.microsoft.com/fwlink/?LinkID=148207) no site do MSDN.
