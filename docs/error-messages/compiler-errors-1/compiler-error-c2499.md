---
title: Erreur du compilateur C2499
ms.date: 11/04/2016
f1_keywords:
- C2499
helpviewer_keywords:
- C2499
ms.assetid: b323ff4d-b3c1-4bfd-b052-ae7292d53222
ms.openlocfilehash: 29fbb691304f9fc101f2367e014ae1e4e2231ff0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756979"
---
# <a name="compiler-error-c2499"></a>Erreur du compilateur C2499

'classe' : une classe ne peut pas être sa propre classe de base

Vous avez tenté de spécifier la classe que vous définissez en tant que classe de base.

L’exemple suivant génère l’C2499 :

```cpp
// C2499.cpp
// compile with: /c
class CMyClass : public CMyClass {};   // C2499
class CMyClass{};   // OK
```
