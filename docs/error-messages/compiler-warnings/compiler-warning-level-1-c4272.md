---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4272'
title: Avertissement du compilateur (niveau 1) C4272
ms.date: 11/04/2016
f1_keywords:
- C4272
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
ms.openlocfilehash: a44e3a4121c1d01b15af47b0b4eefb1f982423bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266115"
---
# <a name="compiler-warning-level-1-c4272"></a>Avertissement du compilateur (niveau 1) C4272

'fonction' : est marqué __declspec (dllimport); la Convention d’appel Native doit être spécifiée lors de l’importation d’une fonction.

L’exportation d’une fonction marquée avec la Convention d’appel [__clrcall](../../cpp/clrcall.md) est une erreur et le compilateur émet cet avertissement si vous tentez d’importer une fonction marquée `__clrcall` .

L’exemple suivant génère l’C4272 :

```cpp
// C4272.cpp
// compile with: /c /W1 /clr
__declspec(dllimport) void __clrcall Test();   // C4272
__declspec(dllimport) void Test2();   // OK
```
