---
title: Avertissement du compilateur (niveau 1) C4581
ms.date: 11/04/2016
f1_keywords:
- C4581
helpviewer_keywords:
- C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
ms.openlocfilehash: 491121bc236c54ce5b74c76abfa6a650ff7a99ff
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162164"
---
# <a name="compiler-warning-level-1-c4581"></a>Avertissement du compilateur (niveau 1) C4581

comportement déconseillé : ' "chaîne1" 'remplacé par’string2 'pour traiter l’attribut

Cette erreur peut être générée en raison du travail de conformité du compilateur pour Visual Studio 2005 : vérification des paramètres pour les attributs visuels C++ .

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
