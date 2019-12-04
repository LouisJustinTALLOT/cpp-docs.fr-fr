---
title: Erreur du compilateur C2626
ms.date: 11/04/2016
f1_keywords:
- C2626
helpviewer_keywords:
- C2626
ms.assetid: 4c283ad0-251b-4571-bc18-468b9836746f
ms.openlocfilehash: 339d48265bdc1f68ea4e18fadfde48fca956dd1f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754743"
---
# <a name="compiler-error-c2626"></a>Erreur du compilateur C2626

'identificateur' : une donnée membre privé ou protégé n'est pas autorisé dans un struct ou union anonyme

Un membre d'un struct ou d'une union anonyme doit avoir un accès public.

L'exemple suivant génère l'erreur C2626 :

```cpp
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

Pour résoudre ce problème, supprimez toutes les étiquettes privées ou protégées :

```cpp
// C2626b.cpp
int main() {
   union {
   public:
      int i;   // OK, i is public
   };
}
```
