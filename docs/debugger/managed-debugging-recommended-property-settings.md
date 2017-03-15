---
title: "Depura&#231;&#227;o gerenciada: configura&#231;&#245;es de propriedade recomendadas | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurando [Visual Studio], gerenciadas"
  - "depurando código gerenciado, definições de propriedade recomendadas"
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depura&#231;&#227;o gerenciada: configura&#231;&#245;es de propriedade recomendadas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Certas propriedades devem ser definidas da mesma maneira para todos os cenários gerenciados de depuração.  
  
 As tabelas a seguir exibem as configurações de propriedade recomendadas.  
  
 As configurações não listadas aqui podem variar entre os diferentes tipos de projeto gerenciados.  Por exemplo, **Iniciar Ação** será definido de maneira diferente em um projeto do Windows Forms do que em um projeto [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
### As propriedades de configuração na compilação \(C\#\) ou na guia Compilar \(Visual Basic\)  
  
|**Nome da propriedade**|**Configuração**|  
|-----------------------------|----------------------|  
|**Defina a constante DEPURAR**|C\# e F\#: defina a caixa de seleção como verificado.  Isso permite que o aplicativo use uma classe de Depuração.|  
|**Defina a constante RASTREAR**|C\# e F\#: defina a caixa de seleção como verificado.  Isso permite que o aplicativo use uma classe de rastreamento.|  
|**Código de otimização**|F\#, C\# e Visual Basic: definidos como falso.  O código otimizado é mais difícil de depurar porque as instruções geradas não correspondem diretamente ao código\-fonte.  Se você descobrir que seu programa tem um bug que aparece apenas em código otimizado, poderá ativar essa configuração, mas lembre\-se de que o código exibido na janela **Desmontagem** é gerado de origem otimizada que pode não corresponder ao que é visto no Editor de Códigos.  Para depurar um código otimizado, você deve desativar o Apenas Meu Código. \(Consulte [Restringir o passo ao Apenas Meu Código](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code).\)<br /><br /> Para obter mais informações, consulte [Definições do projeto para configurações de depuração do C\#](../debugger/project-settings-for-csharp-debug-configurations.md) ou [Definições do projeto para uma configuração de depuração do Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|  
|**Caminho de saída**|Defina como bin\\Debug\\.|  
|**Opções compiladas avançadas**|Somente Visual Basic.  Clique em **Avançado** para definir as propriedades avançadas descritas na tabela a seguir.|  
  
### Caixa de diálogo de Configurações Avançadas do Compilador  
  
|**Nome da propriedade**|**Configuração**|  
|-----------------------------|----------------------|  
|**Habilitar otimizações**|Defina como falso para obter as razões especificadas na opção **Otimizar Código** na tabela anterior.|  
|**Gerar informações sobre depuração**|Marque esta caixa de seleção para que o sinalizador \/DEBUG seja definido ao compilar, o que vai gerar as informações necessárias para facilitar a depuração.|  
|**Defina a constante DEPURAR**|Marque esta caixa de seleção para definir a constante de `DEBUG`, que permite que seu aplicativo use a classe <xref:System.Diagnostics.Debug>.|  
|**Defina a constante RASTREAR**|Marque esta caixa de seleção para definir a constante de `TRACE`, que permite que seu aplicativo use a classe <xref:System.Diagnostics.Trace>.|  
  
## Consulte também  
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)   
 [Tipos de projeto C\#, F\# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)