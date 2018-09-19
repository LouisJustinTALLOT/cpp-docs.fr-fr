---
title: Erreur du compilateur C2879 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2879
dev_langs:
- C++
helpviewer_keywords:
- C2879
ms.assetid: ac92b645-2394-49de-8632-43d44e0553ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 632142ea0efd8a9d009f18b898213cfa92514b16
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042474"
---
# <a name="compiler-error-c2879"></a>Erreur du compilateur C2879

'symbol' : seul un espace de noms existant peut être renommé par une définition d’alias d’espace de noms

Vous ne pouvez pas créer un [alias d’espace de noms](../../cpp/namespaces-cpp.md#namespace_aliases) pour un symbole autre qu’un espace de noms.

L’exemple suivant génère l’erreur C2879 :

```
// C2879.cpp
int main() {
   int i;
   namespace A = i;   // C2879 i is not a namespace
}
```