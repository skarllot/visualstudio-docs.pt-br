---
title: Funcionalidades do Dotfuscator | Microsoft Docs
ms.date: 2017-02-08
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
description: "Conheça as funcionalidades do Dotfuscator Community Edition gratuito incluído no Visual Studio 2017."
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
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
translationtype: Human Translation
ms.sourcegitcommit: 507ff049dae50698d86e1536ed21ab982da1af85
ms.openlocfilehash: fb277e75054f27cbe475acdd21ef4771fbdcde40
ms.lasthandoff: 02/22/2017

---

# <a name="capabilities-of-dotfuscator"></a>Funcionalidades do Dotfuscator

Esta página apresenta as funcionalidades do Dotfuscator CE (Dotfuscator Community Edition) com algumas referências às opções avançadas disponíveis por meio de [atualizações][upgrades].

O Dotfuscator é um sistema *pós-build* para aplicativos .NET.
Com o Dotfuscator CE, os usuários do Visual Studio podem [ofuscar assemblies][obfuscation] e injetar [defesa ativa][checks] e [acompanhamento de análise][analytics] no aplicativo – tudo sem que o Dotfuscator precise acessar o código-fonte original.
O Dotfuscator protege seu aplicativo de várias maneiras, criando uma estratégia de proteção em camadas.

O Dotfuscator CE dá suporte a uma ampla variedades de tipos de assembly e de aplicativo do .NET, incluindo [UWP (Plataforma Universal do Windows)][uwp] e [Xamarin][xamarin].

## <a name="intellectual-property-protection"></a>Proteção de propriedade intelectual

O design, o comportamento e a implementação do aplicativo são formas de IP (propriedade intelectual).
No entanto, os aplicativos criados para o .NET Framework são basicamente manuais abertos; é muito fácil executar engenharia reversa dos assemblies do .NET, [pois eles contêm metadados de alto nível e código intermediário][assemblies].

O Dotfuscator CE inclui a [ofuscação básica do .NET][obfuscation] na forma de [renomeação][renaming].
A ofuscação do código com o Dotfuscator reduz o risco de acesso não autorizado ao código-fonte por meio de engenharia reversa, já que informações importantes de nomenclatura deixarão de ser públicas.
A ofuscação também mostra um esforço de sua parte em proteger o código contra o exame – uma etapa importante em estabelecer que sua IP é legalmente protegida como segredo comercial.

Vários dos [recursos de proteção de integridade do aplicativo](#application-integrity-protection) do Dotfuscator CE impedem ainda mais a engenharia reversa.
Por exemplo, um ator mal-intencionado pode tentar anexar um depurador a uma instância em execução do aplicativo para entender a lógica do programa.
O Dotfuscator pode injetar um [comportamento antidepuração][debug] no aplicativo para impedir isso.

## <a name="application-integrity-protection"></a>Proteção de integridade do aplicativo

Além de proteger o código-fonte, também é importante garantir que o aplicativo seja usado como projetado.
Os invasores podem tentar sequestrar o aplicativo para contornar políticas de licenciamento (ou seja, pirataria de software), roubar ou manipular dados confidenciais tratados pelo aplicativo ou alterar o comportamento do aplicativo.

O Dotfuscator CE pode injetar um [código de validação do aplicativo][checks] nos assemblies, incluindo medidas de [antiadulteração][tamper] e [antidepuração][debug].
Quando um estado de aplicativo inválido é detectado, o código de validação pode [chamar o código do aplicativo para resolver a situação de maneira apropriada][check-app].
Ou se preferir não escrever o código para manipular usos inválidos do aplicativo, o Dotfuscator também poderá injetar [relatórios de telemetria][check-telemetry] e comportamentos de [resposta][check-action], sem precisar modificar o código-fonte.

Muitos desses mesmos métodos também podem ser usados para impor [datas limite de fim da vida útil][shelflife] para avaliação ou software de avaliação.

## <a name="application-monitoring"></a>Monitoramento de aplicativos

Ao desenvolver um aplicativo, é fundamental entender os padrões de comportamento dos usuários, incluindo os testadores de versões beta e os usuários de versões anteriores.
A análise do aplicativo permite acompanhar a frequência com que o aplicativo é usado e como ele é usado, incluindo erros que os clientes recebem.

O Dotfuscator CE pode injetar um código de [acompanhamento de exceção][exceptions], [acompanhamento de sessão][sessions] e [acompanhamento de recurso][features] no aplicativo.
Quando executado, o aplicativo processado transmitirá dados de análise para um [ponto de extremidade do PreEmptive Analytics][endpoints] configurado.

## <a name="see-also"></a>Consulte também

[Este tópico no Guia do Usuário completo do Dotfuscator CE][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]: https://docs.microsoft.com/en-us/dotnet/articles/standard/assembly-format
[uwp]: https://www.preemptive.com/blog/article/856-uwp-applications-in-dotfuscator-ce/91-dotfuscator-ce
[xamarin]: https://www.preemptive.com/obfuscating-xamarin-with-dotfuscator

[upgrades]: upgrades.md

[obfuscation]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/obfuscation_overview.html
[renaming]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/obfuscation_renaming.html

[analytics]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/analytics_overview.html
[endpoints]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/analytics_overview.html#endpoints

[checks]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/checks_overview.html
[check-app]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/checks_overview.html#app-notification
[check-action]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/checks_overview.html#action

[tamper]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/checks_tamper.html
[debug]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/checks_debug.html
[shelflife]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/checks_shelflife.html
[exceptions]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/analytics_exceptions.html
[sessions]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/analytics_sessions.html
[features]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/analytics_features.html
[check-telemetry]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/analytics_checks.html

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/intro_capabilities.html
