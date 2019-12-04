---
title: Erreur du compilateur C2800
ms.date: 11/04/2016
f1_keywords:
- C2800
helpviewer_keywords:
- C2800
ms.assetid: a2f1a590-9fe6-44cb-ad09-b4505ef47c6a
ms.openlocfilehash: 4c73ef05894f4f9e08c51ca074de40813ef35616
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739194"
---
# <a name="compiler-error-c2800"></a>Erreur du compilateur C2800

'operator opérateur’ne peut pas être surchargé

Les opérateurs suivants ne peuvent pas être surchargés : accès aux membres de classe (`.`), pointeur vers membre (`.*`), résolution de portée (`::`), expression conditionnelle (`? :`) et `sizeof`.

L’exemple suivant génère l’C2800 :

```cpp
// C2800.cpp
// compile with: /c
class C {
   operator:: ();   // C2800
};
```
