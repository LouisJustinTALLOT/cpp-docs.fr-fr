---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4581'
title: Avertissement du compilateur (niveau 1) C4581
ms.date: 11/04/2016
f1_keywords:
- C4581
helpviewer_keywords:
- C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
ms.openlocfilehash: 6fffa3f7ea74cb17eae7fe4af2575e1d574084fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332222"
---
# <a name="compiler-warning-level-1-c4581"></a>Avertissement du compilateur (niveau 1) C4581

comportement déconseillé : ' "chaîne1" 'remplacé par’string2 'pour traiter l’attribut

Cette erreur peut être générée en raison du travail de conformité du compilateur pour Visual Studio 2005 : vérification des paramètres pour les attributs de Visual C++.

Dans les versions précédentes, les valeurs d’attribut étaient acceptées, qu’elles soient ou non placées entre guillemets. Si la valeur est une énumération, elle ne doit pas être placée entre guillemets.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4581.

```cpp
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
