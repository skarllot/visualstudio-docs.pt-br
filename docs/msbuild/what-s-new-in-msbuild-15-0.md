---
title: Novidades no MSBuild 15 | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
caps.latest.revision: 23
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
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 620d5739c450ddece13257bf7efa249ebf9c2a6a
ms.lasthandoff: 03/07/2017

---
# <a name="whats-new-in-msbuild-15"></a>Novidades no MSBuild 15
Agora o MSBuild está disponível como parte do [SDK do .NET Core](https://www.microsoft.com/net/download/core) e pode compilar projetos do .NET Core no Windows, macOS e Linux.  

## <a name="changed-path"></a>Caminho alterado
 Agora o MSBuild é instalado em uma pasta em cada versão do Visual Studio. Por exemplo, `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild`. Você também pode usar o seguinte módulo do PowerShell para localizar o MSBuild: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

 O MSBuild não é mais instalado no Cache de Assembly Global. Para referenciar o MSBuild de forma programática, use pacotes NuGet.

## <a name="changed-properties"></a>Propriedades alteradas  
 As propriedades do MSBuild a seguir foram atualizadas devido ao novo número de versão.  

-   A `MSBuildToolsVersion` desta versão das ferramentas é 15.0. A versão de assembly é 15.1.0.0.

-   `MSBuildToolsPath` não tem mais uma localização fixa. Por padrão, ele está localizado na pasta MSBuild\15.0\Bin relativa à localização de instalação do Visual Studio, mas ela pode ser alterada em tempo de instalação.

-   Os valores `ToolsVersion` não são mais definidos no Registro.  

-   As propriedades `SDK35ToolsPath` e `SDK40ToolsPath` apontam para o SDK do .NET Framework que é empacotado com esta versão do Visual Studio (por exemplo, 10.0A para as ferramentas 4.X).  

## <a name="updates"></a>Atualizações
- O [elemento Project](../msbuild/project-element-msbuild.md) tem um novo atributo `SDK`. Além disso, agora o atributo `Xmlns` é opcional.
- O [Elemento Item](../msbuild/item-element-msbuild.md) fora dos destinos tem um novo atributo `Update`. Além disso, a restrição no atributo `Remove` foi eliminada.
- `Directory.Build.props` é um arquivo definido pelo usuário que fornece personalizações para projetos em um diretório. Esse arquivo é importado automaticamente de Microsoft.Common.props, a menos que a propriedade `ImportDirectoryBuildTargets` seja definida como **false**. `Directory.Build.targets` é importado por Microsoft.Common.targets.
- Os metadados com um nome que não entra em conflito com a lista atual de atributos, opcionalmente, podem ser expressos como um atributo. Para obter mais informações, consulte [Elemento Item](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Novas funções de propriedade

- `EnsureTrailingSlash` adiciona uma barra à direita a um caminho, se ainda não houver um.
- `NormalizePath` combina elementos de caminho e garante que a cadeia de caracteres de saída tem os caracteres separadores de diretório corretos do sistema operacional atual.
- `NormalizeDirectory` combina elementos de caminho, garante uma barra à direita e garante que a cadeia de caracteres de saída tem os caracteres separadores de diretório corretos do sistema operacional atual.
- `GetPathOfFileAbove` retorna o caminho do arquivo imediatamente anterior a esse. É funcionalmente equivalente a chamar `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>Consulte também
[MSBuild](../msbuild/msbuild.md)

