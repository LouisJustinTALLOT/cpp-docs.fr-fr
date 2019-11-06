---
title: Avertissement du compilateur (niveau 1) C4272
ms.date: 11/04/2016
f1_keywords:
- C4272
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
ms.openlocfilehash: 13c56c2261cd069e7edec63921c198e2bee56c95
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626701"
---
# <a name="compiler-warning-level-1-c4272"></a>Avertissement du compilateur (niveau 1) C4272

'fonction' : est marqué comme _ _ declspec (dllimport); la Convention d’appel Native doit être spécifiée lors de l’importation d’une fonction.

L’exportation d’une fonction marquée avec la Convention d’appel [_ _ clrcall](../../cpp/clrcall.md) est une erreur et le compilateur émet cet avertissement si vous tentez d’importer une fonction marquée `__clrcall`.

L’exemple suivant génère l’C4272 :

```cpp
// C4272.cpp
// compile with: /c /W1 /clr
__declspec(dllimport) void __clrcall Test();   // C4272
__declspec(dllimport) void Test2();   // OK
```