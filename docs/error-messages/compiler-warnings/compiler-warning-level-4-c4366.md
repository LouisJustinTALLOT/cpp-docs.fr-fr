---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4366'
title: Avertissement du compilateur (niveau 4) C4366
ms.date: 11/04/2016
f1_keywords:
- C4366
helpviewer_keywords:
- C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
ms.openlocfilehash: 9fa703d64ca48090d3bf6c2f5d9e21668d9acd71
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330593"
---
# <a name="compiler-warning-level-4-c4366"></a>Avertissement du compilateur (niveau 4) C4366

Le résultat de l’opérateur’opérateur’unaire peut être non aligné

Si un membre de structure n’est jamais aligné en raison de la compression, le compilateur vous avertit lorsque l’adresse de ce membre est assignée à un pointeur aligné. Par défaut, tous les pointeurs sont alignés.

Pour résoudre les C4366, modifiez l’alignement de la structure ou déclarez le pointeur avec le mot clé [__unaligned](../../cpp/unaligned.md) .

Pour plus d’informations, consultez __unaligned et [Pack](../../preprocessor/pack.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4366.

```cpp
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
