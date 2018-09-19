---
title: Erreur du compilateur C2617 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2617
dev_langs:
- C++
helpviewer_keywords:
- C2617
ms.assetid: d6a435d2-7d95-4dbf-ad4a-abe4744f63e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 14435dd5620a144f1b1dd53836c583acefe309c9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109871"
---
# <a name="compiler-error-c2617"></a>Erreur du compilateur C2617

'fonction' : instruction return incohérente

La fonction spécifiée n’a pas un type de retour déclaré et une précédente retourner l’instruction n’a pas fourni une valeur.

L’exemple suivant génère l’erreur C2617 :

```
// C2617.cpp
int i;
func() {   // no return type prototype
   if( i ) return;   // no return value
   else return( 1 );   // C2617 detected on this line
}
```

Solution possible :

```
// C2617b.cpp
// compile with: /c
int i;
int MyF() {
   if (i)
      return 0;
   else
      return (1);
}
```