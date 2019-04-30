---
title: Avertissement du compilateur C4868
ms.date: 10/26/2017
f1_keywords:
- C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
ms.openlocfilehash: d0bc8716e53e71c52f6a31036a95d0b4cefedd79
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388707"
---
# <a name="compiler-warning-level-4-c4868"></a>Avertissement (niveau 4) du compilateur C4868

> «_fichier_(*line_number*) « compilateur ne peut pas appliquer l’ordre d’évaluation de gauche à droite dans la liste d’initialiseurs entre accolades

Les éléments d’une liste d’initialiseurs entre accolades doivent être évaluées dans l’ordre de gauche à droite. Il existe deux cas dans lequel le compilateur est incapable de garantir l’ordre : la première est lorsque certains éléments sont des objets passés par valeur ; la seconde est lors de la compilation avec `/clr` et certains éléments de sont des champs d’objets ou éléments de tableau. Lorsque le compilateur ne peut pas garantir l’évaluation de gauche à droite, il émet l’avertissement C4868.

Cet avertissement peut être généré en raison de travail de la conformité du compilateur pour Visual C++ 2015 Update 2. Le code compilé avant Visual C++ 2015 Update 2 peut désormais générer C4868.

Cet avertissement est désactivé par défaut. Utilisez `/Wall` pour activer cet avertissement.

Pour résoudre cet avertissement, envisagez d’abord si l’évaluation de gauche à droite des éléments de liste d’initialiseur est nécessaire, par exemple lorsque d’évaluation des éléments peut produire des effets d’ordre dépendant. Dans de nombreux cas, l’ordre dans lequel les éléments sont évalués n’a pas d’effet visible.

Si l’ordre d’évaluation doit être de gauche à droite, considérez si il est possible de passer les éléments `const` font référence à la place. Une modification telle que cela supprime l’avertissement dans l’exemple de code suivant.

## <a name="example"></a>Exemple

Cet exemple génère C4868 et montre un moyen de résoudre le problème :

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