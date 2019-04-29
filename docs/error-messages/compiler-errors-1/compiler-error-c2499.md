---
title: Erreur du compilateur C2499
ms.date: 11/04/2016
f1_keywords:
- C2499
helpviewer_keywords:
- C2499
ms.assetid: b323ff4d-b3c1-4bfd-b052-ae7292d53222
ms.openlocfilehash: 645dd3923e65240de17803a8831a0223ff0e1656
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360552"
---
# <a name="compiler-error-c2499"></a>Erreur du compilateur C2499

'classe' : une classe ne peut pas être sa propre classe de base

Vous avez tenté de spécifier la classe que vous définissez comme classe de base.

L’exemple suivant génère l’erreur C2499 :

```
// C2499.cpp
// compile with: /c
class CMyClass : public CMyClass {};   // C2499
class CMyClass{};   // OK
```