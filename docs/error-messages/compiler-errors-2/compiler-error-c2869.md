---
title: Erreur du compilateur C2869
ms.date: 11/04/2016
f1_keywords:
- C2869
helpviewer_keywords:
- C2869
ms.assetid: 6e30c001-47f3-4101-b9f1-cc542c9fffae
ms.openlocfilehash: 38ac73484814e0089b412938ffc2776872deff3e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614446"
---
# <a name="compiler-error-c2869"></a>Erreur du compilateur C2869

'name' : a déjà été défini pour être un espace de noms

Vous ne pouvez pas réutiliser un nom déjà utilisé comme un espace de noms.

L’exemple suivant génère l’erreur C2869 :

```
// C2869.cpp
// compile with: /c
namespace A { int i; };

class A {};   // C2869, A is already used
```