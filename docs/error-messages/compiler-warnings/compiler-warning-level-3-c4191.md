---
title: Avertissement du compilateur (niveau 3) C4191
ms.date: 11/04/2016
f1_keywords:
- C4191
helpviewer_keywords:
- C4191
ms.assetid: 576d3bc6-95b7-448a-af31-5d798452df09
ms.openlocfilehash: 9914818520fafb707b6821ba827e867b8aea9928
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220026"
---
# <a name="compiler-warning-level-3-c4191"></a>Avertissement du compilateur (niveau 3) C4191

'operator/operation' : conversion risquée de 'type of expression' en 'type required'

Plusieurs opérations faisant appel à des pointeurs fonction sont considérées comme non sécurisées :

- Types de fonction avec conventions d’appel différentes.

- Types de fonction avec conventions de retour différentes.

- Types d’argument ou de retour de différentes tailles, catégories de types ou classifications.

- Longueurs de liste d’arguments différente (on **`__cdecl`** , uniquement dans la conversion d’une liste plus longue vers une liste plus petite, même si la valeur est plus petite).

- Pointeur vers des données (autres que **`void`** <strong>\*</strong> ) aliasés par rapport à un pointeur vers une fonction.

- Toute autre différence de type qui générerait une erreur ou un avertissement sur un **`reinterpret_cast`** .

L’appel de cette fonction par le pointeur résultat peut bloquer votre programme.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère l’avertissement C4191.

```cpp
// C4191.cpp
// compile with: /W3 /clr
#pragma warning(default: 4191)

void __clrcall f1() { }
void __cdecl   f2() { }

typedef void (__clrcall * fnptr1)();
typedef void (__cdecl   * fnptr2)();

int main() {
   fnptr1 fp1 = static_cast<fnptr1>(&f1);
   fnptr2 fp2 = (fnptr2) &f2;

   fnptr1 fp3 = (fnptr1) &f2;   // C4191
   fnptr2 fp4 = (fnptr2) &f1;   // C4191
};
```
