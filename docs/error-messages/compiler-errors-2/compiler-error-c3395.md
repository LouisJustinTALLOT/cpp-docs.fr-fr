---
description: 'En savoir plus sur : erreur du compilateur C3395'
title: Erreur du compilateur C3395
ms.date: 11/04/2016
f1_keywords:
- C3395
helpviewer_keywords:
- C3395
ms.assetid: 26a9ebc9-ed97-47ce-b436-19aa2bcf6e50
ms.openlocfilehash: 65db71a9dbc076b21d16f3f0c250c20a9b283daa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321967"
---
# <a name="compiler-error-c3395"></a>Erreur du compilateur C3395

'fonction' : __declspec (dllexport) ne peut pas être appliqué à une fonction avec la \_ Convention d’appel _clrcall

`__declspec(dllexport)` et [__clrcall](../../cpp/clrcall.md) ne sont pas compatibles.  Pour plus d’informations, consultez [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

L’exemple suivant génère l’C3395 :

```cpp
// C3395.cpp
// compile with: /clr /c

__declspec(dllexport) void __clrcall Test(){}   // C3395
void __clrcall Test2(){}   // OK
__declspec(dllexport) void Test3(){}   // OK
```
