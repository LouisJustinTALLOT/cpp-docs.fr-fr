---
description: 'En savoir plus sur : erreur du compilateur C2272'
title: Erreur du compilateur C2272
ms.date: 11/04/2016
f1_keywords:
- C2272
helpviewer_keywords:
- C2272
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
ms.openlocfilehash: 5a46c68a09eaec9fc33ef4eaa64afaebea411659
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336249"
---
# <a name="compiler-error-c2272"></a>Erreur du compilateur C2272

'fonction' : modificateurs non autorisés sur les fonctions membres statiques

Une **`static`** fonction membre est déclarée avec un spécificateur de modèle de mémoire, tel que [const](../../cpp/const-cpp.md) ou [volatile](../../cpp/volatile-cpp.md), et ces modificateurs ne sont pas autorisés sur les **`static`** fonctions membres.

L’exemple suivant génère l’C2272 :

```cpp
// C2272.cpp
// compile with: /c
class CMyClass {
public:
   static void func1() const volatile;   // C2272  func1 is static
   void func2() const volatile;   // OK
};
```
