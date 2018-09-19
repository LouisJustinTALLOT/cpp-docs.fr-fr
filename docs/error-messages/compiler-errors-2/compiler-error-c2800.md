---
title: Erreur du compilateur C2800 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2800
dev_langs:
- C++
helpviewer_keywords:
- C2800
ms.assetid: a2f1a590-9fe6-44cb-ad09-b4505ef47c6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 23441361ea0c8dbc241f5bf655186f0399b6b42f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016375"
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