---
description: 'En savoir plus sur : erreur du compilateur C3136'
title: Erreur du compilateur C3136
ms.date: 10/03/2018
f1_keywords:
- C3136
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
ms.openlocfilehash: 4203eaa1f41603075bbb8162b7156783c8f2680a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239374"
---
# <a name="compiler-error-c3136"></a>Erreur du compilateur C3136

'interface' : une interface COM ne peut hériter que d’une autre interface COM, 'interface’n’est pas une interface COM

Une interface à laquelle vous avez appliqué un [attribut d’interface](../../windows/attributes/interface-attributes.md) hérite d’une interface qui n’est pas une interface com. Une interface COM hérite finalement de `IUnknown` . Toute interface précédée d’un attribut d’interface est une interface COM.

L’exemple suivant génère l’C3136 :

```cpp
// C3136.cpp
#include "unknwn.h"

__interface A   // C3136
// try the following line instead
// _interface A : IUnknown
{
   int a();
};

[object]
__interface B : A
{
   int aa();
};
```
