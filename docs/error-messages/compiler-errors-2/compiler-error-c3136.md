---
title: Erreur du compilateur C3136
ms.date: 10/03/2018
f1_keywords:
- C3136
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
ms.openlocfilehash: e32ffca067c3b25120301527e7a708d53001d541
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501088"
---
# <a name="compiler-error-c3136"></a>Erreur du compilateur C3136

'interface' : une interface COM ne peut hériter que d’une autre interface COM, 'interface' n’est pas une interface COM

Une interface à laquelle vous avez appliqué une [attribut interface](../../windows/attributes/interface-attributes.md) hérite d’une interface qui n’est pas une interface COM. Finalement, une interface COM hérite `IUnknown`. N’importe quelle interface précédé par un attribut de l’interface est une interface COM.

L’exemple suivant génère l’erreur C3136 :

```
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