---
title: Erreur du compilateur C2790
ms.date: 11/04/2016
f1_keywords:
- C2790
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
ms.openlocfilehash: c63fe7bb3686692818337e890de7fe4c80a18158
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739556"
---
# <a name="compiler-error-c2790"></a>Erreur du compilateur C2790

'Super' : ce mot clé ne peut être utilisé que dans le corps d’une fonction membre de classe

Ce message d’erreur s’affiche si l’utilisateur tente d’utiliser le mot clé [Super](../../cpp/super.md) en dehors du contexte d’une fonction membre.

L’exemple suivant génère l’C2790 :

```cpp
// C2790.cpp
void f() {
   __super::g();   // C2790
}
```
