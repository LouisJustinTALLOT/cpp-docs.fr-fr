---
description: 'En savoir plus sur : erreur du compilateur C2040'
title: Erreur du compilateur C2040
ms.date: 11/04/2016
f1_keywords:
- C2040
helpviewer_keywords:
- C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
ms.openlocfilehash: 39e5152e012d793bcc174f5abe451e23f03b60d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175363"
---
# <a name="compiler-error-c2040"></a>Erreur du compilateur C2040

'opérateur' : les niveaux d'indirection de 'identificateur1' et de 'identificateur2' sont différents

Une expression impliquant les opérandes spécifiés possède des types d'opérande incompatibles ou convertis implicitement. Si les deux opérandes sont arithmétiques ou si les deux sont non arithmétiques (tels qu’un tableau ou un pointeur), ils sont utilisés sans modification. Si un opérande est arithmétique et que l’autre ne l’est pas, l’opérande arithmétique est converti vers le type de l’opérande non arithmétique.

Cet exemple génère l'erreur C2040 et montre comment la corriger.

```cpp
// C2040.cpp
// Compile by using: cl /c /W3 C2040.cpp
bool test() {
   char c = '3';
   return c == "3"; // C2446, C2040
   // return c == '3'; // OK
}
```
