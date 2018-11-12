---
title: Erreur du compilateur C2396
ms.date: 11/04/2016
f1_keywords:
- C2396
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
ms.openlocfilehash: d320f78937fc60910bbed4a5b1b89841ea674fb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438087"
---
# <a name="compiler-error-c2396"></a>Erreur du compilateur C2396

' your_type::operator '' : functionnot de conversion définie par l’utilisateur CLR ou WinRT valide. La conversion doit être opérée depuis ou vers : 'T^', 'T^%', 'T^&', où T = 'your_type'

Une fonction de conversion dans un type managé ou Windows Runtime ne disposait pas d'au moins un paramètre dont le type est le même que le type qui contient la fonction de conversion.

L'exemple suivant génère l'erreur C2396 et montre comment la corriger :

```
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