---
title: Avertissement du compilateur (niveau 1) C4581
ms.date: 11/04/2016
f1_keywords:
- C4581
helpviewer_keywords:
- C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
ms.openlocfilehash: 9e370bcff0c30fb508ebc22aaff1f6a56dd420a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625119"
---
# <a name="compiler-warning-level-1-c4581"></a>Avertissement du compilateur (niveau 1) C4581

comportement déconseillé : '« string1 »' remplacé par 'chaîne2' pour traiter l’attribut

Cette erreur peut être due à la mise en conformité du compilateur pour Visual C++ 2005 : vérification des paramètres des attributs Visual C++.

Dans les versions précédentes, les valeurs d’attribut ont été acceptées s’ils ont été placés entre guillemets. Si la valeur est une énumération, elle ne doit pas figurer entre guillemets.

## <a name="example"></a>Exemple

L’exemple suivant génère C4581.

```
// C4581.cpp
// compile with: /c /W1
#include "unknwn.h"
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI : IUnknown {};

[coclass, uuid(12345678-1111-2222-3333-123456789012), threading("free")]   // C4581
// try the following line instead
// [coclass, uuid(12345678-1111-2222-3333-123456789012), threading(free)]
class CSample : public IMyI {};
```