---
description: 'En savoir plus sur : erreur du compilateur C3387'
title: Erreur du compilateur C3387
ms.date: 11/04/2016
f1_keywords:
- C3387
helpviewer_keywords:
- C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
ms.openlocfilehash: febd47004026a7e22ca576c153ee8cf1506c3e1d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285550"
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
