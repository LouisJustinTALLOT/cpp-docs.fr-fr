---
title: Erreur du compilateur C3386
ms.date: 11/04/2016
f1_keywords:
- C3386
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
ms.openlocfilehash: ca78433fcb835ad60b553be28ea746f0f880b315
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743248"
---
# <a name="compiler-error-c3386"></a>Erreur du compilateur C3386

'type' : __declspec (dllexport)/\__declspec (dllimport) ne peut pas être appliqué à un WinRTtype ou managé

Les modificateurs de `__declspec` `dllimport` et [dllexport](../../cpp/dllexport-dllimport.md) ne sont pas valides sur un type managé ou Windows Runtime.

L'exemple suivant génère l'erreur C3386 et montre comment la corriger :

```cpp
// C3386.cpp
// compile with: /clr /c
ref class __declspec(dllimport) X1 {   // C3386
// try the following line instead
// ref class X1 {
};
```
