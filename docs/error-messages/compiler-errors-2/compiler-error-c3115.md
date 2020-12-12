---
description: 'En savoir plus sur : erreur du compilateur C3115'
title: Erreur du compilateur C3115
ms.date: 11/04/2016
f1_keywords:
- C3115
helpviewer_keywords:
- C3115
ms.assetid: 51726145-9782-4ec9-84b9-286f366d9cbd
ms.openlocfilehash: 4ac27ba71307d73526d82f72092150e0ca5559ab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115961"
---
# <a name="compiler-error-c3115"></a>Erreur du compilateur C3115

'Attribute' : cet attribut n’est pas autorisé sur’Construct'

Un attribut a été appliqué à une construction pour laquelle il n’était pas prévu.  Pour plus d’informations [, consultez attributs par utilisation](../../windows/attributes/attributes-by-usage.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3115.

```cpp
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
