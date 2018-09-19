---
title: Erreur du compilateur C2943 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2943
dev_langs:
- C++
helpviewer_keywords:
- C2943
ms.assetid: ede6565e-d892-44c0-8eee-c69545f3be2e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4849e138cdbef97595d4aa1bbb45c277e7feb96a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047328"
---
# <a name="compiler-error-c2943"></a>Erreur du compilateur C2943

'classe' : type-class-id redéfini comme argument de type d’un modèle

Vous ne pouvez pas utiliser une classe générique ni de modèle à la place d’un symbole comme argument de type générique ou d’un modèle.

L’exemple suivant génère l’erreur C2943 :

```
// C2943.cpp
// compile with: /c
template<class T>
class List {};

template<class List<int> > class MyList;   // C2943
template<class T >  class MyList;
```