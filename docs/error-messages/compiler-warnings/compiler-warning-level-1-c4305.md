---
title: Compilateur avertissement (niveau 1) C4305 | Documents Microsoft
ms.custom: ''
ms.date: 1/17/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4305
dev_langs:
- C++
helpviewer_keywords:
- C4305
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7694c511f57b6907227d62f969b61218f836cb14
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277821"
---
# <a name="compiler-warning-level-1-c4305"></a>Avertissement du compilateur (niveau 1) C4305

> '*contexte*' : troncation de '*type1*'à'*type2*'  

## <a name="remarks"></a>Notes

Cet avertissement est émis lorsqu’une valeur est convertie en un type plus petit dans une initialisation ou comme un argument de constructeur, ce qui entraîne une perte d’informations.

## <a name="example"></a>Exemple

Cet exemple montre deux façons, vous pouvez voir cet avertissement :

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
