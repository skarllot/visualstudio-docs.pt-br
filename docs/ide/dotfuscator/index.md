---
title: Dotfuscator CE (Community Edition) | Microsoft Docs
ms.date: 2017-06-22
ms.prod: visual-studio-dev15
ms.devlang: dotnet
ms.technology:
- dotfuscator
ms.topic: article
keywords: "Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, proteção, community edition, ofuscação, .NET, gratuito, Visual Studio 2017"
helpviewer_keywords:
- PreEmptive Protection - Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: "Saiba como você pode proteger seus aplicativos .NET com o Dotfuscator Community Edition incluído gratuitamente no Visual Studio 2017."
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: Joe-Sewell-PreEmptive
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: 15dd6127493b9977732fdb891a086f931e002459
ms.contentlocale: pt-br
ms.lasthandoff: 06/23/2017

---

# <a name="dotfuscator-community-edition-ce"></a>Dotfuscator Community Edition (CE)

*PreEmptive Protection – Dotfuscator* fornece uma proteção abrangente de aplicativos .NET que pode ser adaptada facilmente ao seu ciclo de vida de desenvolvimento seguro de software.
Use-o para otimizar, proteger e remover aplicativos para desktop, móveis, servidores e incorporados, a fim de ajudar a proteger segredos comerciais e outras propriedades intelectuais (IP), reduzir a pirataria e a falsificação e proteger contra violação e depuração não autorizada.
O Dotfuscator funciona em assemblies compilados sem a necessidade de programação adicional ou até mesmo de acesso ao código-fonte.

![](media/header.svg)

## <a name="why-protection-matters"></a>Por que a proteção é importante

É importante **proteger sua propriedade intelectual** (IP).
O código do seu aplicativo contém detalhes de design e implementação que podem ser considerados IP.
No entanto, os aplicativos compilados no .NET Framework [contêm metadados significativos e código intermediário de alto nível][assemblies], facilitando muito a engenharia reversa apenas usando uma das muitas ferramentas automatizadas e gratuitas.
Ao interromper e parar a engenharia reversa, você pode evitar divulgação não autorizada de IP, bem como demonstrar que seu código contém segredos comerciais.
O Dotfuscator pode [ofuscar][obfuscation] seus assemblies .NET para atrapalhar a engenharia reversa, mantendo o comportamento do aplicativo original.

Também é importante **proteger a integridade do seu aplicativo**.
Além da engenharia reversa, atores ruins podem tentar piratear seu aplicativo, alterar o comportamento do aplicativo no tempo de execução ou manipular dados.
O Dotfuscator pode injetar em seu aplicativo a capacidade de [detectar, relatar e responder a usuários não autorizados][checks], incluindo violação e depuração de terceiros.

Para saber mais sobre como o Dotfuscator se encaixa em um ciclo de vida de desenvolvimento seguro de software, veja a página [Proteção de aplicativo do SDL][sdl-protection] da PreEmptive Solutions.

## <a name="about-dotfuscator-ce"></a>Sobre o Dotfuscator CE

Sua cópia do Microsoft Visual Studio 2017 inclui uma cópia do ***PreEmptive Protection – Dotfuscator* Community Edition**, também conhecido como Dotfuscator CE, gratuito para uso pessoal.
Para obter instruções sobre como instalar a versão do Dotfuscator CE incluída no Visual Studio 2017, veja a [página Instalação][install].

O Dotfuscator CE oferece vários [softwares de proteção e serviços de][software-protection] otimização para desenvolvedores, arquitetos e testadores.
Exemplos de [ofuscação de .NET][obfuscation] e outros recursos de [Proteção de aplicativo][app-protection] incluídos no Dotfuscator CE:

* *[Renomeação][renaming]* de identificadores para dificultar a engenharia reversa de assemblies compilados.
* *[Antiviolação][tamper]* para detectar a execução de aplicativos violados, transmitir alertas de incidentes e encerrar sessões violadas.
* *[Antidepuração][debug]* para detectar a anexação de um depurador a um aplicativo em execução, transmissão de alertas de incidentes e encerramento de sessões depuradas.
* *[Comportamentos de expiração do aplicativo][shelflife]* que codifica uma data de "fim da vida", transmite alertas quando os aplicativos são executados após a data de vencimento e encerra sessões do aplicativo que expirou.
* *[Acompanhamento de exceção][exceptions]* para monitorar as exceções sem tratamento que ocorrem dentro do aplicativo.
* Acompanhamento de uso de *[Sessão][sessions] e [recurso][features]* para determinar quais aplicativos foram executados, quais versões e quais recursos são usados nesses aplicativos.

Para obter detalhes sobre esses recursos, incluindo como eles se encaixam em sua estratégia de proteção do aplicativo, veja a [página Recursos][capabilities].

O Dotfuscator CE oferece proteção básica de forma nativa.
Há ainda mais medidas de proteção do aplicativo disponíveis para usuários registrados do Dotfuscator CE e para os usuários do *PreEmptive Protection - Dotfuscator* Professional Edition, o principal [Ofuscador .NET][net-obfuscator] do mundo.
Para saber mais sobre como melhorar o Dotfuscator, veja a [página Atualizações][upgrades].

## <a name="getting-started"></a>Guia de Introdução

Para começar a usar o Dotfuscator CE no Visual Studio, digite `dotfuscator` na barra de pesquisa **Início Rápido** (Ctrl+Q).

* Se o Dotfuscator CE já estiver instalado, a opção *Menu* será exibida para iniciar a interface de usuário do Dotfuscator CE. Para obter detalhes, veja [a página de Introdução do guia do usuário completo do CE Dotfuscator][get-started].
* Se o Dotfuscator CE ainda não estiver instalado, a opção *Instalar* relevante será exibida. Consulte a [página Instalação][install] para obter detalhes.

Você também pode obter a **versão mais recente** do Dotfuscator CE na [página de Downloads do Dotfuscator em preemptive.com][download].

## <a name="full-documentation"></a>Documentação completa

Esta página e suas subpáginas fornecem uma visão geral de alto nível dos recursos do Dotfuscator CE, bem como [instruções para instalar a ferramenta][install].

Veja [o guia de usuário completo do Dotfuscator CE em preemptive.com][full] para obter instruções detalhadas de uso, incluindo [como começar a usar a interface de usuário do Dotfuscator CE][get-started].

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]: https://docs.microsoft.com/en-us/dotnet/standard/assembly-format
[software-protection]: https://www.preemptive.com/software-protection
[obfuscation]: https://www.preemptive.com/obfuscation
[app-protection]: https://www.preemptive.com/application-protection
[sdl-protection]: https://www.preemptive.com/solutions/SDL-App-Protection
[net-obfuscator]: https://www.preemptive.com/products/dotfuscator/overview
[download]: https://www.preemptive.com/products/dotfuscator/downloads

[install]: install.md
[capabilities]: capabilities.md
[upgrades]: upgrades.md

[get-started]: https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[renaming]: https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[tamper]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[shelflife]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[exceptions]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_exceptions.html
[sessions]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_sessions.html
[features]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_features.html

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/index.html

