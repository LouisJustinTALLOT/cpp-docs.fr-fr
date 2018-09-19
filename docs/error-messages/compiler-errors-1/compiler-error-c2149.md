---
title: Erreur du compilateur C2149 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2149
dev_langs:
- C++
helpviewer_keywords:
- C2149
ms.assetid: 7a106dab-d79f-41b9-85be-f36e86e4d2ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38ebb710cc9f4d5f546c40d84909dbe23805f2f7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094921"
---
# <a name="compiler-error-c2149"></a>Erreur du compilateur C2149

'identificateur' : un champ de bits nommé ne peut pas avoir une largeur égale à zéro

Les champs de bits ne peuvent avoir une largeur égale à zéro que s’ils ne portent pas de nom.

L’exemple suivant génère l’erreur C2149 :

```
// C2149.cpp
// compile with: /c
struct C {
   int i : 0;   // C2149
   int j : 2;   // OK
};
```