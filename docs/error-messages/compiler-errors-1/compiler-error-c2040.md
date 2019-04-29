---
title: Erreur du compilateur C2040
ms.date: 11/04/2016
f1_keywords:
- C2040
helpviewer_keywords:
- C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
ms.openlocfilehash: b45ec25f1ed516ae73b242fdcc7c66f68c92f724
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387108"
---
# <a name="compiler-error-c2040"></a>Erreur du compilateur C2040

'opérateur' : les niveaux d'indirection de 'identificateur1' et de 'identificateur2' sont différents

Une expression impliquant les opérandes spécifiés possède des types d'opérande incompatibles ou convertis implicitement. Si les deux opérandes sont arithmétiques ou si les deux sont non arithmétiques (tels qu’un tableau ou un pointeur), ils sont utilisés sans modification. Si un opérande est arithmétique et que l’autre ne l’est pas, l’opérande arithmétique est converti vers le type de l’opérande non arithmétique.

Cet exemple génère l'erreur C2040 et montre comment la corriger.

```
// C2040.cpp
// Compile by using: cl /c /W3 C2040.cpp
bool test() {
   char c = '3';
   return c == "3"; // C2446, C2040
   // return c == '3'; // OK
}
```