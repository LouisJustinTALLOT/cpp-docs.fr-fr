---
description: 'En savoir plus sur : erreur du compilateur C2626'
title: Erreur du compilateur C2626
ms.date: 11/04/2016
f1_keywords:
- C2626
helpviewer_keywords:
- C2626
ms.assetid: 4c283ad0-251b-4571-bc18-468b9836746f
ms.openlocfilehash: 1a89d63d18fd029daa98ce1d248da24296ee2d4f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123541"
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
