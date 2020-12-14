---
description: 'En savoir plus sur : erreur du compilateur C2299'
title: Erreur du compilateur C2299
ms.date: 11/04/2016
f1_keywords:
- C2299
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
ms.openlocfilehash: eb96829c4e16153a0a304a5b2a9640d4591dec3f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235097"
---
# <a name="compiler-error-c2299"></a>Erreur du compilateur C2299

'fonction' : changement de comportement : une spécialisation explicite ne peut pas être un constructeur de copie ou un opérateur d’assignation de copie

Cette erreur peut également être générée en raison du travail de mise en conformité du compilateur pour Visual Studio 2005 : les versions antérieures de Visual C++ autorisées des spécialisations explicites pour un constructeur de copie ou un opérateur d’assignation de copie.

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
