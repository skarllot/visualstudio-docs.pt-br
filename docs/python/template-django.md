---
title: Modelo de projeto Web do Django para o Python no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c479be58-13eb-4d77-9a27-c97ddc290963
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
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
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 4a5db2deb3633e8305dbf83cbe6ba8c0e3344c72
ms.contentlocale: pt-br
ms.lasthandoff: 05/09/2017

---

# <a name="django-web-project-template"></a>Modelo de projeto Web do Django

O [Django](https://www.djangoproject.com/) é uma estrutura do Python de alto nível projetada para um desenvolvimento da Web rápido, seguro e escalonável. O suporte do Python no Visual Studio fornece um modelo de projeto para configurar a estrutura de um aplicativo Web baseado em Django. Para usar o modelo no Visual Studio, selecione **Arquivo > Novo > Projeto**, pesquise “Django” e selecione o modelo “Projeto Web do Django”. O projeto resultante incluirá um código de texto clichê, bem como um banco de dados SQLite padrão. O modelo “Projeto Web em Branco do Django” é semelhante, mas não inclui o banco de dados.

O Visual Studio fornece o IntelliSense completo para projetos do Django:

- Variáveis de contexto passadas para o modelo:

    ![IntelliSense para variáveis de contexto](~/python/media/template-django-intellisense.png)

- Marcação e filtragem para elementos internos e definidos pelo usuário:

    ![IntelliSense para marcas e filtros](~/python/media/template-django-intellisense-filter.png)

- Realce de sintaxe para CSS e JavaScript inserido:

    ![CSS IntelliSense](~/python/media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](~/python/media/template-django-intellisense-js.png)


O Visual Studio também fornece [suporte de depuração](debugging.md) completo para projetos do Django: 

![Pontos de interrupção](~/python/media/template-django-debugging.png)

## <a name="django-management-console"></a>Console de gerenciamento do Django

O console de gerenciamento do Django é acessado por meio de vários comandos no menu **Projeto** ou clicando com o botão direito do mouse no projeto, no Gerenciador de Soluções.

- **Abrir o Shell do Django...**: abre um shell no contexto do aplicativo que permite manipular os modelos"

    ![Console](~/python/media/template-django-console-shell.png)

- **Banco de Dados de Sincronização do Django**: executa `manage.py syncdb` em uma janela interativa:

    ![Console](~/python/media/template-django-console-sync-db.png)

- **Coletar Estáticos**: executa `manage.py collectstatic --noinput` para copiar todos os arquivos estáticos para o caminho especificado por `STATIC_ROOT` em `settings.py`. Observe que ao [publicar no Microsoft Azure](template-web.md#publishing-to-azure-app-service), os arquivos estáticos são coletados automaticamente como parte da operação de publicação.

    ![Console](~/python/media/template-django-console-collect-static.png)

- **Validar**: executa `manage.py validate`, que relata os erros de validação nos modelos instalados especificados por `INSTALLED_APPS` em `settings.py`:

    ![Console](~/python/media/template-django-console-validate.png)
