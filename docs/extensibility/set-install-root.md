---
title: "Instalando fora da pasta extensões com VSIX v3 | Documentos do Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
caps.latest.revision: 1
author: gregvanl
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
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 6d87c86d0a7793f661c6a3b28e95340f3a28c616
ms.lasthandoff: 03/07/2017

---
# <a name="installing-outside-the-extensions-folder"></a>Instalando fora da pasta de extensões

Começando com o Visual Studio 2017 e VSIX v3 (versão 3), há agora oferecem suporte para instalar os ativos de extensão fora da pasta extensões. Atualmente, os seguintes locais são habilitados como locais de instalação válida (onde [installdir] é mapeado para o diretório de instalação da instância do Visual Studio):

* \Common7\IDE\PublicAssemblies [installdir]
* \Common7\IDE\ReferenceAssemblies [installdir]
* \MSBuild [installdir]
* \Schemas [installdir]
* \Licenses [installdir]
* \RemoteDebugger [installdir]
* \VSTargets [installdir]

>**Observação:** o formato do VSIX não permitem que você instale fora da estrutura de pasta de instalação do VS.

Para suportar a instalação para esses diretórios, VSIX deve ser instalado "por instância por máquina". Isso pode ser habilitado, marcando a caixa de seleção "todos os usuários" no designer de vsixmanifest:

![Verifique todos os usuários](~/docs/extensibility/media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Como definir a Raiz_da_instalação

Para definir os diretórios de instalação, você pode usar o **propriedades** janela no Visual Studio. Por exemplo, você pode definir o `InstallRoot` propriedade de uma referência de projeto para um dos locais acima:

![instalar propriedades raiz](~/docs/extensibility/media/install-root-properties.png)

Isso irá adicionar alguns metadados para os respectivos `ProjectReference` propriedade dentro do arquivo do projeto VSIX. csproj:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**Observação:** é possível editar o arquivo. csproj diretamente, se preferir.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Como definir um subcaminho sob o Raiz_da_instalação

Se você gostaria de instalar um subcaminho sob o `InstallRoot`, você pode fazer isso definindo o `VsixSubPath` propriedade assim o `InstallRoot` propriedade. Por exemplo, digamos que queremos que a saída da nossa referência de projeto para instalar ' [installdir]\MSBuild\MyCompany\MySDK\1.0'. Podemos fazer isso facilmente com o designer de propriedade:

![subcaminho de conjunto](~/docs/extensibility/media/set-subpath.png)

As alterações. csproj correspondentes terá esta aparência:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Informações adicionais

As alterações de propriedade designer se aplicam a mais do que apenas referências do projeto; Você pode definir o `InstallRoot` metadados para os itens dentro de seu projeto também (usando os métodos descritos acima).

