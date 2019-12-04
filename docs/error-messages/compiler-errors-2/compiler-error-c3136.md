---
title: Erreur du compilateur C3136
ms.date: 10/03/2018
f1_keywords:
- C3136
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
ms.openlocfilehash: 75862f3b80d617b607a7b3e735cb3e16e9a40bb7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757382"
---
# <a name="compiler-error-c3136"></a>Erreur du compilateur C3136

'interface' : une interface COM ne peut hériter que d’une autre interface COM, 'interface’n’est pas une interface COM

Une interface à laquelle vous avez appliqué un [attribut d’interface](../../windows/attributes/interface-attributes.md) hérite d’une interface qui n’est pas une interface com. Une interface COM hérite finalement de `IUnknown`. Toute interface précédée d’un attribut d’interface est une interface COM.

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
