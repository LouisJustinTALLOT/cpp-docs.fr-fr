---
title: Erreur du compilateur C2380 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2380
dev_langs:
- C++
helpviewer_keywords:
- C2380
ms.assetid: 717b1e6e-ddfe-4bac-a5f3-7f9a4dcb1572
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e4dae59f686a1d2fe9f80a4f3f4c47ea6b7ea2d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065476"
---
# <a name="compiler-error-c2380"></a>Erreur du compilateur C2380

type (s) précédant 'identificateur' (constructeur avec type de retour ou redéfinition non conforme du nom de classe actif ?)

Un constructeur retourne une valeur ou redéfinit le nom de classe.

L’exemple suivant génère l’erreur C2326 :

```
// C2380.cpp
// compile with: /c
class C {
public:
   int C();   // C2380, specifies an int return
   int C;   // C2380, redefinition of i
   C();   // OK
};
```