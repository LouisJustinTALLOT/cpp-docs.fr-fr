---
title: "Fonctions virtuelles | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "classes dérivées, fonctions virtuelles"
  - "fonctions (C++), fonctions virtuelles"
  - "fonctions virtuelles"
ms.assetid: b3e1ed88-2a90-4af8-960a-16f47deb3452
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Fonctions virtuelles
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Une fonction virtuelle est une fonction membre dont vous souhaitez la redéfinition dans des classes dérivées.  Lorsque vous faites référence à un objet de classe dérivée à l'aide d'un pointeur ou d'une référence à la classe de base, vous pouvez appeler une fonction virtuelle pour cet objet et exécuter la version de la classe dérivée de la fonction.  
  
 Les fonctions virtuelles garantissent que la fonction correcte est appelée pour un objet, quelle que soit l'expression utilisée pour créer l'appel de fonction.  
  
 Supposons qu'une classe de base contient une fonction déclarée comme [virtuelle](../cpp/virtual-cpp.md) et qu'une classe dérivée définit la même fonction.  La fonction de la classe dérivée est appelée pour les objets de la classe dérivée, même si elle est appelée à l'aide d'un pointeur ou d'une référence à la classe de base.  L'exemple suivant montre une classe de base qui fournit une implémentation de la fonction `PrintBalance` et de deux classes dérivées.  
  
```  
// deriv_VirtualFunctions.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
class Account {  
public:  
   Account( double d ) { _balance = d; }  
   virtual double GetBalance() { return _balance; }  
   virtual void PrintBalance() { cerr << "Error. Balance not available for base type." << endl; }  
private:  
    double _balance;  
};  
  
class CheckingAccount : public Account {  
public:  
   CheckingAccount(double d) : Account(d) {}  
   void PrintBalance() { cout << "Checking account balance: " << GetBalance() << endl; }  
};  
  
class SavingsAccount : public Account {  
public:  
   SavingsAccount(double d) : Account(d) {}  
   void PrintBalance() { cout << "Savings account balance: " << GetBalance(); }  
};  
  
int main() {  
   // Create objects of type CheckingAccount and SavingsAccount.  
   CheckingAccount *pChecking = new CheckingAccount( 100.00 ) ;  
   SavingsAccount  *pSavings  = new SavingsAccount( 1000.00 );  
  
   // Call PrintBalance using a pointer to Account.  
   Account *pAccount = pChecking;  
   pAccount->PrintBalance();  
  
   // Call PrintBalance using a pointer to Account.  
   pAccount = pSavings;  
   pAccount->PrintBalance();     
}  
```  
  
 Dans le code précédent, les appels à `PrintBalance` sont identiques, sauf pour l'objet vers lequel `pAccount` pointe.  Étant donné que `PrintBalance` est virtuelle, c'est la version de la fonction définie pour chaque objet qui est appelée.  La fonction `PrintBalance` dans les classes dérivées `CheckingAccount` et `SavingsAccount` « remplacent » la fonction dans la classe de base `Account`.  
  
 Si une classe qui ne fournit pas d'implémentation de substitution de la fonction `PrintBalance` est déclarée, c'est l'implémentation par défaut de la classe de base `Account` qui est utilisée.  
  
 Les fonctions dans les classes dérivées remplacent les fonctions virtuelles dans les classes de base uniquement si leur type est identique.  Une fonction dans une classe dérivée ne peut pas différer d'une fonction virtuelle dans une classe de base uniquement par son type de retour ; la liste d'arguments doit différer également.  
  
 Lors de l'appel d'une fonction via des pointeurs ou des références, les règles suivantes s'appliquent :  
  
-   Un appel à une fonction virtuelle est résolu en fonction du type sous\-jacent d'objet pour lequel cette fonction est appelée.  
  
-   Un appel à une fonction non virtuelle est résolu en fonction du type du pointeur ou de la référence.  
  
 L'exemple suivant montre comment les fonctions virtuelles et non virtuelles se comportent lorsqu'elles sont appelées via des pointeurs :  
  
```  
// deriv_VirtualFunctions2.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
class Base {  
public:  
   virtual void NameOf();   // Virtual function.  
   void InvokingClass();   // Nonvirtual function.  
};  
  
// Implement the two functions.  
void Base::NameOf() {  
   cout << "Base::NameOf\n";  
}  
  
void Base::InvokingClass() {  
   cout << "Invoked by Base\n";  
}  
  
class Derived : public Base {  
public:  
   void NameOf();   // Virtual function.  
   void InvokingClass();   // Nonvirtual function.  
};  
  
// Implement the two functions.  
void Derived::NameOf() {  
   cout << "Derived::NameOf\n";  
}  
  
void Derived::InvokingClass() {  
   cout << "Invoked by Derived\n";  
}  
  
int main() {  
   // Declare an object of type Derived.  
   Derived aDerived;  
  
   // Declare two pointers, one of type Derived * and the other  
   //  of type Base *, and initialize them to point to aDerived.  
   Derived *pDerived = &aDerived;  
   Base    *pBase    = &aDerived;  
  
   // Call the functions.  
   pBase->NameOf();           // Call virtual function.  
   pBase->InvokingClass();    // Call nonvirtual function.  
   pDerived->NameOf();        // Call virtual function.  
   pDerived->InvokingClass(); // Call nonvirtual function.  
}  
```  
  
### Sortie  
  
```  
Derived::NameOf  
Invoked by Base  
Derived::NameOf  
Invoked by Derived  
```  
  
 Comme vous pouvez le constater, que la fonction `NameOf` soit appelée via un pointeur vers `Base` ou un pointeur vers `Derived`, c'est la fonction pour `Derived` qui est appelée.  La fonction pour `Derived` est appelée car `NameOf` est une fonction virtuelle, et `pBase` et `pDerived` pointent vers un objet de type `Derived`.  
  
 Étant donné que les fonctions virtuelles sont appelées uniquement pour les objets de type de classe, vous ne pouvez pas déclarer les fonctions globales ou statiques comme **virtuelles**.  
  
 Le mot clé **virtual** peut être utilisé lors de la déclaration des fonctions de substitution dans une classe dérivée, mais il est inutile ; les substitutions des fonctions virtuelles sont toujours virtuelles.  
  
 Les fonctions virtuelles dans une classe de base doivent être définies à moins qu'elles ne soient déclarées à l'aide de l'élément *pure\-specifier*.  \(Pour plus d'informations sur les fonctions virtuelles pures, consultez [Classes abstraites](../cpp/abstract-classes-cpp.md).\)  
  
 Le mécanisme d'appel de fonction virtuelle peut être supprimé en qualifiant explicitement le nom de fonction à l'aide de l'opérateur de résolution de portée \(`::`\).  Prenons l'exemple précédent qui implique la classe `Account`.  Pour appeler `PrintBalance` dans la classe de base, utilisez le code suivant :  
  
```  
CheckingAccount *pChecking = new CheckingAccount( 100.00 );  
  
pChecking->Account::PrintBalance();  //  Explicit qualification.  
  
Account *pAccount = pChecking;  // Call Account::PrintBalance  
  
pAccount->Account::PrintBalance();   //  Explicit qualification.  
```  
  
 Les deux appels à `PrintBalance` dans l'exemple précédent suppriment le mécanisme d'appel de fonction virtuelle.  
  
## Voir aussi  
 [Accès aux fonctions virtuelles](../misc/access-to-virtual-functions.md)