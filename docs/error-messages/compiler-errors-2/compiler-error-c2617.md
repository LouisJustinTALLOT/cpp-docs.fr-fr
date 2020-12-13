---
description: 'En savoir plus sur : erreur du compilateur C2617'
title: Erreur du compilateur C2617
ms.date: 11/04/2016
f1_keywords:
- C2617
helpviewer_keywords:
- C2617
ms.assetid: d6a435d2-7d95-4dbf-ad4a-abe4744f63e8
ms.openlocfilehash: 3522b9f07911fb674f95f6ae09193f9bc35567e9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338630"
---
# <a name="compiler-error-c2617"></a>Erreur du compilateur C2617

'fonction' : instruction return incohérente

La fonction spécifiée n’a pas de type de retour déclaré et une instruction return précédente n’a pas fourni de valeur.

L’exemple suivant génère l’C2617 :

```cpp
// C2617.cpp
int i;
func() {   // no return type prototype
   if( i ) return;   // no return value
   else return( 1 );   // C2617 detected on this line
}
```

Solution possible :

```cpp
// C2617b.cpp
// compile with: /c
int i;
int MyF() {
   if (i)
      return 0;
   else
      return (1);
}
```
