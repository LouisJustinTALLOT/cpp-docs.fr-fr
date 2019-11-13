---
title: Avertissement du compilateur (niveau 1) C4677
ms.date: 11/04/2016
f1_keywords:
- C4677
helpviewer_keywords:
- C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
ms.openlocfilehash: 8567e7392537507a25121977448ac47ec079316b
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051370"
---
# <a name="compiler-warning-level-1-c4677"></a>Avertissement du compilateur (niveau 1) C4677

'fonction' : la signature d’un membre non privé contient un type privé d’assembly’private_type'

Un type qui a une accessibilité publique en dehors de l’assembly utilise un type qui a un accès privé en dehors de l’assembly. Un composant qui fait référence au type d’assembly public ne pourra pas utiliser le membre de type ou les membres qui référencent le type privé de l’assembly.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4677.

```cpp
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