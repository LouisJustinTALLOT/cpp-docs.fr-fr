---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4722'
title: Avertissement du compilateur (niveau 1) C4722
ms.date: 11/04/2016
f1_keywords:
- C4722
helpviewer_keywords:
- C4722
ms.assetid: d8660710-f67b-4f59-a5fd-59259475529e
ms.openlocfilehash: b147eb63592235f4246c9826419aca77357df31a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328102"
---
# <a name="compiler-warning-level-1-c4722"></a>Avertissement du compilateur (niveau 1) C4722

'fonction' : aucun retour du destructeur, fuite de mémoire possible

Le flux de contrôle se termine dans un destructeur. Le thread ou la totalité du programme va se terminer et les ressources allouées risquent de ne pas être libérées.  En outre, si un destructeur est appelé pour le déroulement de pile pendant le traitement de l’exception, le comportement du fichier exécutable est indéfini.

Pour résoudre ce problème, supprimez l’appel de fonction qui provoque le non-retour du destructeur.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4722 :

```cpp
// C4722.cpp
// compile with: /O1 /W1 /c
#include <stdlib.h>
class C {
public:
   C();
   ~C() { exit(1); };   // C4722
};

extern void func (C*);

void Test(){
   C x;
   func(&x);
   // control will not leave Test because destructor will exit
}
```
