---
description: 'En savoir plus sur : erreur du compilateur C2892'
title: Erreur du compilateur C2892
ms.date: 11/04/2016
f1_keywords:
- C2892
helpviewer_keywords:
- C2892
ms.assetid: c22a5084-2f50-42c2-a56b-6dfe5442edc9
ms.openlocfilehash: bcc1a43298973e270c39656b965b76cd75f3472e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278348"
---
# <a name="compiler-error-c2892"></a>Erreur du compilateur C2892

la classe locale ne doit pas avoir de modèles membres

Les fonctions membres basées sur un modèle ne sont pas valides dans une classe définie dans une fonction.

L’exemple suivant génère l’C2892 :

```cpp
// C2892.cpp
int main() {
   struct local {
      template<class T>   // C2892
      void f() {}
   };
}
```
