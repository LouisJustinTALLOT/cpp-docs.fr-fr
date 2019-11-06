---
title: Avertissement du compilateur (niveau 1) C4096
ms.date: 11/04/2016
f1_keywords:
- C4096
helpviewer_keywords:
- C4096
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
ms.openlocfilehash: 8f526b26eda4c02825d225aa007c6029cc4b03dd
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627079"
---
# <a name="compiler-warning-level-1-c4096"></a>Avertissement du compilateur (niveau 1) C4096

'a' : l’interface n’est pas une interface COM ; ne sera pas émis dans IDL

Une définition d’interface que vous avez peut-être conçue comme interface COM n’a pas été définie comme interface COM et, par conséquent, n’est pas émise dans le fichier IDL.

Consultez [attributs d’interface](../../windows/attributes/interface-attributes.md) pour les attributs de liste indiquant qu’une interface est une interface com.

L’exemple suivant génère l’C4096 :

```cpp
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