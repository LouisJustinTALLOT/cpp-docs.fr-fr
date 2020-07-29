---
title: Fonctions récursives
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], recursive
- function calls, recursive
- functions [C], calling recursively
- recursive function calls
ms.assetid: 59739040-3081-4006-abbc-9d8423992bce
ms.openlocfilehash: 8979d386c6fc3415cd50159250db8488cb917cee
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87199514"
---
# <a name="recursive-functions"></a>Fonctions récursives

Toute fonction d'un programme C peut être appelée de manière récursive. Autrement dit, elle peut s'appeler elle-même. Le nombre d'appels récurrents est limité à la taille de la pile. Pour plus d’informations sur les options d’éditeur de liens qui définissent la taille de la pile, consultez l’option de l’éditeur de liens [ `/STACK` (allocations de piles)](../build/reference/stack-stack-allocations.md) . Chaque fois que la fonction est appelée, un nouveau stockage est alloué pour les paramètres et pour les **`auto`** **`register`** variables et afin que leurs valeurs dans les appels précédents et non terminés ne soient pas remplacées. Les paramètres sont uniquement directement accessibles à l'instance de la fonction dans laquelle ils sont créés. Les paramètres précédents ne sont pas directement accessibles aux instances suivantes de la fonction.

Notez que les variables déclarées avec le **`static`** stockage ne nécessitent pas de nouveau stockage avec chaque appel récurrent. Leur stockage existe pour la durée de vie du programme. Chaque référence à cette variable accède à la même zone de stockage.

## <a name="example"></a>Exemple

Cet exemple illustre des appels récurrents :

```C
int factorial( int num );      /* Function prototype */

int main()
{
    int result, number;
    .
    .
    .
    result = factorial( number );
}

int factorial( int num )      /* Function definition */
{
    .
    .
    .
    if ( ( num > 0 ) || ( num <= 10 ) )
        return( num * factorial( num - 1 ) );
}
```

## <a name="see-also"></a>Voir aussi

[Appels de fonction](../c-language/function-calls.md)
