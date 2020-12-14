---
description: 'En savoir plus sur : instruction while (C++)'
title: while, instruction (C++)
ms.date: 11/04/2016
f1_keywords:
- while_cpp
helpviewer_keywords:
- while keyword [C++]
- while keyword [C++], syntax
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
ms.openlocfilehash: 3001760372410222651366416ac74d0cba59f23b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302827"
---
# <a name="while-statement-c"></a>while, instruction (C++)

Exécute l' *instruction* à plusieurs reprises jusqu’à ce que la valeur de l' *expression* soit égale à zéro.

## <a name="syntax"></a>Syntaxe

```
while ( expression )
   statement
```

## <a name="remarks"></a>Notes

Le test d' *expression* a lieu avant chaque exécution de la boucle. par conséquent, une **`while`** boucle s’exécute zéro, une ou plusieurs fois. l' *expression* doit être d’un type intégral, d’un type pointeur ou d’un type de classe avec une conversion non ambiguë en type intégral ou pointeur.

Une **`while`** boucle peut également se terminer lorsqu’une instruction [break](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md)ou [Return](../cpp/return-statement-cpp.md) est exécutée dans le corps de l’instruction. Utilisez [continue](../cpp/continue-statement-cpp.md) pour terminer l’itération actuelle sans quitter la **`while`** boucle. **`continue`** passe le contrôle à l’itération suivante de la **`while`** boucle.

Le code suivant utilise une **`while`** boucle pour supprimer les traits de soulignement à droite d’une chaîne :

```cpp
// while_statement.cpp

#include <string.h>
#include <stdio.h>
char *trim( char *szSource )
{
    char *pszEOS = 0;

    //  Set pointer to character before terminating NULL
    pszEOS = szSource + strlen( szSource ) - 1;

    //  iterate backwards until non '_' is found
    while( (pszEOS >= szSource) && (*pszEOS == '_') )
        *pszEOS-- = '\0';

    return szSource;
}
int main()
{
    char szbuf[] = "12345_____";

    printf_s("\nBefore trim: %s", szbuf);
    printf_s("\nAfter trim: %s\n", trim(szbuf));
}
```

La condition d’arrêt est évaluée en haut de la boucle. S’il n’existe aucun trait de soulignement de fin, la boucle ne s’exécute jamais.

## <a name="see-also"></a>Voir aussi

[Instructions d'itération](../cpp/iteration-statements-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[do-while, instruction (C++)](../cpp/do-while-statement-cpp.md)<br/>
[for, instruction (C++)](../cpp/for-statement-cpp.md)<br/>
[Basé sur une plage, instruction (C++)](../cpp/range-based-for-statement-cpp.md)
