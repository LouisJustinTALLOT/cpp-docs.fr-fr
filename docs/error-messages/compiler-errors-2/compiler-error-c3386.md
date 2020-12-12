---
description: 'En savoir plus sur : erreur du compilateur C3386'
title: Erreur du compilateur C3386
ms.date: 11/04/2016
f1_keywords:
- C3386
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
ms.openlocfilehash: 5bc80abe7c43e30c4114d0f3ffd7733c8ea3e9d1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115896"
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
