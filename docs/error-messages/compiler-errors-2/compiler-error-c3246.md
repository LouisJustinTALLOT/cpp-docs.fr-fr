---
title: Erreur du compilateur C3246
ms.date: 11/04/2016
f1_keywords:
- C3246
helpviewer_keywords:
- C3246
ms.assetid: ad85224a-e540-479b-a5eb-a3bc3964c30b
ms.openlocfilehash: eb5ba268508922daf00adb49cf611c038db76343
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777443"
---
# <a name="compiler-error-c3246"></a>Erreur du compilateur C3246

'classe' : ne peut pas hériter de 'type', car il a été déclaré comme 'sealed'

Une classe marquée [sealed](../../extensions/sealed-cpp-component-extensions.md) ne peut pas être la classe de base d’autres classes.

L’exemple suivant génère l’erreur C3246 :

```
// C3246_2.cpp
// compile with: /clr /LD
ref class X sealed {};

ref class Y : public X {}; // C3246
```
