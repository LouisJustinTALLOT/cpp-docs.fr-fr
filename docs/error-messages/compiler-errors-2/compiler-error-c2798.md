---
title: Erreur du compilateur C2798
ms.date: 11/04/2016
f1_keywords:
- C2798
helpviewer_keywords:
- C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
ms.openlocfilehash: 6eed1f1aad0783f9e1d5f4126847b54f6b7278e0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739200"
---
# <a name="compiler-error-c2798"></a>Erreur du compilateur C2798

'Super :: Member’est ambigu

Plusieurs structures héritées contiennent le membre que vous avez référencé à l’aide de [Super](../../cpp/super.md). Vous pouvez corriger l’erreur de l’une des deux opérations suivantes :

- Suppression de B1 ou B2 de la liste d’héritage de D.

- Modification du nom du membre de données dans B1 ou B2.

L’exemple suivant génère l’C2798 :

```cpp
// C2798.cpp
struct B1 {
   int i;
};

struct B2 {
   int i;
};

struct D : B1, B2 {
   void g() {
      __super::i = 4; // C2798
   }
};
```
