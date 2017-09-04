---
title: "Ações de Build"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 347378da197b5c6d22bbd145c2ac8673d53a63bf
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---

# <a name="build-actions"></a>Ações de Build 

Todos os arquivos em um projeto do Visual Studio para Mac tem uma ação de build que controla o que acontece com o arquivo durante um build. Elas podem ser definidas clicando com o botão direito do mouse em qualquer arquivo e navegando para **Ação de Build**, conforme ilustrado abaixo:

![](media/projects-and-solutions-image1.png)

Algumas das ações de build comuns para projetos C# são:

* **None** – O arquivo não faz parte do build de nenhuma forma, sendo incluído no projeto para fácil acesso do IDE.
* **Compile** – O arquivo será passado para o compilador C# como um arquivo de origem.
* **EmbeddedResource** – O arquivo será passado para o compilador C# como um recurso a ser inserido no assembly. O namespace `System.Reflection` pode ser usado para ler o arquivo do assembly.
* **Content** – Para projetos ASP.NET, esses arquivos serão incluídos como parte do site quando ele for implantado. Para projetos Xamarin.iOS e Xamarin.Mac, eles estarão contidos no lote de aplicativo.

É possível selecionar mais de um arquivo no gerenciador de Soluções, permitindo que você defina a ação de build para vários arquivos ao mesmo tempo.

Além disso, há ações de build para projetos específicos. Por exemplo, projetos Xamarin.iOS têm a ação de build **BundeledResource**, que adiciona o arquivo como parte do lote de aplicativo. Informações sobre as ações de build específicas do Xamarin.Android podem ser encontradas no guia de [processo de build](https://developer.xamarin.com/guides/android/under_the_hood/build_process/#Build_Actions) em developer.xamarin.com.
