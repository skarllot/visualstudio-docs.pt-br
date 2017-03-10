---
title: "Implantando aplicativos ClickOnce para servidores de teste e produ&#231;&#227;o sem assinar novamente | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "atualizações do aplicativo, ClickOnce"
  - "Aplicativos ClickOnce, implantando sem assinar novamente"
  - "implantação ClickOnce, sem assinar novamente"
  - "Marca deploymentProvider"
  - "manifestos [ClickOnce]"
  - "atualizar localização [ClickOnce]"
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Implantando aplicativos ClickOnce para servidores de teste e produ&#231;&#227;o sem assinar novamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico apresenta um novo recurso de ClickOnce, introduzido na.NET Framework versão 3.5, o que permite a implantação de aplicativos de ClickOnce de vários locais de rede sem a nova assinatura ou alterando a ClickOnce manifesta.  
  
> [!NOTE]
>  Desistindo do jogo ainda é o método preferencial para a implantação de novas versões dos aplicativos.  Sempre que possível, use o método resigning.  Para obter mais informações, consulte [Mage.exe \(Ferramenta de Geração e Edição de Manifesto\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md).  
  
 ISVs e desenvolvedores de terceiros podem opt\-in para esse recurso, tornando mais fácil para seus clientes atualizar seus aplicativos.  Esse recurso pode ser usado nas seguintes situações:  
  
-   Ao atualizar um aplicativo, e não a primeira instalação de um aplicativo.  
  
-   Quando há apenas uma configuração do aplicativo em um computador.  Por exemplo, se um aplicativo estiver configurado para apontar para dois bancos de dados diferentes, você não pode usar esse recurso.  
  
## Excluindo deploymentProvider de manifestos de implantação  
 No.NET Framework 2.0 e o.NET Framework 3.0, qualquer aplicativo de ClickOnce que é instalado no sistema para disponibilidade offline deve especificar um `deploymentProvider` em seu manifesto de implantação.  O `deploymentProvider` é conhecida como o local de atualização; é o local em que ClickOnce irá verificar atualizações do aplicativo.  Esse requisito, juntamente com a necessidade de editores do aplicativo assinar suas implantações, dificultou para uma empresa atualizar um aplicativo de ClickOnce por um fornecedor ou de outros fabricantes.  Ele também torna mais difícil implantar no mesmo aplicativo em vários locais na mesma rede.  
  
 Com as alterações que foram feitas em ClickOnce na.NET Framework 3.5, é possível que um terceiro fornecer um aplicativo de ClickOnce para outra organização, que pode implantar o aplicativo em sua própria rede.  
  
 Para tirar proveito desse recurso, exclua os desenvolvedores de aplicativos ClickOnce `deploymentProvider` da sua implantação manifestos.  Isso significa excluindo o `-providerUrl` argumento quando você cria a implantação manifesta com Mage ou certificando\-se o  **Local iniciar** caixa de texto no  **O manifesto de aplicativo** guia for deixado em branco se você estiver gerando manifestos de implantação com MageUI.exe.  
  
## deploymentProvider e atualizações de aplicativos  
 Começando com o.NET Framework 3.5, você não precisa especificar um `deploymentProvider` em seu manifesto de implantação para implantar um aplicativo de ClickOnce para uso online e offline.  Isso oferece suporte para o cenário em que você precise empacotar e assinar a implantação por conta própria, mas permitir que outras empresas implantar o aplicativo suas redes.  
  
 O ponto chave a ser lembrado é que os aplicativos que excluem um `deploymentProvider` não é possível alterar seu local de instalação durante as atualizações, até que eles são fornecidos em uma atualização que inclui o `deploymentProvider` marca novamente.  
  
 Aqui estão dois exemplos para esclarecer esse ponto.  No primeiro exemplo, você pode publicar um aplicativo de ClickOnce que não tenha `deploymentProvider` marca e você solicitar aos usuários que instalá\-lo a partir de http:\/\/www.adatum.com\/MyApplication\/.  Se você decidir que deseja publicar a próxima atualização do aplicativo do http:\/\/subdomain.adatum.com\/MyApplication\/, você não terá de nenhuma maneira de significando isso no manifesto de implantação que reside no http:\/\/www.adatum.com\/MyApplication\/.  Você pode fazer uma destas duas coisas:  
  
-   Avise os usuários para desinstalar a versão anterior e instalar a nova versão da nova localização.  
  
-   Incluem uma atualização do http:\/\/www.adatum.com\/MyApplication\/ que inclui um `deploymentProvider` apontando para http:\/\/www.adatum.com\/MyApplication\/.  Em seguida, solte outra atualização posterior com `deploymentProvider` apontando para http:\/\/subdomain.adatum.com\/MyApplication\/.  
  
 No segundo exemplo, você pode publicar um aplicativo de ClickOnce que especifica `deploymentProvider`, e você decida removê\-lo.  Uma vez a nova versão sem `deploymentProvider` foi descarregado para clientes, não será capaz de redirecionar o caminho usado para atualizações até você liberar uma versão do seu aplicativo que tenha `deploymentProvider` restaurado.  Assim como acontece com o primeiro exemplo, `deploymentProvider` inicialmente deve apontar para o local de atualização atual, seu novo local.  Neste caso, se você tentar inserir uma `deploymentProvider` que se refere a http:\/\/subdomain.adatum.com\/MyApplication\/, em seguida, a próxima atualização falhará.  
  
## A criação de uma implantação  
 Para obter orientações passo a passo sobre a criação de implantações que podem ser implantadas a partir de diferentes locais da rede, consulte [Instruções passo a passo: implantando manualmente um aplicativo ClickOnce que não requer nova assinatura e que preserva informações de identidade visual](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
## Consulte também  
 [Mage.exe \(Ferramenta de Geração e Edição de Manifesto\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(Ferramenta de Geração e Edição de Manifesto, cliente gráfico\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)