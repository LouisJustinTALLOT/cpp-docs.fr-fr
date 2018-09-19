---
title: Erreur du compilateur C3136 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 0439aa157a683065ccf7fff5b5f9d6d4d85e2f12
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054218"
---
# <a name="compiler-error-c3136"></a>Erreur du compilateur C3136

'interface' : une interface COM ne peut hériter que d’une autre interface COM, 'interface' n’est pas une interface COM

Une interface à laquelle vous avez appliqué une [attribut interface](../../windows/interface-attributes.md) hérite d’une interface qui n’est pas une interface COM. Finalement, une interface COM hérite `IUnknown`. N’importe quelle interface précédé par un attribut de l’interface est une interface COM.

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