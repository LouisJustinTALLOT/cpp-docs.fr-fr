---
description: 'En savoir plus sur : erreur du compilateur C3131'
title: Erreur du compilateur C3131
ms.date: 11/04/2016
f1_keywords:
- C3131
helpviewer_keywords:
- C3131
ms.assetid: 38f20fac-83c9-4cd9-b7b5-74ca8f650ea6
ms.openlocfilehash: 3fde5045f2c14efdac96f902e12dcea1f5118505
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177404"
---
# <a name="compiler-error-c3131"></a>Erreur du compilateur C3131

le projet doit avoir un attribut’module’avec une propriété’name'

L’attribut [module](../../windows/attributes/module-cpp.md) doit avoir un paramètre Name.

L’exemple suivant génère l’C3131 :

```cpp
// C3131.cpp
[emitidl];
[module];   // C3131
// try the following line instead
// [module (name="MyLib")];

[public]
typedef long int LongInt;
```
