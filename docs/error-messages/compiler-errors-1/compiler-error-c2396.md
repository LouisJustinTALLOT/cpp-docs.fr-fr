---
title: Erreur du compilateur C2396
ms.date: 11/04/2016
f1_keywords:
- C2396
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
ms.openlocfilehash: 5020732ce5186ee1c6e9d2ea13f452fe9988bdfa
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744834"
---
# <a name="compiler-error-c2396"></a>Erreur du compilateur C2396

'your_type :: operator’type' ' : le CLR ou la conversion définie par l’utilisateur WinRT functionnot est valide. Vous devez convertir ou convertir en : 't ^ ', 't ^% ', 't ^ & ', où T = 'your_type'

Une fonction de conversion dans un type managé ou Windows Runtime ne disposait pas d'au moins un paramètre dont le type est le même que le type qui contient la fonction de conversion.

L'exemple suivant génère l'erreur C2396 et montre comment la corriger :

```cpp
// C2396.cpp
// compile with: /clr /c

ref struct Y {
   static operator int(char c);   // C2396

   // OK
   static operator int(Y^ hY);
   // or
   static operator Y^(char c);
};
```
