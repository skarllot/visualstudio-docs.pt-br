---
title: "Projeto de exemplo para cria&#231;&#227;o de testes de unidade | Microsoft Docs"
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
  - "exemplo de teste de unidade [Visual Studio]"
  - "testes de unidade, exemplos"
ms.assetid: db80aaf2-0652-4d3f-a8c5-2a98fd8502a2
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "mlearned"
manager: "douge"
---
# Projeto de exemplo para cria&#231;&#227;o de testes de unidade
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este código de exemplo é fornecido para uso nas instruções a seguir:  
  
-   [Instruções passo a passo: criando e executando testes de unidade para código gerenciado](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).  Este passo a passo leva você através das etapas para criar e personalizar testes de unidade, executá\-los e examinar os resultados do teste.  
  
-   [Walkthrough: Run tests and view code coverage](http://msdn.microsoft.com/pt-br/d4aab8e2-2140-4975-b4e3-41ef3fa944c8).  Este passo a passo ilustra como exibir dados de cobertura de código, que mostra a proporção de código do projeto que está sendo testado.  
  
-   [Instruções passo a passo: usando o utilitário de teste de linha de comando](../Topic/Walkthrough:%20using%20the%20command-line%20test%20utility.md).  Neste passo a passo, você pode usar o utilitário de linha de comando MSTest.exe para executar testes e exibir os resultados.  
  
## Código de exemplo  
 O erro intencional somente nesse exemplo é que o método Debit em "m\_balance \+ \= valor" deve ter um sinal de menos não um sinal de mais entrar antes do sinal de igual.  
  
```  
using System;   
  
namespace BankAccountNS  
{  
    /// <summary>   
    /// Bank Account demo class.   
    /// </summary>   
    public class BankAccount  
    {  
        private string m_customerName;  
  
        private double m_balance;  
  
        private bool m_frozen = false;  
  
        private BankAccount()  
        {  
        }  
  
        public BankAccount(string customerName, double balance)  
        {  
            m_customerName = customerName;  
            m_balance = balance;  
        }  
  
        public string CustomerName  
        {  
            get { return m_customerName; }  
        }  
  
        public double Balance  
        {  
            get { return m_balance; }  
        }  
  
        public void Debit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount > m_balance)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount; // intentionally incorrect code  
        }  
  
        public void Credit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount;  
        }  
  
        private void FreezeAccount()  
        {  
            m_frozen = true;  
        }  
  
        private void UnfreezeAccount()  
        {  
            m_frozen = false;  
        }  
  
        public static void Main()  
        {  
            BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);   
  
            ba.Credit(5.77);  
            ba.Debit(11.22);  
            Console.WriteLine("Current balance is ${0}", ba.Balance);  
        }  
  
    }  
}  
```  
  
 \/ \* Os exemplos de empresas, organizações, produtos, nomes de domínio, endereços de email, logotipos, pessoas, lugares e eventos aqui descritos são fictícios.  Nenhuma associação com qualquer empresa, organização, produto, nome de domínio, endereço de email, logotipo, pessoa, lugares ou eventos é intencional ou deve ser inferida.  \*\/  
  
## Trabalhando com o código  
 Para trabalhar com esse código, primeiramente, você precisa criar um projeto para ele no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Siga as etapas na seção "Preparar o passo a passo" [Instruções passo a passo: criando e executando testes de unidade para código gerenciado](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).  
  
## Consulte também  
 [Instruções passo a passo: criando e executando testes de unidade para código gerenciado](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)   
 [Walkthrough: Run tests and view code coverage](http://msdn.microsoft.com/pt-br/d4aab8e2-2140-4975-b4e3-41ef3fa944c8)   
 [Instruções passo a passo: usando o utilitário de teste de linha de comando](../Topic/Walkthrough:%20using%20the%20command-line%20test%20utility.md)