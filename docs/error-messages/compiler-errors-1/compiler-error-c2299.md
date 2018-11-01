---
title: Erreur du compilateur C2299
ms.date: 11/04/2016
f1_keywords:
- C2299
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
ms.openlocfilehash: 4776ddede31dbcebe56a5919fd111f4df7248215
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590006"
---
# <a name="compiler-error-c2299"></a>Erreur du compilateur C2299

'fonction' : changement de comportement : une spécialisation explicite ne peut pas être un constructeur de copie ou l’opérateur d’assignation de copie

Cette erreur peut également être due à la mise en conformité du compilateur pour Visual C++ 2005 : les versions précédentes de Visual C++ autorisaient les spécialisations explicites pour un constructeur de copie ou un opérateur d’assignation de copie.

Pour résoudre C2299, ne faites pas le constructeur de copie ou opérateur d’assignation une fonction de modèle, mais plutôt une fonction sans modèle qui prend un type de classe. Tout code qui appelle le constructeur de copie ou l’opérateur d’assignation en spécifiant explicitement les arguments template doit supprimer les arguments template.

L’exemple suivant génère l’erreur C2299 :

```
// C2299.cpp
// compile with: /c
class C {
   template <class T>
   C (T t);

   template <> C (const C&);   // C2299
   C (const C&);   // OK
};
```