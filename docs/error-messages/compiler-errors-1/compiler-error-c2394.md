---
description: 'En savoir plus sur : erreur du compilateur C2394'
title: Erreur du compilateur C2394
ms.date: 11/04/2016
f1_keywords:
- C2394
helpviewer_keywords:
- C2394
ms.assetid: 653fa9a0-29b3-48aa-bc01-82f98f717a2b
ms.openlocfilehash: 116ab480c5a72c18bfa551e582fb797d3c216d6e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194864"
---
# <a name="compiler-error-c2394"></a>Erreur du compilateur C2394

'your_type :: operator’op' " : CLR ou WinRToperator non valide. Au moins un paramètre doit être de l’un des types suivants : 't ^ ', 't ^% ', 't ^& ', où T = 'your_type'

Un opérateur dans un type managé ou Windows Runtime ne disposait pas d'au moins un paramètre dont le type est le même que le type de la valeur de retour de l'opérateur.

L'exemple suivant génère l'erreur C2394 :

```cpp
// C2394.cpp
// compile with: /clr /c
ref struct Y {
   static Y^ operator -(int i, char c);   // C2394

   // OK
   static Y^ operator -(Y^ hY, char c);
   // or
   static Y^ operator -(int i, Y^& rhY);
};
```
