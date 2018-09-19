---
title: Compilateur Warning (level 1) C4096 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4096
dev_langs:
- C++
helpviewer_keywords:
- C4096
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef2aaf3f37e9699547c3a85c55a2f72d4baab7a6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047692"
---
# <a name="compiler-warning-level-1-c4096"></a>Compilateur Warning (level 1) C4096

« a » : interface n’est pas une interface COM ; ne sera pas émise vers IDL

Une définition d’interface que vous aviez prévu comme une interface COM n’a pas été définie comme une interface COM et ne sera donc pas émise pour le fichier IDL.

Consultez [attributs d’Interface](../../windows/interface-attributes.md) pour une liste d’attributs qui indiquent une interface est une interface COM.

L’exemple suivant génère l’erreur C4096 :

```
// C4096.cpp
// compile with: /W1 /LD
#include "windows.h"
[module(name="xx")];

// [object, uuid("00000000-0000-0000-0000-000000000001")]
__interface a
{
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct b : a
{
};   // C4096, remove coclass or uncomment object
```