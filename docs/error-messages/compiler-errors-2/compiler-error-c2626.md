---
title: Erreur du compilateur C2626
ms.date: 11/04/2016
f1_keywords:
- C2626
helpviewer_keywords:
- C2626
ms.assetid: 4c283ad0-251b-4571-bc18-468b9836746f
ms.openlocfilehash: 434858991c23345e2a6c174c8f323000d42b9b6b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565177"
---
# <a name="compiler-error-c2626"></a>Erreur du compilateur C2626

'identificateur' : une donnée membre privé ou protégé n'est pas autorisé dans un struct ou union anonyme

Un membre d'un struct ou d'une union anonyme doit avoir un accès public.

L'exemple suivant génère l'erreur C2626 :

```
// C2626.cpp
int main() {
   union {
   protected:
      int j;     // C2626, j is protected
   private:
      int k;     // C2626, k is private
   };
}
```

Pour résoudre ce problème, supprimez toutes les balises privées ou protégées :

```
// C2626b.cpp
int main() {
   union {
   public:
      int i;   // OK, i is public
   };
}
```