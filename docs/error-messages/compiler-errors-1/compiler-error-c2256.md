---
description: 'En savoir plus sur : erreur du compilateur C2256'
title: Erreur du compilateur C2256
ms.date: 11/04/2016
f1_keywords:
- C2256
helpviewer_keywords:
- C2256
ms.assetid: 171fa2bc-8c72-49cd-afe5-d723b7acd3c5
ms.openlocfilehash: a0dfc7601a09a47c24128ca5f999780d9fdf3e48
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134756"
---
# <a name="compiler-error-c2256"></a>Erreur du compilateur C2256

utilisation non conforme du spécificateur Friend sur’Function'

Un destructeur ou un constructeur ne peut pas être spécifié en tant que [Friend](../../cpp/friend-cpp.md).

L’exemple suivant génère l’C2256 :

```cpp
// C2256.cpp
// compile with: /c
class C {
public:
   friend ~C();   // C2256
   ~C();   // OK
};
```
