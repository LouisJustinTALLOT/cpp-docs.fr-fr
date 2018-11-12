---
title: Erreur du compilateur C2236
ms.date: 11/04/2016
f1_keywords:
- C2236
helpviewer_keywords:
- C2236
ms.assetid: 0b6771a7-a783-4729-9c3d-7a3339c432cc
ms.openlocfilehash: 988377d2995468c84b86872ab6f2b25f5c3df9f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462645"
---
# <a name="compiler-error-c2236"></a>Erreur du compilateur C2236

jeton 'identificateur' inattendu. N'auriez-vous pas oublié un ';' ?

L'identificateur est déjà défini comme un type et ne peut pas être remplacé par un type défini par l'utilisateur.

L'exemple suivant génère l'erreur C2236 :

```
// C2236.cpp
// compile with: /c
int class A {};  // C2236 "int class" is unexpected
int i;
class B {};
```