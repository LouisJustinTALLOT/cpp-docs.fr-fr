---
title: Erreur du compilateur C3387
ms.date: 11/04/2016
f1_keywords:
- C3387
helpviewer_keywords:
- C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
ms.openlocfilehash: 9f083f5c21e494d08374e72155b44ee14719881f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743144"
---
# <a name="compiler-error-c3387"></a>Erreur du compilateur C3387

'membre' : __declspec (dllexport)/\__declspec (dllimport) ne peut pas être appliqué à un membre d’un type managé ou WinRT

Les modificateurs de `__declspec` `dllimport` et [dllexport](../../cpp/dllexport-dllimport.md) ne sont pas valides sur les membres d’un type managé ou Windows Runtime.

L'exemple suivant génère l'erreur C3387 et montre comment la corriger :

```cpp
// C3387a.cpp
// compile with: /clr /c
ref class X2 {
   void __declspec(dllexport) mf() {   // C3387
   // try the following line instead
   // void mf() {
   }
};
```
