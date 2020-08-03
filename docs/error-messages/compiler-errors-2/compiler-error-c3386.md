---
title: Erreur du compilateur C3386
ms.date: 11/04/2016
f1_keywords:
- C3386
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
ms.openlocfilehash: efe882db447b9ebc69d02e3b10d9e484a3cfd8a8
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520446"
---
# <a name="compiler-error-c3386"></a>Erreur du compilateur C3386

> '*type-name*' : `__declspec(dllexport)` / `__declspec(dllimport)` ne peut pas être appliqué à un type managé ou WinRT

Les [`dllimport`](../../cpp/dllexport-dllimport.md) [`dllexport`](../../cpp/dllexport-dllimport.md) **`__declspec`** modificateurs et ne sont pas valides sur un type managé ou Windows Runtime.

L'exemple suivant génère l'erreur C3386 et montre comment la corriger :

```cpp
// C3386.cpp
// compile with: /clr /c
ref class __declspec(dllimport) X1 {   // C3386
// try the following line instead
// ref class X1 {
};
```
