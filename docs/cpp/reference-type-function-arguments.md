---
title: Arguments de fonction de type référence
ms.date: 08/27/2018
helpviewer_keywords:
- arguments [C++], function
- functions [C++], parameters
- function parameters [C++], reference-type
- function arguments [C++], reference-type
- passing parameters [C++], reference-type arguments
ms.assetid: 0a70e831-9e76-46c0-821d-aeba13d73cc0
ms.openlocfilehash: 5a409efbe2908954d394656cb989ad6b80a9ce22
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233637"
---
# <a name="reference-type-function-arguments"></a>Arguments de fonction de type référence

Il est souvent plus efficace de passer des références que de grands objets à des fonctions. Cela permet au compilateur de passer l'adresse de l'objet tout en maintenant la syntaxe qui aurait été utilisée pour accéder à l'objet. Prenons l'exemple suivant, qui utilise la structure `Date` :

```cpp
// reference_type_function_arguments.cpp
#include <iostream>

struct Date
{
    short Month;
    short Day;
    short Year;
};

// Create a date of the form DDDYYYY (day of year, year)
// from a Date.
long DateOfYear( Date& date )
{
    static int cDaysInMonth[] = {
        31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31
    };
    long dateOfYear = 0;

    // Add in days for months already elapsed.
    for ( int i = 0; i < date.Month - 1; ++i )
        dateOfYear += cDaysInMonth[i];

    // Add in days for this month.
    dateOfYear += date.Day;

    // Check for leap year.
    if ( date.Month > 2 &&
        (( date.Year % 100 != 0 || date.Year % 400 == 0 ) &&
        date.Year % 4 == 0 ))
        dateOfYear++;

    // Add in year.
    dateOfYear *= 10000;
    dateOfYear += date.Year;

    return dateOfYear;
}

int main()
{
    Date date{ 8, 27, 2018 };
    long dateOfYear = DateOfYear(date);
    std::cout << dateOfYear << std::endl;
}
```

Le code précédent montre que les membres d’une structure passée par référence sont accessibles à l’aide de l’opérateur de sélection de membres (**.**) au lieu de l’opérateur de sélection de membre de pointeur ( **->** ).

Bien que les arguments passés comme types référence observent la syntaxe des types non-pointeur, ils conservent une caractéristique importante des types pointeur : ils sont modifiables sauf s’ils sont déclarés comme **`const`** . Comme l'objectif du code précédent n'est pas de modifier l'objet `date`, un prototype de fonction plus approprié est :

```cpp
long DateOfYear( const Date& date );
```

Ce prototype garantit que la fonction `DateOfYear` ne modifiera pas son argument.

Toute fonction prototypée comme acceptant un type référence peut accepter un objet du même type à sa place, car il existe une conversion standard de *TypeName* en *TypeName* <strong>&</strong> .

## <a name="see-also"></a>Voir aussi

[Informations de référence](../cpp/references-cpp.md)<br/>
