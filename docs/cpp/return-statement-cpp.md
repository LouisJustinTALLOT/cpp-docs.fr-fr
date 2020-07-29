---
title: return, instruction (C++)
ms.date: 11/04/2016
f1_keywords:
- return_cpp
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
ms.openlocfilehash: 6a1ed4f374f133abd0233826d1b58896d49576cf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225863"
---
# <a name="return-statement-c"></a>return, instruction (C++)

Termine l'exécution d'une fonction et retourne le contrôle à la fonction d'appel (ou au système d'exploitation si vous transférez le contrôle à partir de la fonction `main`). L'exécution reprend dans la fonction d'appel au point immédiatement après l'appel.

## <a name="syntax"></a>Syntaxe

```
return [expression];
```

## <a name="remarks"></a>Notes

La clause `expression`, si elle est présente, est convertie dans le type spécifié dans la déclaration de fonction, comme si une initialisation était exécutée. La conversion du type de l’expression vers le **`return`** type de la fonction peut créer des objets temporaires. Pour plus d’informations sur la façon de créer des objets temporaires, consultez la page [objets temporaires](../cpp/temporary-objects.md).

La valeur de la clause `expression` est retournée à la fonction d'appel. Si l'expression est omise, la valeur de retour de la fonction n'est pas définie. Les constructeurs et les destructeurs, ainsi que les fonctions de type **`void`** , ne peuvent pas spécifier une expression dans l' **`return`** instruction. Les fonctions de tous les autres types doivent spécifier une expression dans l' **`return`** instruction.

Lorsque le déroulement du contrôle quitte le bloc englobant la définition de la fonction, le résultat est le même que si une **`return`** instruction sans expression avait été exécutée. Ceci n'est pas valable pour les fonctions déclarées comme retournant une valeur.

Une fonction peut avoir un nombre quelconque d' **`return`** instructions.

L’exemple suivant utilise une expression avec une **`return`** instruction pour obtenir le plus grand de deux entiers.

## <a name="example"></a>Exemple

```cpp
// return_statement2.cpp
#include <stdio.h>

int max ( int a, int b )
{
   return ( a > b ? a : b );
}

int main()
{
    int nOne = 5;
    int nTwo = 7;

    printf_s("\n%d is bigger\n", max( nOne, nTwo ));
}
```

## <a name="see-also"></a>Voir aussi

[Instructions de saut](../cpp/jump-statements-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
