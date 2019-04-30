---
title: Avertissement du compilateur (niveau 3) C4191
ms.date: 11/04/2016
f1_keywords:
- C4191
helpviewer_keywords:
- C4191
ms.assetid: 576d3bc6-95b7-448a-af31-5d798452df09
ms.openlocfilehash: 72a485811647911207b6d048c686acdadd142b65
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402253"
---
# <a name="compiler-warning-level-3-c4191"></a>Avertissement du compilateur (niveau 3) C4191

'operator/operation' : conversion risquée de 'type of expression' en 'type required'

Plusieurs opérations faisant appel à des pointeurs fonction sont considérées comme non sécurisées :

- Types de fonction avec conventions d’appel différentes.

- Types de fonction avec conventions de retour différentes.

- Types d’argument ou de retour de différentes tailles, catégories de types ou classifications.

- Longueurs des listes d’arguments différentes (sur `__cdecl`, le cast de type n’est effectué que de la liste la plus longue vers la liste la plus courte, même si la plus courte est déclarée varargs).

- Pointeur vers des données (autre que **void**<strong>\*</strong>) utilisé comme alias d’un pointeur vers une fonction.

- Toute autre différence de type pouvant conduire à une erreur ou un avertissement sur un `reinterpret_cast`.

L’appel de cette fonction par le pointeur résultat peut bloquer votre programme.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère l’avertissement C4191.

```
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