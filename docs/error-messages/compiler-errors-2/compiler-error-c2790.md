---
description: 'En savoir plus sur : erreur du compilateur C2790'
title: Erreur du compilateur C2790
ms.date: 11/04/2016
f1_keywords:
- C2790
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
ms.openlocfilehash: 0913b87f40e7f4ad2ecccb333e67bb0d76b4afde
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297797"
---
# <a name="compiler-error-c2790"></a>Erreur du compilateur C2790

'Super' : ce mot clé ne peut être utilisé que dans le corps d’une fonction membre de classe

Ce message d’erreur s’affiche si l’utilisateur tente d’utiliser le mot clé [Super](../../cpp/super.md) en dehors du contexte d’une fonction membre.

L’exemple suivant génère l’C2790 :

```cpp
// C2790.cpp
void f() {
   __super::g();   // C2790
}
```
