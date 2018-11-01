---
title: Erreur du compilateur C3913
ms.date: 11/04/2016
f1_keywords:
- C3913
helpviewer_keywords:
- C3913
ms.assetid: a678bfce-9524-470d-9f23-7d08ecb972c8
ms.openlocfilehash: bf83be5e95109c9e7fa0516cde780ca6907416ff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516380"
---
# <a name="compiler-error-c3913"></a>Erreur du compilateur C3913

propriété par défaut doit être indexée.

Une propriété par défaut a été définie de manière incorrecte.

Pour plus d'informations, consultez [property](../../windows/property-cpp-component-extensions.md).

L’exemple suivant génère l’erreur C3913 :

```
// C3913.cpp
// compile with: /clr /c
ref struct X {
   property int default {   // C3913
   // try the following line instead
   // property int default[int] {
      int get(int) { return 0; }
      void set(int, int) {}
   }
};
```