---
title: "Como: instalar uma vers&#227;o espec&#237;fica do Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instalar uma versão específica, o Visual Studio"
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
caps.handback.revision: 16
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Como: instalar uma vers&#227;o espec&#237;fica do Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Podemos atualizar a instalação do Visual Studio com freqüência para que você obtenha a versão mais atual, otimizada de nossos recursos opcionais.  Mas se você deseja instalar uma versão anterior do Visual Studio 2015 — por exemplo, uma versão anterior à atualização 1 do Visual Studio com suporte para iOS, e em seguida, você deve forçar a instalação do Visual Studio para usar uma versão anterior dos seus arquivos de manifesto do recurso. Este artigo descreve como fazer isso.  
  
## Instalando a versão atual  
 Desde o lançamento inicial do Visual Studio 2015, atualizamos o mecanismo de instalação e os arquivos de manifesto várias vezes.  Isso significa que se você [download e execute o Visual Studio hoje instalação](https://www.visualstudio.com/downloads/download-visual-studio-vs) em uma máquina limpa e conectado à internet, o programa de instalação instala a atualização mais recente do Visual Studio 2015, que inclui aprimoramentos mais recentes, bem como versões mais novas e recentes de ferramentas e recursos opcionais.  
  
## Instalando versões anteriores  
 Você pode criar e montar uma imagem ISO, ou você pode baixar e inicie o instalador da web diretamente e, em seguida, anexe o arquivo de .exe com parâmetros de linha de comando adicionais \(como \/CustomInstallPath, \/Full, \/InstallSelectableItems, \/NoRestart, etc.\) para controlar como o Visual Studio é instalado.  
  
 A tabela a seguir inclui alguns cenários de point\-in\-time específicos e os parâmetros de linha de comando necessários, que você deve passar para o instalador da web do Enterprise edition. \(Os mesmos parâmetros funcionarão com a comunidade ou Professional edition instaladores da web também.\)  
  
|Edição do Visual Studio 2015|O que fazer|Linha de comando para usar|O que a instalação não|  
|----------------------------------|-----------------|--------------------------------|----------------------------|  
|O Visual Studio Enterprise \(a versão pública mais recente\)|Visual Studio Enterprise com atualizações \(disponível em   [VisualStudio.com](https://www.visualstudio.com/products/vs-2015-product-editions.aspx)\)|`vs_enterprise.exe` **Note:**  O comportamento padrão de instalação oferece os mais recentes recursos opcionais e, portanto, não requer nenhum parâmetro de linha de comando.|Instalação do Visual Studio usará o feed.xml mais recente e instale os arquivos mais recentes|  
|Visual Studio Enterprise atualização 3 \(o original 3 sem nenhuma outra atualização 3 era atualização\)|Visual Studio Enterprise RTM \(disponível no [página de download de assinaturas do MSDN](https://msdn.microsoft.com/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160628.2/enu/feed.xml`|Instalação do Visual Studio usará o feed.xml que estava disponível quando a atualização 3 lançada|  
|Enterprise atualização 2 do Visual Studio \(atualização 2 original, mas com atualizações que a atualização 3 previamente atualizado\)|Visual Studio Enterprise RTM \(disponível no [página de download de assinaturas do MSDN](https://msdn.microsoft.com/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160620.2/enu/feed.xml`|Instalação do Visual Studio usará o feed.xml atual antes da atualização 3 lançado|  
|O Visual Studio Enterprise \(o original 2 sem nenhuma outra atualização 2 era atualização\)|Visual Studio Enterprise RTM \(disponível no [página de download de assinaturas do MSDN](https://msdn.microsoft.com/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/0/6/B/06BB0C5C-C767-4250-91DA-AB463377597E/20160405.3/enu/feed.xml`|Instalação do Visual Studio usará o feed.xml que estava disponível quando a atualização 2 lançada|  
|Enterprise atualização 1 do Visual Studio \(atualização 1 original, mas com atualizações que previamente atualizados atualização 2\)|Visual Studio Enterprise RTM \(disponível no [página de download de assinaturas do MSDN](https://msdn.microsoft.com/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20160225.3/enu/feed.xml`|Instalação do Visual Studio usará o feed.xml atual antes da atualização 2 lançado|  
|Visual Studio Enterprise Update 1 \(o 1 atualização original sem nenhuma outra atualização era 1 atualização\)|Visual Studio Enterprise RTM \(disponível no [página de download de assinaturas do MSDN](https://msdn.microsoft.com/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|Instalação do Visual Studio usará o feed.xml estava disponível na atualização 1 lançado|  
|O Visual Studio Enterprise \(RTM original, mas com atualizações previamente atualizados atualização 1\)|Visual Studio Enterprise RTM \(disponível no  [página de download de assinaturas do MSDN](https://msdn.microsoft.com/en-us/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|Instalação do Visual Studio usará o feed.xml atual antes da atualização 1 lançado|  
|O Visual Studio Enterprise \(RTM original sem qualquer atualização\)|Visual Studio Enterprise RTM \(disponível no [página de download de assinaturas do MSDN](https://msdn.microsoft.com/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|Instalação do Visual Studio usará o feed.xml que estava disponível quando lançado RTM|  
  
> [!IMPORTANT]
>  Dependendo da linguagem que você deseja usar, substitua "enu" \(para inglês\) com um dos seguintes valores:  
>   
>  -   CHS \(para chinês \(simplificado\)\)  
> -   chinês tradicional \(em chinês \(tradicional\)\)  
> -   csy \(para tcheco\)  
> -   deu \(para o alemão\)  
> -   ESN \(para espanhol\)  
> -   FRA \(para francês\)  
> -   ITA \(para italiano\)  
> -   JPA \(para japonês\)  
> -   KOR \(para coreano\)  
> -   plk \(para polonês\)  
> -   PTB \(para o português\)  
> -   RUS \(para Russo\)  
> -   TRK \(para o turco\)  
  
## Consulte também  
 [Guia do Administrador do Visual Studio](../install/visual-studio-administrator-guide.md)