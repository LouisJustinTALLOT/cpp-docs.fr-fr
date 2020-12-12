---
description: 'En savoir plus sur : erreur du compilateur C2380'
title: Erreur du compilateur C2380
ms.date: 11/04/2016
f1_keywords:
- C2380
helpviewer_keywords:
- C2380
ms.assetid: 717b1e6e-ddfe-4bac-a5f3-7f9a4dcb1572
ms.openlocfilehash: 4455fef072b6d8f686d5f43130db8d02aba69fd1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174687"
---
# <a name="compiler-error-c2380"></a>Erreur du compilateur C2380

type (s) précédant’identifier' (constructeur avec type de retour ou redéfinition non conforme de Class-Name actuel ?)

Un constructeur retourne une valeur ou redéfinit le nom de la classe.

L’exemple suivant génère l’erreur C2326 :

```cpp
// C2380.cpp
// compile with: /c
class C {
public:
   int C();   // C2380, specifies an int return
   int C;   // C2380, redefinition of i
   C();   // OK
};
```
