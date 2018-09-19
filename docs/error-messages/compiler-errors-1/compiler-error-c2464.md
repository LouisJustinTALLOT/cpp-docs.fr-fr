---
title: Erreur du compilateur C2464 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2464
dev_langs:
- C++
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff74085364d6638772ab2376aace93fea741056b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103139"
---
# <a name="compiler-error-c2464"></a>Erreur du compilateur C2464

'identificateur' : Impossible d’utiliser 'new' pour allouer une référence

Un identificateur de référence a été alloué avec le `new` opérateur. Références ne sont pas des objets de mémoire, par conséquent, `new` ne peut pas retourner un pointeur vers les. Utilisez la syntaxe de déclaration de variable standard pour déclarer une référence.

L’exemple suivant génère l’erreur C2464 :

```
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```