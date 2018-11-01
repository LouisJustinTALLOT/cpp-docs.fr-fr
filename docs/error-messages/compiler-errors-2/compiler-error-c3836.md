---
title: Erreur du compilateur C3836
ms.date: 11/04/2016
f1_keywords:
- C3836
helpviewer_keywords:
- C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
ms.openlocfilehash: 33860273db07894a9a4d15ba6d578598a18819ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477543"
---
# <a name="compiler-error-c3836"></a>Erreur du compilateur C3836

constructeur statique n’est pas autorisé à avoir une liste d’initialiseurs de membres

Une classe managée ne peut pas avoir un constructeur statique qui possède également une liste d’initialisation de membre. Constructeurs de classe statique sont appelés par le common language runtime pour l’initialisation, l’initialisation des membres de données statiques de classe.

## <a name="example"></a>Exemple

L’exemple suivant génère C3836 :

```
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
