---
title: Compilateur avertissement (niveau 1) C4716 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4716
dev_langs:
- C++
helpviewer_keywords:
- C4716
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f7a6fd31ecae4643e947cb4a56897e80010e350
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093400"
---
# <a name="compiler-warning-level-1-c4716"></a>Avertissement du compilateur (niveau 1) C4716

'fonction' doit retourner une valeur

La fonction donnée n’a pas retourné une valeur.

Ne fonctionne qu’avec un type de retour de void peuvent utiliser la commande return sans valeur de retour associée.

Une valeur non définie s’affichera lorsque cette fonction est appelée.

Cet avertissement est automatiquement promu en une erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma warning](../../preprocessor/warning.md).

L’exemple suivant génère C4716 :

```
// C4716.cpp
// compile with: /c /W1
// C4716 expected
#pragma warning(default:4716)
int test() {
   // uncomment the following line to resolve
   // return 0;
}
```