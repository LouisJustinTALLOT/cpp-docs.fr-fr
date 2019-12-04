---
title: Erreur du compilateur C2909
ms.date: 11/04/2016
f1_keywords:
- C2909
helpviewer_keywords:
- C2909
ms.assetid: 1c9df8ae-925d-4002-a5f8-a71413c45f9e
ms.openlocfilehash: 6c9a40bd271fa04146193e8315e205e293e8a34d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750479"
---
# <a name="compiler-error-c2909"></a>Erreur du compilateur C2909

'identifier' : l’instanciation explicite d’un modèle de fonction exige un type de retour

Une instanciation explicite d’un modèle de fonction nécessite la spécification explicite de son type de retour. La spécification d’un type de retour implicite ne fonctionne pas.

L’exemple suivant génère l’erreur C2909 :

```cpp
// C2909.cpp
// compile with: /c
template<class T> int f(T);
template f<int>(int);         // C2909
template int f<int>(int);   // OK
```
