---
title: "Amostra de demonstra&#231;&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "análise de código, exemplos"
  - "exemplo de demonstração [Visual Studio ALM]"
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Amostra de demonstra&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os procedimentos a seguir mostram como criar o exemplo para [Instruções passo a passo: analisando código do C\/C\+\+ em busca de defeitos](../Topic/Walkthrough:%20Analyzing%20C-C++%20Code%20for%20Defects.md).  Os procedimentos criam:  
  
-   Uma solução [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] chamada CppDemo.  
  
-   Um projeto de biblioteca estática chamada CodeDefects  
  
-   Um projeto de biblioteca estática chamada Anotações.  
  
 Os procedimentos também fornecem o código para o cabeçalho e arquivos .cpp para as bibliotecas estáticas.  
  
### Crie a solução CppDemo e o projeto CodeDefects  
  
1.  Clique no menu **Arquivo**, aponte para **Novo**, e então clique em **Novo Projeto**.  
  
2.  Na lista de árvore **Tipos de projeto**, se o Visual C\+\+ não é sua linguagem padrão no VS expanda **Outras Linguagens**.  
  
3.  Expanda **Visual C\+\+**, então clique em **Geral**.  
  
4.  Em **Modelos**, clique **Projeto Vazio**.  
  
5.  Na caixa de texto **Nome**, digite **CodeDefects**.  
  
6.  Marque a caixa de seleção **Crie diretórios para Solução**.  
  
7.  Na caixa de texto **Nome da Solução**, digite **CppDemo**.  
  
### Configure os projetos CodeDefects como biblioteca estática.  
  
1.  No Gerenciador de Soluções, clique com o botão direito em **CodeDefects**, então clique em **Propriedades**.  
  
2.  Expanda **Propriedades de Configuração** então clique em **Geral**.  
  
3.  Na lista **Geral**, selecione o texto na coluna próxima a **Extensão de Destino**, depois digite **.lib**  
  
4.  No **Padrões de Projeto**, clique na coluna ao lado de **Tipo de Configuração**, então clique em **Lib Estático \(.lib\)**.  
  
### Adicione o cabeçalho e o arquivo fonte ao projeto CodeDefects  
  
1.  No Gerenciador de Soluções, expanda **CodeDefects**, clique com o botão direito em **Arquivos de Cabeçalho**, clique em **Adicionar**, então clique em **Novo Item**.  
  
2.  Na caixa de diálogo **Adicionar Novo Item**, clique em **Código**, então clique em **Arquivo de Cabeçalho \(.h\)**.  
  
3.  Na caixa **Nome**, digite **Bug.cpp** e depois clique em **Adicionar**.  
  
4.  Copie o seguinte código e cole\-o no arquivo **Bug.cpp** no editor [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    ```  
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5.  No Gerenciador de Soluções, clique com o botão direito em **Arquivos Fonte**, aponte para **Novo**, e então clique em **Novo Item**.  
  
6.  Na caixa de diálogo **Adicionar Novo Item**, clique em **Arquivo C\+\+ \(.cpp\)**  
  
7.  Na caixa **Nome**, digite **Bug.cpp** e depois clique em **Adicionar**.  
  
8.  Copie o seguinte código e cole\-o no arquivo Bug.h no editor [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    ```  
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. Clique no menu **Arquivo**, depois clique em **Salvar Tudo**.  
  
### Adicione o projeto de Anotações e configure\-o como biblioteca estática  
  
1.  No Gerenciador de Soluções, clique em **CppDemo**, aponte para **Adicionar**, e depois clique em **Novo Projeto**.  
  
2.  Na caixa de diálogo **Adicionar Novo Projeto**, expanda Visual C\+\+, clique em **Geral**, depois clique em **Projeto Vazio**.  
  
3.  Na caixa de texto **Nome**, digite **Annotations**, então clique em **Adicionar**.  
  
4.  No Gerenciador de Soluções, clique com o botão direito em **Anotações**, e depois clique em **Propriedades**.  
  
5.  Expanda **Propriedades de Configuração** então clique em **Geral**.  
  
6.  Na lista **Geral**, selecione o texto na coluna próxima a **Extensão de Destino**, depois digite **.lib**  
  
7.  No **Padrões de Projeto**, clique na coluna ao lado de **Tipo de Configuração**, então clique em **Lib Estático \(.lib\)**.  
  
### Adicione o arquivo cabeçalho e o arquivo fonte ao projeto de Anotações  
  
1.  No Gerenciador de Soluções, expanda **Anotações**, clique com o botão direito do mouse em **Arquivos de Cabeçalho**, clique **Adicionar**, e depois clique em **Novo Item**.  
  
2.  Na caixa de diálogo **Adicionar Novo Item**, clique **Arquivo de Cabeçalho \(.h\)**.  
  
3.  Na caixa **Nome**, digite **annotations.h** e depois clique em **Adicionar**.  
  
4.  Copie o seguinte código e cole\-o no arquivo **annotations.h** no editor [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5.  No Gerenciador de Soluções, clique com o botão direito em **Arquivos Fonte**, aponte para **Novo**, e então clique em **Novo Item**.  
  
6.  Na caixa de diálogo **Adicionar Novo Item**, clique em **Código** e depois clique em **Arquivo C\+\+ \(.cpp\)**  
  
7.  Na caixa **Name**, digite **annotations.cpp** e depois clique em **Add**.  
  
8.  Copie o seguinte código e cole\-o no arquivo **annotations.cpp** no editor [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. Clique no menu **Arquivo**, depois clique em **Salvar Tudo**.