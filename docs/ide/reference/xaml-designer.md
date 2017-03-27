---
title: "Página de opções do Designer XAML | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.XAMLDesigner
ms.assetid: ad3820b2-0d95-4807-a75c-c3467ed973a3
caps.latest.revision: 1
author: kempb
ms.author: kempb
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
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: d23a47b708754248cd5c3fb8d86510a0c96491fa
ms.lasthandoff: 03/07/2017

---
# <a name="xaml-designer-options-page"></a>Página de opções do Designer XAML
Use a página de opções do **Designer XAML** para especificar como os elementos e atributos são formatados nos documentos XAML. Para abrir essa página, escolha o menu **Ferramentas** e, em seguida, **Opções**. Para acessar a página de propriedades **XAML Designer**, escolha o nó **XAML Designer**. As configurações para o XAML Designer são aplicadas quando você abre o documento. Portanto, se você alterar as configurações, será necessário fechar e reabrir o Visual Studio para ver as alterações.

> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  

## <a name="enable-xaml-designer"></a>Habilitar o XAML Designer
Quando selecionada, essa configuração habilita o XAML Designer. O XAML Designer fornece uma área de trabalho visual para editar documentos XAML. Algumas funcionalidades no Visual Studio, como o IntelliSense para associação de dados e recursos, exigem que o XAML Designer seja habilitado.

As configurações a seguir aplicam-se somente quando o XAML Designer está habilitado. Se você alterar esta opção, será necessário reiniciar o Visual Studio para que a configuração entre em vigor.

## <a name="default-document-view"></a>Exibição de documento padrão
Use essa configuração para controlar se o modo de exibição de Design aparece quando documentos XAML são carregados.

|||  
|-|-|  
|**Modo de Exibição de Fonte**|Especifica se somente a fonte de XAML aparece no modo de exibição XAML. Isso é útil ao carregar documentos grandes.|  
|**Modo de exibição de Design**|Especifica se apenas um XAML Designer visual aparece no modo de exibição XAML.|  
|**Modo Divisão**|Especifica se o XAML Designer visual e a fonte de XAML aparecem próximos um do outro no modo de exibição XAML (local com base na configuração **Orientação de Divisão**).|  

## <a name="split-orientation"></a>Orientação de Divisão
Use essa configuração para controlar quando e como o XAML Designer aparece ao editar um documento XAML. Essas configurações aplicam-se somente quando a **Exibição do documento padrão** está definida como **Modo Divisão**.

|||  
|-|-|  
|**Vertical**|A fonte de XAML aparece no lado esquerdo do modo de exibição XAML e o XAML Designer aparece no outro lado.|  
|**Horizontal**|O XAML Designer aparece na parte superior do modo de exibição XAML e a fonte de XAML aparece abaixo dele.|  
|**Padrão**|O documento XAML usa a orientação de divisão recomendada para a plataforma de destino do projeto do documento. Para a maioria das plataformas, isso é equivalente a **Horizontal**.|  

## <a name="zoom-by-using"></a>Aplicar zoom usando
Use essa configuração para determinar o funcionamento de aplicar zoom ao editar um documento XAML.

|||  
|-|-|  
|**Botão de rolagem do mouse**|Ampliar o XAML Designer ao rolar o botão de rolagem do mouse.|  
|**CTRL + botão de rolagem do mouse**|Ampliar o XAML Designer pressionando a tecla CTRL ao rolar o botão de rolagem do mouse.|  
|**Alt + botão de rolagem do mouse**|Ampliar o XAML Designer pressionando a tecla ALT ao rolar o botão de rolagem do mouse.|  

Essas configurações determinam o comportamento do Designer ao editar um documento XAML.

