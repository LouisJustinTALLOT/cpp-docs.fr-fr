---
title: Avertissement du compilateur (niveau 1) C4677
ms.date: 11/04/2016
f1_keywords:
- C4677
helpviewer_keywords:
- C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
ms.openlocfilehash: 66b8d42b63bcbf328703523c4eeda7a047f4643c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374571"
---
# <a name="compiler-warning-level-1-c4677"></a>Avertissement du compilateur (niveau 1) C4677

'fonction' : signature de membre non privée contient un type privé d’assembly 'type_privé'

Un type qui a une accessibilité publique en dehors de l’assembly utilise un type qui possède un accès privé en dehors de l’assembly. Un composant qui fait référence au type d’assembly public ne sera pas en mesure d’utiliser le type ou les membres qui font référence au type privé d’assembly.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4677 :.

```
// C4677.cpp
// compile with: /clr /c /W1
delegate void TestDel();
public delegate void TestDel2();

public ref class MyClass {
public:
   static event TestDel^ MyClass_Event;   // C4677
   static event TestDel2^ MyClass_Event2;   // OK
};
```