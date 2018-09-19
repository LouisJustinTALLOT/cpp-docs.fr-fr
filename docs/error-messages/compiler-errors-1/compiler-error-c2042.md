---
title: Erreur du compilateur C2042 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2042
dev_langs:
- C++
helpviewer_keywords:
- C2042
ms.assetid: e111788f-41ce-405a-9824-a4c1c26059e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cbc1d0d5ec0781ebf203a2cebcd99a58996c6547
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079997"
---
# <a name="compiler-error-c2042"></a>Erreur du compilateur C2042

les mots clés signed/unsigned s'excluent mutuellement

Les mots clés `signed` et `unsigned` sont utilisés dans une même déclaration.

L’exemple suivant génère l’erreur C2042 :

```
// C2042.cpp
unsigned signed int i;   // C2042
```

Solution possible :

```
// C2042b.cpp
// compile with: /c
unsigned int i;
signed int ii;
```