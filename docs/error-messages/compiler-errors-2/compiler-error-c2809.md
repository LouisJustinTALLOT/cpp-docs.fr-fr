---
description: 'En savoir plus sur : erreur du compilateur C2809'
title: Erreur du compilateur C2809
ms.date: 11/04/2016
f1_keywords:
- C2809
helpviewer_keywords:
- C2809
ms.assetid: ce796b8e-1a8c-4074-995d-1ad09afd0e93
ms.openlocfilehash: 75333b2742e1860eede12727e465479b4869e00c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320598"
---
# <a name="compiler-error-c2809"></a>Erreur du compilateur C2809

'operator opérateur’n’a pas de paramètres formels

L’opérateur n’a pas les paramètres requis.

L’exemple suivant génère l’C2809 :

```cpp
// C2809.cpp
// compile with: /c
class A{};
int operator+ ();   // C2809
int operator+ (A);   // OK
```
