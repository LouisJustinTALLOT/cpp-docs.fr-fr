---
description: 'En savoir plus sur : avertissement du compilateur (niveau 2) C4285'
title: Avertissement du compilateur (niveau 2) C4285
ms.date: 11/04/2016
f1_keywords:
- C4285
helpviewer_keywords:
- C4285
ms.assetid: fa14de1f-fc19-4eec-8bea-81003636e12f
ms.openlocfilehash: 2eafb9bb17c5e6ea782ff00900c410727b3b39f9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173582"
---
# <a name="compiler-warning-level-2-c4285"></a>Avertissement du compilateur (niveau 2) C4285

le type de retour de’identifier :: Operator-> 'est récurrent si appliqué à l’aide de la notation infix

La fonction **Operator-> ()** spécifiée ne peut pas retourner le type pour lequel elle est définie ou une référence au type pour lequel elle est définie.

L’exemple suivant génère l’C4285 :

```cpp
// C4285.cpp
// compile with: /W2
class C
{
public:
    C operator->();   // C4285
   // C& operator->();  C4285, also
};

int main()
{
}
```
