---
title: Avertissement du compilateur (niveau 1) C4272
ms.date: 11/04/2016
f1_keywords:
- C4272
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
ms.openlocfilehash: 747b9e60ad2b8b0036c6eac50d44c2d70277384f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163117"
---
# <a name="compiler-warning-level-1-c4272"></a>Avertissement du compilateur (niveau 1) C4272

'fonction' : est marqué __declspec (dllimport); la Convention d’appel Native doit être spécifiée lors de l’importation d’une fonction.

L’exportation d’une fonction marquée avec la Convention d’appel [__clrcall](../../cpp/clrcall.md) est une erreur et le compilateur émet cet avertissement si vous tentez d’importer une fonction marquée `__clrcall`.

L’exemple suivant génère l’C4272 :

```cpp
// C4272.cpp
// compile with: /c /W1 /clr
__declspec(dllimport) void __clrcall Test();   // C4272
__declspec(dllimport) void Test2();   // OK
```
