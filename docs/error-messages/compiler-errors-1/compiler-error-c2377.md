---
title: Erreur du compilateur C2377 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2377
dev_langs:
- C++
helpviewer_keywords:
- C2377
ms.assetid: f7660965-bf4c-4cd9-8307-1bd7016678a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f3813642503013ecd2ad3be4c01d55f12c837ba
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087032"
---
# <a name="compiler-error-c2377"></a>Erreur du compilateur C2377

'identificateur' : redéfinition ; un typedef ne peut pas être surchargé avec un autre symbole

Un identificateur `typedef` est redéfini.

L’exemple suivant génère l’erreur C2377 :

```
// C2377.cpp
// compile with: /c
typedef int i;
int i;   // C2377
int j;   // OK
```