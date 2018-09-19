---
title: Erreur du compilateur C2503 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2503
dev_langs:
- C++
helpviewer_keywords:
- C2503
ms.assetid: da86cc89-fd04-400b-aa8d-a5ffaf7e3918
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b57ce28851d3948db5c14889fceb3594dbe2617a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048927"
---
# <a name="compiler-error-c2503"></a>Erreur du compilateur C2503

'class' : les classes de base ne peut pas contenir de tableaux de taille zéro

Une classe de base ou une structure contient un tableau de taille zéro. Un tableau dans une classe doit avoir au moins un élément.

L’exemple suivant génère l’erreur C2503 :

```
// C2503.cpp
// compile with: /c
class A {
   public:
   int array [];
};

class B : A {};    // C2503

class C {
public:
   int array [10];
};

class D : C {};
```