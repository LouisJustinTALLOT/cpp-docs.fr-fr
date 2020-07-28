---
title: Avertissement du compilateur C4868
ms.date: 10/26/2017
f1_keywords:
- C4868
helpviewer_keywords:
- C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
ms.openlocfilehash: fe113a948cdf2a6e4b4fcf6b0055fe92d583f004
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220130"
---
# <a name="compiler-warning-level-4-c4868"></a>Avertissement du compilateur (niveau 4) C4868

> le compilateur'_file_(*line_number*) 'ne peut pas appliquer l’ordre d’évaluation de gauche à droite dans la liste d’initialiseurs entre accolades

Les éléments d’une liste d’initialiseurs entre accolades doivent être évalués dans l’ordre de gauche à droite. Il existe deux cas dans lesquels le compilateur ne peut pas garantir cet ordre : le premier est lorsque certains des éléments sont des objets passés par valeur ; la seconde est lors de la compilation avec `/clr` et certains des éléments sont des champs d’objets ou des éléments de tableau. Lorsque le compilateur ne peut pas garantir l’évaluation de gauche à droite, il émet un avertissement C4868.

Cet avertissement peut être généré en raison du travail de mise en conformité du compilateur effectué pour Visual Studio 2015 Update 2. Le code compilé avant Visual Studio 2015 Update 2 peut désormais générer des C4868.

Cet avertissement est désactivé par défaut. Utilisez `/Wall` pour activer cet avertissement.

Pour résoudre cet avertissement, commencez par déterminer si l’évaluation de gauche à droite des éléments de la liste d’initialiseurs est nécessaire, par exemple lorsque l’évaluation des éléments peut produire des effets secondaires dépendants de la commande. Dans de nombreux cas, l’ordre dans lequel les éléments sont évalués n’a pas d’effet observable.

Si l’ordre d’évaluation doit être de gauche à droite, déterminez s’il est possible de passer les éléments par **`const`** référence à la place. Une modification telle que celle-ci élimine l’avertissement dans l’exemple de code suivant.

## <a name="example"></a>Exemple

Cet exemple génère C4868 et montre un moyen de le corriger :

```cpp
// C4868.cpp
// compile with: /c /Wall
#include <cstdio>

class HasCopyConstructor
{
public:
    int x;

    HasCopyConstructor(int x): x(x) {}

    HasCopyConstructor(const HasCopyConstructor& h): x(h.x)
    {
        printf("Constructing %d\n", h.x);
    }
};

class TripWarning4868
{
public:
    // note that taking "HasCopyConstructor" parameters by-value will trigger copy-construction.
    TripWarning4868(HasCopyConstructor a, HasCopyConstructor b) {}

    // This variation will not trigger the warning:
    // TripWarning4868(const HasCopyConstructor& a, const HasCopyConstructor& b) {}
};

int main()
{
    HasCopyConstructor a{1};
    HasCopyConstructor b{2};

    // the warning will indicate the below line, the usage of the braced initializer list.
    TripWarning4868 warningOnThisLine{a, b};
};
```
