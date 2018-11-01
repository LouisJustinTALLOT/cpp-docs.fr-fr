---
title: Erreur du compilateur C2800
ms.date: 11/04/2016
f1_keywords:
- C2800
helpviewer_keywords:
- C2800
ms.assetid: a2f1a590-9fe6-44cb-ad09-b4505ef47c6a
ms.openlocfilehash: e893866a28c124e9e6cbc9663a488f89ac2d291b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516894"
---
# <a name="compiler-error-c2800"></a>Erreur du compilateur C2800

'operator opérateur' ne peut pas être surchargé.

Les opérateurs suivants ne peuvent pas être surchargés : accès au membre de classe (`.`), pointeur vers membre (`.*`), résolution de portée (`::`), expression conditionnelle (`? :`), et `sizeof`.

L’exemple suivant génère l’erreur C2800 :

```
// C2800.cpp
// compile with: /c
class C {
   operator:: ();   // C2800
};
```