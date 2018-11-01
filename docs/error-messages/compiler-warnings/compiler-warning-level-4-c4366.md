---
title: Avertissement du compilateur (niveau 4) C4366
ms.date: 11/04/2016
f1_keywords:
- C4366
helpviewer_keywords:
- C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
ms.openlocfilehash: 11fcb0070359201de39ca5f33c83d000e02f0835
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629064"
---
# <a name="compiler-warning-level-4-c4366"></a>Avertissement du compilateur (niveau 4) C4366

Le résultat de l’opérateur 'opérateur' unaire peut être non aligné

Si un membre de structure ne peut jamais être non aligné en raison de la compression, le compilateur vous avertit qu’adresse du membre est attribué à un pointeur aligné. Par défaut, tous les pointeurs sont alignés.

Pour résoudre l’erreur C4366, modifier l’alignement de la structure ou déclarez le pointeur avec le [__unaligned](../../cpp/unaligned.md) mot clé.

Pour plus d’informations, consultez __unaligned et [pack](../../preprocessor/pack.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4366.

```
// C4366.cpp
// compile with: /W4 /c
// processor: IPF x64
#pragma pack(1)
struct X {
   short s1;
   int s2;
};

int main() {
   X x;
   short * ps1 = &x.s1;   // OK
   int * ps2 = &x.s2;   // C4366
}
```