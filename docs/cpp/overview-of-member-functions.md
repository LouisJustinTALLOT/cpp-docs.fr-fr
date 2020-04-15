---
title: Vue d'ensemble des fonctions membres
ms.date: 11/04/2016
helpviewer_keywords:
- this pointer, and nonstatic member functions
- nonstatic member functions [C++]
- inline functions [C++], treating member functions as
- member functions [C++], definition in class declaration
ms.assetid: 9f77a438-500e-40bb-a6c6-544678f3f4c8
ms.openlocfilehash: 6dec4ee53cd840c47d76ac0579daca710b0eeb68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358408"
---
# <a name="overview-of-member-functions"></a>Vue d'ensemble des fonctions membres

Les fonctions membres sont statique ou non statique. Le comportement des fonctions statiques des membres diffère des autres fonctions des membres parce que les fonctions statiques des membres n’ont pas **implicitement cet** argument. Les fonctions non statistiques des membres ont **un** pointeur. Les fonctions membres (statique ou non statique) peuvent être définies à l'intérieur ou à l'extérieur de la déclaration de classe.

Si une fonction membre est définie dans une déclaration de classe, elle est traitée comme une fonction inline, et il est inutile de qualifier le nom de fonction avec son nom de classe. Bien que les fonctions définies à l’intérieur des déclarations de classe soient déjà traitées comme des fonctions inlines, vous pouvez utiliser le mot clé **inline** pour documenter le code.

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

Si la définition d’une fonction membre n’est en dehors de la déclaration de classe, elle n’est traitée comme une fonction inline que si elle est explicitement déclarée **en ligne**. En outre, le nom de fonction dans la définition doit être qualifié avec son nom de classe par l'opérateur de résolution de portée (`::`).

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
> Bien que les fonctions membres puissent être définies dans une déclaration de classe ou séparément, aucune fonction membre ne peut être ajoutée à une classe après la classe définie.

Les classes contenant des fonctions membres peuvent avoir plusieurs déclarations, mais les fonctions membres elles-mêmes doivent avoir une seule définition dans un programme. Plusieurs définitions génèrent un message d'erreur au moment de la liaison. Si une classe contient des définitions de fonction inline, les définitions de fonction doivent être identiques pour observer cette règle « d'une définition ».
