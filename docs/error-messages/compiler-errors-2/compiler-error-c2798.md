---
title: Erreur du compilateur C2798 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2798
dev_langs:
- C++
helpviewer_keywords:
- C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88241989d54e1a068b226b59091a381f531dee9e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028855"
---
# <a name="compiler-error-c2798"></a>Erreur du compilateur C2798

'super::membre' est ambigu

Plusieurs structures héritées contiennent le membre que vous avez référencé avec [super](../../cpp/super.md). Vous pouvez corriger l’erreur à l’aide :

- Suppression de B1 ou B2 dans la liste d’héritage de D.

- Modification du nom du membre de données dans B1 ou B2.

L’exemple suivant génère l’erreur C2798 :

```
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