---
title: "Área de teste 2: Obter do controle de origem | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
caps.latest.revision: 18
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
ms.openlocfilehash: e01dce4fd2c7b9b3d02e01e1949929ef36f9d693
ms.lasthandoff: 02/22/2017

---
# <a name="test-area-2-get-from-source-control"></a>Área de teste 2: Obter do controle de origem
Essa área de teste abrange casos de teste para recuperar itens do repositório de versão por meio do comando Get. Nesses casos de teste pode ser aplicados para locais e projetos da Web.  
  
## <a name="command-menu-access"></a>Acesso ao Menu comando  
 O seguinte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] caminhos de menu do ambiente de desenvolvimento integrado são usados nos casos de teste.  
  
##### <a name="get-latest-version"></a>Obtenha a versão mais recente:  
  
-   **Arquivo**, **controle de origem**, **obter versão mais recente**.  
  
-   **Arquivo**, **obter versão mais recente**.  
  
-   Menu de atalho, **obter última versão**.  
  
-   Get: **File**, **Source Control**, **Get**.  
  
## <a name="expected-behavior"></a>Comportamento esperado  
  
##### <a name="get-latest-version"></a>Obtenha a versão mais recente:  
 Realiza uma recuperação silencioso (nenhuma interface do usuário) da versão mais recente do item do armazenamento de versão.  
  
##### <a name="get"></a>Obter:  
 Exibe o **obter** caixa de diálogo e permite que o usuário faça alterações para o conjunto de arquivos que será recuperado, bem como modifica as opções que afetam como os arquivos são recuperados.  
  
## <a name="test-cases"></a>Casos de teste  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Obter a versão mais recente de um arquivo que não existe localmente|1.  Criar um projeto.<br />2.  Adicione um item ao projeto.<br />3.  Colocar o projeto sob controle de origem.<br />4.  Exclua a cópia local do item.<br />5.  Obter a versão mais recente do item (Menu de atalho, **Get Latest Version**).|Arquivo do item é recuperado localmente.|  
|Obter um arquivo que não existe localmente|1.  Criar um projeto.<br />2.  Adicione um item ao projeto.<br />3.  Colocar o projeto sob controle de origem.<br />4.  Exclua a cópia local do item.<br />5.  Obter o item (**arquivo**, **controle de origem**, **obter** \<item >).|Arquivo do item é recuperado localmente.|  
|Obter um arquivo que foi feito check-out exclusivamente e modificado localmente|1.  Criar um projeto.<br />2.  Adicione um item ao projeto.<br />3.  Colocar o projeto sob controle de origem.<br />4.  Check-out do item de projeto exclusivamente.<br />5.  Modificar a cópia local.<br />6.  Obter a versão mais recente do item (**arquivo**, **obter versão mais recente do** \<item >). Se essa etapa for bem-sucedida, continue para a próxima etapa.<br />7.  Clique em **substituir** botão na caixa de diálogo de aviso.|**ReResult da etapa 6**`:`<br /><br /> Caixa de diálogo de aviso indica que o arquivo foi extraído.<br /><br /> **ReResult da etapa 7:**<br /><br /> Modificação de arquivo local é substituído pela versão original do armazenamento de versão.<br /><br /> Arquivo é leitura/gravação.|  
|Obter e substituir o arquivo que está com check-out, compartilhado e modificado localmente|1.  Crie um novo projeto.<br />2.  Adicione um item ao projeto.<br />3.  Colocar o projeto sob controle de origem.<br />4.  Check-out do item de projeto como compartilhada.<br />5.  Modificar a cópia local.<br />6.  Obter a versão mais recente do item (**arquivo**, **obter versão mais recente do** \<item >). Se essa etapa for bem-sucedida, continue para a próxima etapa.<br />7.  Clique em **substituir** na caixa de diálogo de aviso.|**Resultado da etapa 6:**<br /><br /> Caixa de diálogo de aviso indica que o arquivo foi extraído.<br /><br /> **Resultado da etapa 7:**<br /><br /> Modificação de arquivo local é substituído pela versão original do armazenamento de versão.<br /><br /> Arquivo é leitura/gravação.|  
|Obter um arquivo que existe localmente, mesmo que a versão mais recente no armazenamento de versão|1.  Crie um novo projeto.<br />2.  Adicione um item ao projeto.<br />3.  Colocar o projeto sob controle de origem.<br />4.  Obter o item (**arquivo**, **controle de origem**, **obter** \<item >).|Arquivo local é alterado.|  
|Obtenha uma solução com um projeto|1.  Crie uma solução com um projeto.<br />2.  Coloque a solução sob controle de origem.<br />3.  Exclua todos os arquivos de projeto localmente.<br />4.  A solução (**arquivo**, **controle de origem**, **obter**).|Todos os arquivos excluídos são restaurados localmente.|  
  
## <a name="see-also"></a>Consulte também  
 [Guia de teste para Plug-ins de controle de origem](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
