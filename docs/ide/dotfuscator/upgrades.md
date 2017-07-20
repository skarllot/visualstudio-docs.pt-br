---
title: Atualizar o Dotfuscator CE (Community Edition) | Microsoft Docs
ms.date: 2017-02-08
ms.prod: visual-studio-dev15
ms.devlang: dotnet
ms.technology:
- dotfuscator
ms.topic: article
keywords: "Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, proteção, community edition, ofuscação, .NET, gratuito, Visual Studio 2017, atualização, linha de comando"
helpviewer_keywords:
- PreEmptive Protection - Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: "Saiba como atualizar o Dotfuscator Community Edition gratuito incluído no Visual Studio 2017."
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
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
ms.openlocfilehash: 60ca38639f6523cdbace4efa4aa48b48d5e9a886
ms.contentlocale: pt-br
ms.lasthandoff: 06/23/2017

---

# Atualizar o Dotfuscator CE (Community Edition)
<a id="upgrade-dotfuscator-community-edition-ce" class="xliff"></a>

O Dotfuscator CE (Dotfuscator Community Edition) oferece vários recursos de proteção do aplicativo imediatamente para todos os desenvolvedores que usam o Microsoft Visual Studio.
No entanto, há mais recursos disponíveis aos usuários que atualizam a versão do Dotfuscator.

## Registrando o Dotfuscator CE
<a id="registering-dotfuscator-ce" class="xliff"></a>

Os usuários registrados do Dotfuscator CE obtém acesso a recursos adicionais, como [suporte de linha de comando][cli], o que facilita a integração do Dotfuscator CE no processo de build automatizado.

O registro é rápido, simples e gratuito.
Para registrar o Dotfuscator CE, consulte [a seção Registrando o Dotfuscator CE na página Introdução do Guia do Usuário completo do Dotfuscator CE][register-ce].

## Dotfuscator Professional
<a id="dotfuscator-professional" class="xliff"></a>

Embora o Dotfuscator Community Edition forneça um nível básico de proteção, o **_PreEmptive Protection – Dotfuscator_ Professional Edition** inclui funcionalidades de proteção e transformações de ofuscação avançadas.
Elas incluem:

* *Proteção de propriedade intelectual*
  * Opções de renomeação avançadas, incluindo Enhanced Overload Induction™ e seleção de identificador aleatória.
  * Ferramentas de decodificação de rastreamentos de pilha ofuscados.
  * Acesso a transformações de ofuscação de nível empresarial, incluindo [transformações destinadas a acabar com a descompilação automatizada de código][control-flow].
  * A capacidade de [obscurecer cadeias de caracteres confidenciais][string-encryption], impossibilitando uma pesquisa simples do código descompilado.
  * A capacidade de [inserir discretamente cadeias de caracteres de propriedade e de distribuição nos assemblies][watermarking] (marca-d'água de software), permitindo determinar a origem de perdas de software não autorizadas.
  * A capacidade de [combinar vários assemblies em um][linking], tornando ainda mais difícil para invasores determinar as funções de elementos de código, pois a separação de preocupações foi eliminada.
  * A capacidade de [remover automaticamente o código não utilizado do aplicativo][pruning], reduzindo a quantidade de código confidencial fornecido.
* *Proteção de integridade do aplicativo*
  * [Comportamentos de defesa do aplicativo][check-actions] adicionais.
  * A capacidade de injetar código antiadulteração e antidepuração em assemblies `.dll`.
  * A capacidade de fornecer um período de aviso antes da data limite do fim da vida útil do aplicativo.
  * A capacidade de notificar o código do aplicativo durante um período de aviso do fim da vida útil ou após a data limite.
  * Criptografia de telemetria.
* *Monitoramento de aplicativos*
  * A capacidade de coletar e salvar as informações coletadas durante interrupções de rede temporárias.
  * A capacidade de coletar informações de identificação pessoal.
  * Uso ilimitado de [acompanhamento de recursos][features].
  * A capacidade de acompanhar exceções capturadas e geradas pelo código, além de exceções sem tratamento.
  * A capacidade de acompanhar exceções em assemblies `.dll`.
  * Criptografia de telemetria.

O Dotfuscator Professional é o [.NET Obfuscator][net-obfuscator] padrão do setor e é adequado para desenvolvedores empresariais que precisam de atualizações de produto, manutenção e suporte contínuos.
Além disso, o Dotfuscator Professional oferece maior integração com o Visual Studio e é licenciado para uso comercial.

Para obter mais informações sobre os recursos avançados de proteção do aplicativo do Dotfuscator Professional, visite a [página de Visão geral do Dotfuscator][product-about] do PreEmptive Solutions e [faça uma comparação com o Community Edition][product-compare].
[Avaliações com suporte completo estão disponíveis mediante solicitação em preemptive.com][eval].

## Consulte também
<a id="see-also" class="xliff"></a>

[Este tópico no Guia do Usuário completo do Dotfuscator CE][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[control-flow]: https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]: https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]: https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]: https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]: https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]: https://www.preemptive.com/images/stories/Dotfuscator/webframe.html#Check%20Actions.html
[features]: https://www.preemptive.com/images/stories/Dotfuscator/webframe.html#Feature_Usage_Tracking_and_the_Feature_Attribute.html

[net-obfuscator]: https://www.preemptive.com/products/dotfuscator/overview
[eval]: https://www.preemptive.com/eval-request

[product-about]: https://www.preemptive.com/products/dotfuscator/overview
[product-compare]: https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]: https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html

