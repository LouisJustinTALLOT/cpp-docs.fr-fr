---
title: Erreur du compilateur C2571 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2571
dev_langs:
- C++
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30cc078251d0511da77e08690db275a788973ffb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067933"
---
# <a name="compiler-error-c2571"></a>Erreur du compilateur C2571

'fonction' : fonction virtuelle ne peut pas figurer dans l’union 'union'

Une union est déclarée avec une fonction virtuelle. Vous pouvez déclarer une fonction virtuelle uniquement dans une classe ou structure.  Solutions possibles :

1. Modifier l’union pour une classe ou structure.

1. Rendez la fonction non virtuelle.

L’exemple suivant génère l’erreur C2571 :

```
// C2571.cpp
// compile with: /c
union A {
   virtual void func1();   // C2571
   void func2();   // OK
};
```