---
title: Erreur du compilateur C3136 | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3136
dev_langs:
- C++
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 082a89b69092a8320f6bb4b930d01a7fd2de10c8
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788381"
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