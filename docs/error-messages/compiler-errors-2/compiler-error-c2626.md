---
title: Erreur du compilateur C2626 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2626
dev_langs:
- C++
helpviewer_keywords:
- C2626
ms.assetid: 4c283ad0-251b-4571-bc18-468b9836746f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9929da1f0cf9ffd9c70048017fdef1d854c1fcc9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074680"
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