---
title: C4868 d’avertissement du compilateur | Documents Microsoft
ms.date: 10/26/2017
ms.topic: error-reference
f1_keywords:
- C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 922a1a8434da8449758b9d55ebe89ace2f262cd5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275240"
---
# <a name="compiler-warning-level-4-c4868"></a>Du compilateur (niveau 4) d’avertissement C4868

> '_fichier_(*line_number*)' compilateur ne peut pas appliquer l’ordre d’évaluation de gauche à droite dans la liste d’initialiseurs entre accolades

Les éléments d’une liste d’initialiseurs entre accolades sont évaluées dans l’ordre de gauche à droite. Il existe deux cas dans lequel le compilateur est incapable de garantir l’ordre : le premier est lorsque certains éléments sont des objets passés par valeur ; la seconde est lors de la compilation avec `/clr` et certains éléments sont les champs d’objets ou éléments de tableau. Lorsque le compilateur ne peut pas garantir l’évaluation de gauche à droite, il émet l’avertissement C4868.

Cet avertissement peut être généré en raison de travail de mise en conformité du compilateur pour Visual C++ 2015 Update 2. Le code compilé avant Visual C++ 2015 Update 2 peut maintenant générer C4868.

Cet avertissement est désactivé par défaut. Utilisez `/Wall` pour activer cet avertissement.

Pour résoudre cet avertissement, envisagez d’abord si l’évaluation de gauche à droite des éléments de liste d’initialiseurs est nécessaire, par exemple lorsque d’évaluation des éléments peut produire des effets secondaires dépendant de l’ordre. Dans de nombreux cas, l’ordre dans lequel les éléments sont évalués n’a pas d’effet observable.

Si l’ordre d’évaluation doit être de gauche à droite, considérez s’il est possible de passer les éléments `const` font référence à la place. Une modification de telles élimine l’avertissement dans l’exemple de code suivant.

## <a name="example"></a>Exemple

Cet exemple génère C4868 et illustre une méthode pour résoudre ce problème :

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