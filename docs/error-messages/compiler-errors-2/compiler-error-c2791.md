---
description: 'En savoir plus sur : erreur du compilateur C2791'
title: Erreur du compilateur C2791
ms.date: 11/04/2016
f1_keywords:
- C2791
helpviewer_keywords:
- C2791
ms.assetid: 938ad1fb-75d9-4ce2-ad92-83d6249005b5
ms.openlocfilehash: 0f5bd93c1c6ee32399da793147a18e9225b5fcb1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297770"
---
# <a name="compiler-error-c2791"></a>Erreur du compilateur C2791

utilisation non conforme de’Super' : 'classe’n’a aucune classe de base

Le mot clé [Super](../../cpp/super.md) a été utilisé dans le contexte d’une fonction membre d’une classe qui n’a pas de classes de base.

L’exemple suivant génère l’C2791 :

```cpp
// C2791.cpp
struct D {
   void mf() {
      __super::mf();   // C2791
   }
};
```
