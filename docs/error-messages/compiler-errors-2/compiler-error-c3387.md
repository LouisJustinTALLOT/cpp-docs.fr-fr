---
title: Erreur du compilateur C3387
ms.date: 11/04/2016
f1_keywords:
- C3387
helpviewer_keywords:
- C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
ms.openlocfilehash: 8218233bb7a92c699952f7a506f6728386af4d17
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221066"
---
# <a name="compiler-error-c3387"></a>Erreur du compilateur C3387

'membre' : __declspec (dllexport)/ \_ _declspec (dllimport) ne peut pas être appliqué à un membre d’un type managé ou WinRT

Les `dllimport` modificateurs et [dllexport](../../cpp/dllexport-dllimport.md) ne **`__declspec`** sont pas valides sur les membres d’un type managé ou Windows Runtime.

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
