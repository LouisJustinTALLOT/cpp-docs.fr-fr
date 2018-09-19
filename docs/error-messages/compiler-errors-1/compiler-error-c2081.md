---
title: Erreur du compilateur C2081 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2081
dev_langs:
- C++
helpviewer_keywords:
- C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 48f2cdecaea38beed14735bb3f94c8422a28c747
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030454"
---
# <a name="compiler-error-c2081"></a>Erreur du compilateur C2081

'identificateur' : nom non conforme de liste de paramètres formels dans

L’identificateur a causé une erreur de syntaxe.

Cette erreur peut être due à l’aide de l’ancien style pour la liste de paramètres formels. Vous devez spécifier le type de paramètres formels dans la liste de paramètres formels.

L’exemple suivant génère l’erreur C2081 :

```
// C2081.c
void func( int i, j ) {}  // C2081, no type specified for j
```

Solution possible :

```
// C2081b.c
// compile with: /c
void func( int i, int j ) {}
```