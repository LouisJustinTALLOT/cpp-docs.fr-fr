---
description: 'En savoir plus sur : erreur du compilateur C2850'
title: Erreur du compilateur C2850
ms.date: 11/04/2016
f1_keywords:
- C2850
helpviewer_keywords:
- C2850
ms.assetid: f3efe86c-4168-4e76-a133-3f8314c69f51
ms.openlocfilehash: 820aa0e12db5ffe7e6d7b7bf0e87282f53e8477c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97260161"
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
