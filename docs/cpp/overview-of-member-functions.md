---
title: Vue d’ensemble des fonctions membres | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- this pointer, and nonstatic member functions
- nonstatic member functions [C++]
- inline functions [C++], treating member functions as
- member functions [C++], definition in class declaration
ms.assetid: 9f77a438-500e-40bb-a6c6-544678f3f4c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 21de116740161a965bd4790eff751d10cf878b79
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39409114"
---
# <a name="overview-of-member-functions"></a>Vue d'ensemble des fonctions membres
Les fonctions membres sont statique ou non statique. Le comportement de fonctions de membre statique diffère des autres fonctions membres, car les fonctions membres statiques ont implicite ne **cela** argument. Les fonctions membres non statiques ont un **cela** pointeur. Les fonctions membres (statique ou non statique) peuvent être définies à l'intérieur ou à l'extérieur de la déclaration de classe.  
  
 Si une fonction membre est définie dans une déclaration de classe, elle est traitée comme une fonction inline, et il est inutile de qualifier le nom de fonction avec son nom de classe. Bien que les fonctions définies dans les déclarations de classe sont déjà traitées comme des fonctions inline, vous pouvez utiliser la **inline** mot clé pour documenter du code.  
  
 Un exemple de déclaration d'une fonction dans une déclaration de classe suit :  
  
```cpp 
// overview_of_member_functions1.cpp  
class Account  
{  
public:  
    // Declare the member function Deposit within the declaration  
    //  of class Account.  
    double Deposit( double HowMuch )  
    {  
        balance += HowMuch;  
        return balance;  
    }  
private:  
    double balance;  
};  
  
int main()  
{  
}  
```  
  
 Si la définition de la fonction d’un membre est en dehors de la déclaration de classe, il est traité comme une fonction inline uniquement si elle est déclarée explicitement comme **inline**. En outre, le nom de fonction dans la définition doit être qualifié avec son nom de classe par l'opérateur de résolution de portée (`::`).  
  
 L'exemple suivant est identique à la déclaration précédente de la classe `Account`, sauf que la fonction `Deposit` est définie à l'extérieur de la déclaration de classe :  
  
```cpp 
// overview_of_member_functions2.cpp  
class Account  
{  
public:  
    // Declare the member function Deposit but do not define it.  
    double Deposit( double HowMuch );  
private:  
    double balance;  
};  
  
inline double Account::Deposit( double HowMuch )  
{  
    balance += HowMuch;  
    return balance;  
}  
  
int main()  
{  
}  
```  
  
> [!NOTE]
>  Bien que les fonctions membres puissent être définies dans une déclaration de classe ou séparément, aucune fonction membre ne peut être ajoutée à une classe après la classe définie.  
  
 Les classes contenant des fonctions membres peuvent avoir plusieurs déclarations, mais les fonctions membres elles-mêmes doivent avoir une seule définition dans un programme. Plusieurs définitions génèrent un message d'erreur au moment de la liaison. Si une classe contient des définitions de fonction inline, les définitions de fonction doivent être identiques pour observer cette règle « d'une définition ».  