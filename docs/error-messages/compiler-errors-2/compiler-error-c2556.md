---
title: Erreur du compilateur C2556 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2556
dev_langs:
- C++
helpviewer_keywords:
- C2556
ms.assetid: fc4399ad-45b3-49fd-be1f-0b13956a595a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 880234d1d11556b8882bfd564fdf64bc587d56ae
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107782"
---
# <a name="compiler-error-c2556"></a>Erreur du compilateur C2556

'identificateur' : les fonctions surchargées ne diffèrent que par le type de retour

Les fonctions surchargées ont des types de retour différents mais la même liste de paramètres. Chaque fonction surchargée doit avoir une liste de paramètres formels distincte.

L’exemple suivant génère l’erreur C2556 :

```
// C2556.cpp
// compile with: /c
class C {
   int func();
   double func();   // C2556
   int func(int i);   // ok parameter lists differ
};
```