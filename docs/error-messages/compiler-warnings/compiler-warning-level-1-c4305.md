---
title: Avertissement du compilateur (niveau 1) C4305
ms.date: 1/17/2018
f1_keywords:
- C4305
helpviewer_keywords:
- C4305
ms.openlocfilehash: 3f9116b0e7bdd9ee13c42b48f44da4b090f41ccd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649122"
---
# <a name="compiler-warning-level-1-c4305"></a>Avertissement du compilateur (niveau 1) C4305

> «*contexte*' : troncation de '*type1*'en'*type2*»

## <a name="remarks"></a>Notes

Cet avertissement est émis lorsqu’une valeur est convertie en un type plus petit dans une initialisation ou comme un argument de constructeur, ce qui entraîne une perte d’informations.

## <a name="example"></a>Exemple

Cet exemple montre deux façons cet avertissement peut s’afficher :

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

Pour résoudre ce problème, initialiser à l’aide d’une valeur du type correct, ou utilisez un cast explicite en type correct. Par exemple, utiliser un **float** littéral comme 2.71828f au lieu d’un **double** (le type par défaut pour les littéraux à virgule flottante) pour initialiser un **float** variable, ou à passer à un constructeur qui accepte un **float** argument.
