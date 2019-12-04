---
title: Erreur du compilateur C3836
ms.date: 11/04/2016
f1_keywords:
- C3836
helpviewer_keywords:
- C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
ms.openlocfilehash: 9c8a7e761f2ece046d5de5c0e74ee911e5ee550d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741402"
---
# <a name="compiler-error-c3836"></a>Erreur du compilateur C3836

le constructeur statique n’est pas autorisé à avoir une liste d’initialiseurs de membres

Une classe managée ne peut pas avoir un constructeur statique qui a également une liste d’initialisation de membre. Les constructeurs de classes statiques sont appelés par le common language runtime pour effectuer l’initialisation de la classe, en initialisant les membres de données statiques.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3836 :

```cpp
// C3836a.cpp
// compile with: /clr
ref class M
{
   static int s_i;

public:
   static M() :  s_i(1234)   // C3836, delete initializer to resolve
   {
   }
};

int main()
{
}
```
