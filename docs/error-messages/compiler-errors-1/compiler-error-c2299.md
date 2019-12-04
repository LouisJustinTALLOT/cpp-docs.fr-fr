---
title: Erreur du compilateur C2299
ms.date: 11/04/2016
f1_keywords:
- C2299
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
ms.openlocfilehash: 009a441ec610053176e79126d9f2663f29b26bc6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759046"
---
# <a name="compiler-error-c2299"></a>Erreur du compilateur C2299

'fonction' : changement de comportement : une spécialisation explicite ne peut pas être un constructeur de copie ou un opérateur d’assignation de copie

Cette erreur peut également être générée en raison du travail de mise en conformité du compilateur pour Visual Studio 2005 : les versions précédentes de Visual C++ autorisaient les spécialisations explicites pour un constructeur de copie ou un opérateur d’assignation de copie.

Pour résoudre les C2299, ne faites pas du constructeur de copie ou de l’opérateur d’assignation une fonction de modèle, mais plutôt une fonction sans modèle qui prend un type de classe. Tout code qui appelle le constructeur de copie ou l’opérateur d’assignation en spécifiant explicitement les arguments template doit supprimer les arguments template.

L’exemple suivant génère l’C2299 :

```cpp
// C2299.cpp
// compile with: /c
class C {
   template <class T>
   C (T t);

   template <> C (const C&);   // C2299
   C (const C&);   // OK
};
```
