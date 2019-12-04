---
title: Erreur du compilateur C3298
ms.date: 11/04/2016
f1_keywords:
- C3298
helpviewer_keywords:
- C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
ms.openlocfilehash: d5e9586b026e0092491c80c23f55080354c9e465
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760073"
---
# <a name="compiler-error-c3298"></a>Erreur du compilateur C3298

'contrainte_1' : impossible d’utiliser 'contrainte_2' en tant que contrainte, car 'contrainte_2' a la contrainte ref et 'contrainte_1' a la contrainte de valeur

Vous ne pouvez pas spécifier des caractéristiques mutuellement exclusives pour une contrainte. Par exemple, un paramètre de type générique ne peut pas être limité à la fois à un type valeur et à un type référence.

Pour plus d’informations, consultez [Contraintes sur les paramètres de type générique (C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3298.

```cpp
// C3298.cpp
// compile with: /clr /c
generic<class T, class U>
where T : ref class
where U : T, value class   // C3298
public ref struct R {};
```
