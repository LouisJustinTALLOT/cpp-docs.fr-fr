---
title: Avertissement du compilateur (niveau 1) C4461
ms.date: 11/04/2016
f1_keywords:
- C4461
helpviewer_keywords:
- C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
ms.openlocfilehash: 195e5532b6555210077e43ad3086ee3106f3e757
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966012"
---
# <a name="compiler-warning-level-1-c4461"></a>Avertissement du compilateur (niveau 1) C4461

'type' : cette classe a un finaliseur’Finalizer', mais aucun destructeur’dtor'

La présence d’un finaliseur dans un type implique des ressources à supprimer. À moins qu’un finaliseur soit explicitement appelé à partir du destructeur du type, le common language runtime détermine quand exécuter le finaliseur, une fois que votre objet est hors de portée.

Si vous définissez un destructeur dans le type et appelez explicitement le finaliseur à partir du destructeur, vous pouvez exécuter votre finaliseur de manière déterministe.

Pour plus d’informations, consultez [destructeurs et finaliseurs](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4461.

```cpp
// C4461.cpp
// compile with: /W1 /clr /c
ref class A {
protected:
   !A() {}   // C4461
};

// OK
ref struct B {
   ~B() {
      B::!B();
   }

   !B() {}
};
```