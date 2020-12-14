---
description: 'En savoir plus sur : erreur du compilateur C3283'
title: Erreur du compilateur C3283
ms.date: 11/04/2016
f1_keywords:
- C3283
helpviewer_keywords:
- C3283
ms.assetid: c51d912c-cde3-4928-904e-26734c8954ce
ms.openlocfilehash: 577f3fa6c3316c58bf6e9dca94b22a168a451b17
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311875"
---
# <a name="compiler-error-c3283"></a>Erreur du compilateur C3283

'type' : une interface ne peut pas avoir de constructeur d’instance

Une [interface](../../extensions/interface-class-cpp-component-extensions.md) CLR ne peut pas avoir de constructeur d’instance.  Un constructeur statique est autorisé.

L’exemple suivant génère l’erreur C3283 :

```cpp
// C3283.cpp
// compile with: /clr
interface class I {
   I();   // C3283
};
```

Solution possible :

```cpp
// C3283b.cpp
// compile with: /clr /c
interface class I {
   static I(){}
};
```
