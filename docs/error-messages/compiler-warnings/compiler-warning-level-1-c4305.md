---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4305'
title: Avertissement du compilateur (niveau 1) C4305
ms.date: 01/17/2018
f1_keywords:
- C4305
helpviewer_keywords:
- C4305
ms.openlocfilehash: a6cee5be3b5929c0fbf487a8c40d37e269e6a994
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340084"
---
# <a name="compiler-warning-level-1-c4305"></a>Avertissement du compilateur (niveau 1) C4305

> '*Context*' : troncation de'*type1*'en'*type2*'

## <a name="remarks"></a>Notes

Cet avertissement est émis lorsqu’une valeur est convertie en un type plus petit dans une initialisation ou en tant qu’argument de constructeur, ce qui entraîne une perte d’informations.

## <a name="example"></a>Exemple

Cet exemple montre deux façons d’afficher cet avertissement :

```cpp
// C4305.cpp
// Compile by using: cl /EHsc /W4 C4305.cpp

struct item
{
    item(float) {}
};

int main()
{
    float f = 2.71828;          // C4305 'initializing'
    item i(3.14159);            // C4305 'argument'
    return static_cast<int>(f);
}
```

Pour résoudre ce problème, initialisez à l’aide d’une valeur du type correct ou utilisez un cast explicite vers le type approprié. Par exemple, utilisez un **`float`** littéral tel que 2,71828, f au lieu d’un **`double`** (type par défaut pour les littéraux à virgule flottante) pour initialiser une **`float`** variable, ou pour passer à un constructeur qui accepte un **`float`** argument.
