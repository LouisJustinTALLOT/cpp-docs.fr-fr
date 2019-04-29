---
title: Surcharge de l’opérateur &gt;&gt; pour vos propres classes
ms.date: 11/04/2016
helpviewer_keywords:
- operator>>
- operator>>, overloading for your own classes
- operator >>, overloading for your own classes
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
ms.openlocfilehash: 86b8af963345c8eb9b3f44cfb16332bc09420bf3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370721"
---
# <a name="overloading-the-gtgt-operator-for-your-own-classes"></a>Surcharge de l’opérateur &gt;&gt; pour vos propres classes

Les flux d’entrée utilisent l’opérateur d’extraction (`>>`) pour les types standards. Vous pouvez écrire des opérateurs d’extraction similaires pour vos propres types, en veillant à utiliser les espaces blancs de façon appropriée.

Voici un exemple d’opérateur d’extraction pour la classe `Date` présentée précédemment :

```cpp
istream& operator>> (istream& is, Date& dt)
{
    is>> dt.mo>> dt.da>> dt.yr;
    return is;
}
```

## <a name="see-also"></a>Voir aussi

[Flux d’entrée](../standard-library/input-streams.md)<br/>
