---
title: Erreur du compilateur C3395
ms.date: 11/04/2016
f1_keywords:
- C3395
helpviewer_keywords:
- C3395
ms.assetid: 26a9ebc9-ed97-47ce-b436-19aa2bcf6e50
ms.openlocfilehash: eaf63b42a6c44153a55d8aeb70f4f1174a5c895c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737541"
---
# <a name="compiler-error-c3395"></a>Erreur du compilateur C3395

'fonction' : __declspec (dllexport) ne peut pas être appliqué à une fonction avec la Convention d’appel de _clrcall \_

`__declspec(dllexport)` et [__clrcall](../../cpp/clrcall.md) ne sont pas compatibles.  Pour plus d’informations, consultez [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

L’exemple suivant génère l’C3395 :

```cpp
// C3395.cpp
// compile with: /clr /c

__declspec(dllexport) void __clrcall Test(){}   // C3395
void __clrcall Test2(){}   // OK
__declspec(dllexport) void Test3(){}   // OK
```
