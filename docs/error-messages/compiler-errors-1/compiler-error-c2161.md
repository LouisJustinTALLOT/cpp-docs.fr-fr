---
title: Erreur du compilateur C2161 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2161
dev_langs:
- C++
helpviewer_keywords:
- C2161
ms.assetid: d6798821-13bb-4e60-924f-85f7bf955387
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac32776c954974f0f2f81789c6e78de894786b73
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051818"
---
# <a name="compiler-error-c2161"></a>Erreur du compilateur C2161

'##' ne peut se trouver à la fin de la définition d’une macro

La définition d’une macro s’est terminée par un opérateur de collage de jeton (##).

L’exemple suivant génère l’erreur C2161 :

```
// C2161.cpp
// compile with: /c
#define mac(a,b) a   // OK
#define mac(a,b) a##   // C2161
```