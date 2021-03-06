---
description: "En savoir plus sur : surcharge de l' &gt; &gt; opérateur pour vos propres classes"
title: Surcharge de l’opérateur &gt;&gt; pour vos propres classes
ms.date: 11/04/2016
helpviewer_keywords:
- operator>>
- operator>>, overloading for your own classes
- operator >>, overloading for your own classes
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
ms.openlocfilehash: 4de7c16dd1c42f85f169da50f11a514eb245b47c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340851"
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

[Flux d’entrée](../standard-library/input-streams.md)
