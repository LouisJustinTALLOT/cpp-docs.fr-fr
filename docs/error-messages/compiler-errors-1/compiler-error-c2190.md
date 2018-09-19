---
title: Erreur du compilateur C2190 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2190
dev_langs:
- C++
helpviewer_keywords:
- C2190
ms.assetid: 34e15f85-d979-4948-80fc-46c414508a70
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7fdca31d191700057a255d99c6d943f4b4e6a981
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092841"
---
# <a name="compiler-error-c2190"></a>Erreur du compilateur C2190

première liste de paramètres plu grande que la seconde

Une fonction C a été déclarée une deuxième fois avec une liste de paramètres plus courte. C ne prend pas en charge les fonctions surchargées.

L’exemple suivant génère l’erreur C2190 :

```
// C2190.c
// compile with: /Za /c
void func( int, float );
void func( int  );   // C2190, different parameter list
void func2( int  );   // OK
```