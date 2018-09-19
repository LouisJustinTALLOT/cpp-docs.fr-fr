---
title: Erreur du compilateur C3115 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3115
dev_langs:
- C++
helpviewer_keywords:
- C3115
ms.assetid: 51726145-9782-4ec9-84b9-286f366d9cbd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da47a6987a1b540dc42b154c1a181c67e1524043
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090683"
---
# <a name="compiler-error-c3115"></a>Erreur du compilateur C3115

'attribute' : cet attribut n’est pas autorisé sur 'construction'

Un attribut a été appliqué à une construction pour laquelle il n’a pas été conçu.  Consultez [attributs par utilisation](../../windows/attributes-by-usage.md) pour plus d’informations.

## <a name="example"></a>Exemple

L’exemple suivant génère C3115.

```
// C3115.cpp
// compile with: /c
#include <unknwn.h>
[module(name="xx")];

[object, helpstringdll(xx.dll), uuid("00000000-0000-0000-0000-000000000001")]   // C3115
// try the following line instead
// [object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI {
   HRESULT xx();
};
```