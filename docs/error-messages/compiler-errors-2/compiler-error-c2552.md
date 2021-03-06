---
description: 'En savoir plus sur : erreur du compilateur C2552'
title: Erreur du compilateur C2552
ms.date: 11/04/2016
f1_keywords:
- C2552
helpviewer_keywords:
- C2552
ms.assetid: 0e0ab759-788a-4faf-9337-80d4b9e2e8c9
ms.openlocfilehash: bd028af17ac5535eb1f72acf053dda193d4cc636
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134522"
---
# <a name="compiler-error-c2552"></a>Erreur du compilateur C2552

« identificateur » : les éléments qui ne sont pas des agrégats ne peuvent pas être initialisés avec une liste d'initialiseurs

Identificateur de l'agrégat a été correctement initialisé.

Les [agrégats](../../c-language/initializing-aggregate-types.md) sont définis comme suit :

- Tableaux

- Les classes, structures et unions qui n'ont pas les éléments suivants :

  - Constructeurs

  - Membres privés ou protégés

  - Classes de base

  - Fonctions virtuelles

De plus, Visual C++ n'autorise pas les types de données dans un agrégat qui contient des constructeurs.

Voici les raisons pour lesquelles une erreur C2552 peut se produire lorsqu'une initialisation d'agrégats est tentée sur un type :

- Le type a un ou plusieurs constructeurs définis par l'utilisateur.

- Le type a une ou plusieurs données membres non static privées.

- Le type a une ou plusieurs fonctions virtuelles.

- Le type a une classe de base.

- Un type est une classe de référence, ou une interface CLR.

- Le type a un tableau de dimension non fixée (tableau nul) dont les éléments ont des destructeurs.

L'exemple suivant génère l'erreur C2552 :

```cpp
// C2552.cpp
// compile with: /clr
#include <string>
using namespace std;

struct Pair_Incorrect {
private:
   string m_name;
   double m_val;
};

struct Pair_Correct1 {
public:
   Pair_Correct1(string name, double val)
      : m_name(name), m_val(val) {}

private:
   string m_name;
   double m_val;
};

struct Pair_Correct2 {
public:
   string m_name;
   double m_val;
};

int main() {
   // To fix, add a constructor to this class and use it for
   // initializing the data members, see Pair_Correct1 (below)
   // or
   // Do not have any private or protected non-static data members,
   // see Pair_Correct2 (below).  Pair_Correct2 is not recommended in
   // case your object model requires some non-static data members to
   // be private or protected

   string name("John");
   Pair_Incorrect pair1 = { name, 0.0 };   // C2552

   // initialize a CLR immutable value type that has a constructor
   System::DateTime dt = {2001, 4, 12, 22, 16, 49, 844};   // C2552

   Pair_Correct1 pair2( name, 0.0 );
   Pair_Correct1 pair3 = Pair_Correct1( name, 0.0 );
   Pair_Correct2 pair4 = { name, 0.0 };
   System::DateTime dt2(2001, 4, 12, 22, 16, 49, 844);
}
```
