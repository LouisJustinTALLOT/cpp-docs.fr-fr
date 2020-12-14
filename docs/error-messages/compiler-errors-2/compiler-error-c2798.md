---
description: 'En savoir plus sur : erreur du compilateur C2798'
title: Erreur du compilateur C2798
ms.date: 11/04/2016
f1_keywords:
- C2798
helpviewer_keywords:
- C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
ms.openlocfilehash: d3a78eaf09797d658c64b5659dcd0e05191fab1c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297588"
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
