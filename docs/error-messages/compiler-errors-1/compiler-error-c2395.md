---
title: Erreur du compilateur C2395
ms.date: 11/04/2016
f1_keywords:
- C2395
helpviewer_keywords:
- C2395
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
ms.openlocfilehash: 2ac59856770b04dd3c4ea14360e0a83dd99f2150
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744938"
---
# <a name="compiler-error-c2395"></a>Erreur du compilateur C2395

'your_type::operator'op'' : opérateur CLR ou WinRT non valide. Au moins un paramètre doit être de l’un des types suivants : 't', 't% ', 't & ', 't ^ ', 't ^% ', 't ^ & ', où T = 'your_type'

Un opérateur dans un type managé ou Windows Runtime ne disposait pas d'au moins un paramètre dont le type est le même que le type de la valeur de retour de l'opérateur.

L'exemple suivant génère l'erreur C2395 et montre comment la corriger :

```cpp
// C2395.cpp
// compile with: /clr /c
value struct V {
   static V operator *(int i, char c);   // C2395

   // OK
   static V operator *(V v, char c);
   // or
   static V operator *(int i, V& rv);
};
```
