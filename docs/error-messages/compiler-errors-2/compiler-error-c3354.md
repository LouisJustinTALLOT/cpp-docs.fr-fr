---
description: 'En savoir plus sur : erreur du compilateur C3354'
title: Erreur du compilateur C3354
ms.date: 11/04/2016
f1_keywords:
- C3354
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
ms.openlocfilehash: cb2c110471b95010e56677608725e5d6abeaa5e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245315"
---
# <a name="compiler-error-c3354"></a>Erreur du compilateur C3354

'fonction' : la fonction utilisée pour créer un délégué ne peut pas avoir un type de retour 'type'

Les types suivants ne sont pas valides en tant que types de retour pour un **`delegate`** :

- Pointeur vers fonction

- Pointeur vers membre

- Pointeur vers fonction membre

- Référence vers fonction

- Référence vers fonction membre

L’exemple suivant génère l’erreur C3354 :

```cpp
// C3354_2.cpp
// compile with: /clr /c
using namespace System;
typedef void ( *VoidPfn )();

delegate VoidPfn func(); // C3354
// try the following line instead
// delegate  void func();
```
