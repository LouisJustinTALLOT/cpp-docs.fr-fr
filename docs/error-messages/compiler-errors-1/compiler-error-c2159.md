---
title: Erreur du compilateur C2159 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2159
dev_langs:
- C++
helpviewer_keywords:
- C2159
ms.assetid: 925a2cbd-43c9-45ee-a373-84004350b380
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c33f8faebbca2999a893ceb1d0650ba89ee74bf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048485"
---
# <a name="compiler-error-c2159"></a>Erreur du compilateur C2159

plus d'une classe de stockage spécifiée

Une déclaration contient plusieurs classes de stockage.

L’exemple suivant génère l’erreur C2159 :

```
// C2159.cpp
// compile with: /c
static int i;   // OK
extern static int i;   // C2159
```