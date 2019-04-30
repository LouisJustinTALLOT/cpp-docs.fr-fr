---
title: Erreur du compilateur C3115
ms.date: 11/04/2016
f1_keywords:
- C3115
helpviewer_keywords:
- C3115
ms.assetid: 51726145-9782-4ec9-84b9-286f366d9cbd
ms.openlocfilehash: e334836986548d4f854dd9a5760bd8315b769d03
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404089"
---
# <a name="compiler-error-c3115"></a>Erreur du compilateur C3115

'attribute' : cet attribut n’est pas autorisé sur 'construction'

Un attribut a été appliqué à une construction pour laquelle il n’a pas été conçu.  Consultez [attributs par utilisation](../../windows/attributes/attributes-by-usage.md) pour plus d’informations.

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