---
title: Erreur du compilateur C2850
ms.date: 11/04/2016
f1_keywords:
- C2850
helpviewer_keywords:
- C2850
ms.assetid: f3efe86c-4168-4e76-a133-3f8314c69f51
ms.openlocfilehash: 0a87767bb9194a0a9858dd1734abbe516ffcfac0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758500"
---
# <a name="compiler-error-c2850"></a>Erreur du compilateur C2850

'Construct' : uniquement autorisé au niveau de la portée du fichier ; ne peut pas se trouver dans une construction imbriquée

Les constructions, telles que certains pragmas, ne peuvent apparaître qu’au niveau de la portée globale.

L’exemple suivant génère l’C2850 :

```cpp
// C2850.cpp
// compile with: /c /Yc
// try the following line instead
// #pragma hdrstop
namespace X {
   #pragma hdrstop   // C2850
};
```
