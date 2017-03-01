---
title: "Manutenção de diretrizes para isolar aplicativos do Shell | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 15
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 823f025aa1dfcfc3c0a70e0e4730665b43b55dcc
ms.lasthandoff: 02/22/2017

---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Diretrizes de serviço para aplicativos de Shell isolado
Quando você distribui um aplicativo de shell do Visual Studio isolados, você deve ser capaz de fornecer atualizações de software para o seu aplicativo após a instalação. Para fazer isso, você deve instalar o aplicativo usando um arquivo do Microsoft Installer (MSI). Esse tipo de instalação permite que as atualizações de software fornecidas pela Microsoft para ser redistribuído por Web baixarem e consumida por seus clientes sem intervenção personalizada.  
  
## <a name="servicing-requirements"></a>Requisitos de serviço  
 Você pode garantir que a instalação do shell isolado pode permitir atualizações, certificando-se de que seu programa de instalação atenda aos seguintes critérios de três.  
  
### <a name="redistribute-by-using-an-msi"></a>Redistribuir usando um MSI  
 Você deve usar um MSI redistribuir seu aplicativo, como um MSI preserva a identidade do produto e garante que o aplicativo tem um local físico no computador cliente. Módulos de mesclagem (arquivos. msm) não fornecer essas garantias e não devem ser usados.  
  
### <a name="accounting-for-custom-actions"></a>Estatísticas para ações personalizadas  
 Ações personalizadas são diretivas de instalação não padrão em um programa de instalação. Ações personalizadas alterar parâmetros, como locais de arquivos, configurações do registro, as configurações de usuário ou outros itens de instalação. Ações personalizadas podem manipular os dados no momento da instalação.  
  
 Quando você usa ações personalizadas em um programa de instalação, você deve garantir que todas as ações personalizadas durante a instalação devem ter uma ação personalizada correspondente para desfazer a ação quando o usuário desinstala o aplicativo. Se o programa de instalação falha para fornecer correspondente desinstalar ação personalizada, removendo o aplicativo sairá parcialmente instalado.  
  
-   Uma ação personalizada que se baseia em uma versão específica de um arquivo ou hash de valores falhará quando as atualizações de software alterar essas versões ou valores de hash. Nesse caso a ação personalizada deve atualizar manualmente esses valores. Um problema adicional ocorre se as versões de um arquivo ou hash de valores são compartilhadas entre versões do produto. Evite esta dependência sempre que possível.  
  
### <a name="accounting-for-shared-files"></a>Estatísticas de arquivos compartilhados  
 Arquivos compartilhados com os mesmos nomes e são instalados no mesmo local por vários produtos. Esses produtos podem diferir em versão, unidade de manter estoque (SKU) ou ambos, e os produtos podem coexistir em um determinado computador. No entanto, os arquivos compartilhados criar problemas de manutenção por vários motivos:  
  
-   Atualizar arquivos compartilhados pode causar problemas de compatibilidade de aplicativos, porque uma atualização para um aplicativo pode alterar a versão de um arquivo usado por um segundo aplicativo não foi atualizado. Instaladores de produtos que compartilham arquivos contagem de referências aos arquivos compartilhados. Portanto, a desinstalação de um produto não afeta arquivos compartilhados, além de diminuir a contagem de instâncias instaladas.  
  
-   O instalador de Quick Fix Engineering (QFE) reverte as versões dos arquivos para as versões dos produtos que o instalador QFE atendido. Esse processo potencialmente interrompe um aplicativo que tinha fornecido um arquivo compartilhado atualizado.
