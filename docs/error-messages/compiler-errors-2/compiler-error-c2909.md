---
title: Erreur du compilateur C2909 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2909
dev_langs:
- C++
helpviewer_keywords:
- C2909
ms.assetid: 1c9df8ae-925d-4002-a5f8-a71413c45f9e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f611a026d0a969f49eaf2dcd93ba081bae052d10
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030883"
---
# <a name="compiler-error-c2909"></a>Erreur du compilateur C2909

'identifier' : l’instanciation explicite d’un modèle de fonction exige un type de retour

Une instanciation explicite d’un modèle de fonction nécessite la spécification explicite de son type de retour. La spécification d’un type de retour implicite ne fonctionne pas.

L’exemple suivant génère l’erreur C2909 :

```
// C2909.cpp
// compile with: /c
template<class T> int f(T);
template f<int>(int);         // C2909
template int f<int>(int);   // OK
```