---
title: Erreur du compilateur C2396
ms.date: 11/04/2016
f1_keywords:
- C2396
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
ms.openlocfilehash: d320f78937fc60910bbed4a5b1b89841ea674fb7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303513"
---
# <a name="compiler-error-c2396"></a>Erreur du compilateur C2396

'your_type::operator'type'' : CLR ou WinRT conversion définie par l’utilisateur functionnot valide. Doit soit opérée depuis ou vers : ' T ^', ' t ^ %', ' t ^ &', où T = 'your_type'

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