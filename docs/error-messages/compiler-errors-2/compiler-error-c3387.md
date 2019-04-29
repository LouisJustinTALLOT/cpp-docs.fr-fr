---
title: Erreur du compilateur C3387
ms.date: 11/04/2016
f1_keywords:
- C3387
helpviewer_keywords:
- C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
ms.openlocfilehash: bd783d9510b1699b33f108a4ce8d8c491028b758
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328703"
---
# <a name="compiler-error-c3387"></a>Erreur du compilateur C3387

'membre' : __declspec (dllexport) /\__declspec (dllimport) ne peut pas être appliqué à un membre d’un managée ou WinRT type

Le `dllimport` et [dllexport](../../cpp/dllexport-dllimport.md) `__declspec` modificateurs ne sont pas valides sur les membres d’un objet ou de type Windows Runtime.

L'exemple suivant génère l'erreur C3387 et montre comment la corriger :

```
// C3387a.cpp
// compile with: /clr /c
ref class X2 {
   void __declspec(dllexport) mf() {   // C3387
   // try the following line instead
   // void mf() {
   }
};
```