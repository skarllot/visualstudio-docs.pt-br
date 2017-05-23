---
title: "Exemplos de parâmetros de linha de comando para a instalação do Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
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
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 0f07824b29e7851e353d472838a897853e227d6c
ms.contentlocale: pt-br
ms.lasthandoff: 05/09/2017

---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Exemplos de parâmetros de linha de comando para a instalação do Visual Studio 2017
Para ilustrar como [usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md), aqui estão vários exemplos que podem ser personalizados para atender às suas necessidades.

Em cada exemplo, `vs_enterprise.exe`, `vs_professional.exe` e `vs_community.exe` representam a respectiva edição do bootstrapper do Visual Studio, que é o arquivo pequeno (aproximadamente 1 MB) que inicia o processo de download. Se você estiver usando uma edição diferente, substitua o nome do bootstrapper adequado.

> [!NOTE]
> Todos os comandos exigem elevação administrativa e um prompt do Controle de Conta de Usuário será exibido se o processo não for iniciado em um prompt elevado.

> [!NOTE]
>  Você pode usar o caractere `^` no final de uma linha de comando para concatenar várias linhas em um único comando. Como alternativa, é possível simplesmente colocar essas linhas juntas em uma única linha. No PowerShell, o equivalente é o caractere de acento grave (`` ` ``). 

* Instale uma instância mínima do Visual Studio, com nenhum prompt interativo, com exceção do progresso, exibido:
```
vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
```

* Instale silenciosamente, uma instância da área de trabalho do Visual Studio com o pacote de idioma francês, retornando somente quando o produto estiver instalado.
```
vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
```

> [!NOTE]
>  O parâmetro `--wait` é projetado para uso em um arquivo em lotes. Em um arquivo em lotes, a execução do próximo comando não continuará até que a instalação seja concluída. A variável de ambiente `%ERRORLEVEL%` contém o valor retornado do comando, conforme documentado na página [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

* Baixe o editor de núcleo do Visual Studio (a configuração mínima do Visual Studio). Inclua apenas o pacote de idiomas em inglês:

```cmd
vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
```

* Baixe as cargas de trabalho do .NET desktop e do .NET web juntamente com todos os componentes recomendados e com a extensão do GitHub. Inclua apenas o pacote de idiomas em inglês:
```
vs_community.exe --layout C:\VS2017 ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
```

* Inicie uma instalação interativa de todas as cargas de trabalho e componentes que estão disponíveis no Visual Studio 2017 Enterprise edition:
```
vs_enterprise.exe --all --includeRecommended --includeOptional
```

* Instale uma segunda instância nomeada do Visual Studio 2017 Professional em um computador com Visual Studio 2017 Community edition já instalado, com suporte para o desenvolvimento do Node.js:
```
vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
```

* Remova o componente Ferramentas de Criação de Perfil da instância do Visual Studio instalada por padrão:
```
vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
```

## <a name="see-also"></a>Consulte também

 * [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
 * [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Criar uma instalação offline do Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)

