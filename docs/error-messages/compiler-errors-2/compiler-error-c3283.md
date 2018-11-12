---
title: Erreur du compilateur C3283
ms.date: 11/04/2016
f1_keywords:
- C3283
helpviewer_keywords:
- C3283
ms.assetid: c51d912c-cde3-4928-904e-26734c8954ce
ms.openlocfilehash: 873ab4d4b016fa392b7a2f64fdd14c3e93f2e22d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516088"
---
# <a name="compiler-error-c3283"></a>Erreur du compilateur C3283

'type' : une interface ne peut pas avoir de constructeur d’instance

Une [interface](../../windows/interface-class-cpp-component-extensions.md) CLR ne peut pas avoir de constructeur d’instance.  Un constructeur statique est autorisé.

L’exemple suivant génère l’erreur C3283 :

```
// C3283.cpp
// compile with: /clr
interface class I {
   I();   // C3283
};
```

Solution possible :

```
// C3283b.cpp
// compile with: /clr /c
interface class I {
   static I(){}
};
```