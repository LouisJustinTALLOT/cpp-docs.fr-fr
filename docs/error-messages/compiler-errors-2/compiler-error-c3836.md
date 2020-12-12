---
description: 'En savoir plus sur : erreur du compilateur C3836'
title: Erreur du compilateur C3836
ms.date: 11/04/2016
f1_keywords:
- C3836
helpviewer_keywords:
- C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
ms.openlocfilehash: c7e05bbf95facf5b8552b4442138cc38b86703c0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180875"
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