|||  
|-|-|  
|**Nomear automaticamente os elementos interativos na criação**|Especifica se um nome padrão é fornecido para um novo elemento interativo ao adicioná-lo no Designer.|  
|**Inserir automaticamente as propriedades de layout na criação de elemento**|Especifica se as propriedades de layout são fornecidas a um novo elemento ao adicioná-lo no Designer.|  
|**Usar layout baseado em quadrantes**|Especifica se o controle atualmente selecionado alinha-se às bordas do contêiner pai mais próximas. Se essa caixa de seleção estiver desmarcada, os alinhamentos de controle não se alteram durante uma operação de movimentação ou criação.|  
|**Popular automaticamente os itens da caixa de ferramentas**|Especifica se os controles de usuário e os controles personalizados na solução atual são mostrados automaticamente na caixa de ferramentas.|  

## <a name="settings-blend-only"></a>Configurações (Somente Blend)
Use essas opções para determinar as configurações ao editar arquivos XAML usando o Blend.

|||  
|-|-|  
|**Aplicar zoom usando**|Ampliar o XAML Designer ao rolar o botão de rolagem do mouse ou pressionando a tecla CTRL ou ALT ao rolar o botão de rolagem do mouse.|  
|**Digitar unidades**|Especifica se as medidas no designer são baseadas em pontos ou pixels. Como os Aplicativos Universais do Windows não oferecem suporte a pontos, as unidades serão automaticamente convertidas em pixels se **Pontos** estiver selecionado.|  

## <a name="artboard-blend-only"></a>Prancheta (Somente Blend)
Use essas configurações para determinar o comportamento do XAML Designer ao editar documentos XAML no Blend.

### <a name="snapping"></a>Ajustando

|||  
|-|-|  
|**Mostrar grade de ajuste**|Quando essa opção é selecionada, as linhas de grade aparecem no designer para ajudá-lo a alinhar os controles. Os controles adicionados ao designer ajustam-se a essas linhas de grade quando a opção **Ajustar às linhas de grade** está selecionada.|  
|**Ajustar às linhas de grade**|Quando os controles são adicionados ou movidos no designer, eles se encaixam às linhas de grade.|  
|**Espaçamento da linha de grade**|Especifica o espaçamento entre linhas de grade em pixels ou pontos (conforme determinado pela configuração **Digitar unidades**).|  
|**Ajustar-se às guias de alinhamento**|Especifica se os controles ajustam-se às guias de alinhamento.|  
|**Margem padrão**|Quando **Ajustar-se às guias de alinhamento** está habilitado, especifica o espaçamento entre as guias de alinhamento e o controle em pixels ou pontos (conforme determinado pela configuração **Digitar unidades**).|  
|**Preenchimento padrão**|Quando **Ajustar-se às guias de alinhamento** está habilitado, especifica o espaçamento adicional entre as guias de alinhamento e o controle em pixels ou pontos (conforme determinado pela configuração **Digitar unidades**).|  

### <a name="animation"></a>Animação
Use essa configuração para determinar se um aviso é exibido quando animações dependentes (não aceleradas) estão habilitadas no Blend.

### <a name="effects"></a>Efeitos
Use essas configurações para determinar se efeitos são renderizados ao editar arquivos XAML no XAML Designer usando o Blend.

|||  
|-|-|  
|**Renderizar efeitos**|Especifica se efeitos renderizam ao editar arquivos XAML no XAML Designer usando o Blend.|  
|**Limite de zoom**|Especifica o percentual de ampliação com a qual os efeitos são renderizados quando a caixa de seleção **Renderizar efeitos** está selecionada. Se você aplicar zoom além dessa configuração os efeitos não serão mais renderizados no XAML Designer.|  

## <a name="see-also"></a>Consulte também  
 [XAML no WPF](http://msdn.microsoft.com/Library/5d858575-a83b-42df-ad3f-047ed2d6e3c8)   
 [Como alterar as configurações do modo de exibição XAML](http://msdn.microsoft.com/en-us/aee87c79-ca01-4f84-8fb7-a9e47048ee47)   
 [Passo a passo do Code e XAML](http://msdn.microsoft.com/en-us/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)

