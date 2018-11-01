---
title: Erreur du compilateur C3246
ms.date: 11/04/2016
f1_keywords:
- C3246
helpviewer_keywords:
- C3246
ms.assetid: ad85224a-e540-479b-a5eb-a3bc3964c30b
ms.openlocfilehash: 9e24fc28f84bfacb7478d700047c4eb1363247de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451270"
---
# <a name="compiler-error-c3246"></a>Erreur du compilateur C3246

'classe' : ne peut pas hériter de 'type', car il a été déclaré comme 'sealed'

Une classe marquée [sealed](../../windows/sealed-cpp-component-extensions.md) ne peut pas être la classe de base d’autres classes.

L’exemple suivant génère l’erreur C3246 :

```
// C3246_2.cpp
// compile with: /clr /LD
ref class X sealed {};

ref class Y : public X {}; // C3246
```
