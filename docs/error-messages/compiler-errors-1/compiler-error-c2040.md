---
title: Erreur du compilateur C2040 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2040
dev_langs:
- C++
helpviewer_keywords:
- C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ccfbacff97550e20c0dd0202e0737585ffd39d6d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016466"
---
# <a name="compiler-error-c2040"></a>Erreur du compilateur C2040

'opérateur' : les niveaux d'indirection de 'identificateur1' et de 'identificateur2' sont différents

Une expression impliquant les opérandes spécifiés possède des types d’opérande incompatibles ou convertis implicitement. Si les deux opérandes sont arithmétiques ou si les deux sont non arithmétiques (tels qu'un tableau ou un pointeur), ils sont utilisés sans modification. Si un opérande est arithmétique et que l’autre ne l’est pas, l’opérande arithmétique est converti vers le type de l’opérande non arithmétique.

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