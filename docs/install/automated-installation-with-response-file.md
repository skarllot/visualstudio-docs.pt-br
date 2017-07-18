---
title: "Automatizar a instalação do Visual Studio com um arquivo de resposta | Microsoft Docs"
description: "{{ESPAÇO RESERVADO}}"
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 448C738E-121F-4B64-8CA8-3BC997817A14
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: c77f0321e50a27635e083d656cf6ba8011a4ef4d
ms.contentlocale: pt-br
ms.lasthandoff: 05/11/2017

---
# <a name="how-to-define-settings-in-a-response-file"></a>Como definir as configurações em um arquivo de resposta
Os administradores que implantam o Visual Studio podem especificar um arquivo de resposta usando o parâmetro `--in`; por exemplo:

```
vs_enterprise.exe --in customInstall.json
```

Os arquivos de resposta são arquivos [JSON](http://json-schema.org/) cujo conteúdo espelha os argumentos de linha de comando.  Em geral, se um parâmetro de linha de comando não usa nenhum argumento (por exemplo, `--quiet`, `--passive` etc.), o valor no arquivo de resposta deve ser verdadeiro/falso.  Se for necessário um argumento (por exemplo, `--installPath <dir>`), o valor no arquivo de resposta deverá ser uma cadeia de caracteres.  Se for necessário um argumento e ele puder aparecer mais de uma vez na linha de comando (por exemplo, `--add <id>`), deverá ser uma matriz de cadeias de caracteres.

Os parâmetros especificados na linha de comando substituem as configurações do arquivo de resposta, exceto no caso de parâmetros que usam várias entradas (por exemplo, `--add`), em que as entradas fornecidas na linha de comando são mescladas com as configurações do arquivo de resposta.

# <a name="setting-a-default-configuration-for-visual-studio"></a>Definir uma configuração padrão para o Visual Studio

Se você tiver criado um cache de layout de rede com o `--layout`, um arquivo `response.json` inicial será criado no layout.

Os administradores que criam um layout podem modificar o arquivo `response.json` no layout para controlar as configurações padrão que os usuários verão quando instalarem o Visual Studio do layout.  Por exemplo, se um administrador quiser que cargas de trabalho específicas e componentes selecionados sejam instalado por padrão, poderá configurar o arquivo `response.json` para adicioná-los.

Quando a instalação do Visual Studio for executada em uma pasta de layout, usará _automaticamente_ o arquivo de resposta na pasta do layout.  Não é necessário usar a opção `--in`.

Você pode atualizar o arquivo `response.json` criado em uma pasta de layout offline para definir a configuração padrão para usuários que instalam com esse layout. **No entanto, é fundamental que você deixe as propriedades existentes que foram definidas quando o layout foi criado.**

O arquivo `response.json` base em um layout será semelhante a este, mas com o valor para o produto e o canal que você está instalando:

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

## <a name="example-layout-response-file-content"></a>Conteúdo de arquivo de resposta de layout de exemplo
Este exemplo instalará o Visual Studio Enterprise com seis cargas de trabalho e componentes, com os idiomas inglês e francês da interface do usuário comum. Você pode usar isso como um modelo. Apenas altere as cargas de trabalho e os componentes para as pessoas que você deseja que façam a instalação.

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2017",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```
## <a name="see-also"></a>Consulte também
* [IDs de carga de trabalho e de componente do Visual Studio 2017](workload-and-component-ids.md)

