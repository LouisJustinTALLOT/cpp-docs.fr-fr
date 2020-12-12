---
description: 'En savoir plus sur : erreur du compilateur C2586'
title: Erreur du compilateur C2586
ms.date: 11/04/2016
f1_keywords:
- C2586
helpviewer_keywords:
- C2586
ms.assetid: dae703c7-5c38-4db6-8411-4d1b22713eb5
ms.openlocfilehash: bcf0c374936c994773f0c2d2afa56924d6ca9f4b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177612"
---
# <a name="compiler-error-c2586"></a>Erreur du compilateur C2586

syntaxe de conversion définie par l’utilisateur incorrecte : indirections non conformes

L’indirection d’un opérateur de conversion n’est pas autorisée.

L’exemple suivant génère l’C2586 :

```cpp
// c2586.cpp
// compile with: /c
struct C {
   * operator int();   // C2586
   operator char();   // OK
};
```
