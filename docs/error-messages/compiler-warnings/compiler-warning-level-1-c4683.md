---
title: Avertissement du compilateur (niveau 1) C4683
ms.date: 08/27/2018
f1_keywords:
- C4683
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
ms.openlocfilehash: f86cf8f6d894d6efaa1b49977634956dc1979a98
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175427"
---
# <a name="compiler-warning-level-1-c4683"></a>Avertissement du compilateur (niveau 1) C4683

> '*fonction*' : la source de l’événement a un paramètre’out'; Soyez prudent lorsque vous raccordez plusieurs gestionnaires d’événements

## <a name="remarks"></a>Notes

Si plusieurs récepteurs d’événements écoutent une source d’événements COM, la valeur d’un paramètre de sortie peut être ignorée.

N’oubliez pas qu’une fuite de mémoire se produit dans les situations suivantes :

1. Si une méthode a un paramètre out qui est alloué en interne, par exemple un BSTR *.

2. Si l’événement a plus d’un gestionnaire (est un événement de multidiffusion).

La fuite est due au fait que le paramètre de sortie sera défini par plusieurs gestionnaires, mais retourné au site d’appel uniquement par le dernier gestionnaire.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4683 et montre comment la corriger :

```cpp
// C4683.cpp
// compile with: /W1 /LD
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[ module(name="xx") ];

[ object ]
__interface I {
   HRESULT f([out] int* pi);
   // try the following line instead
   // HRESULT f(int* pi);
};

[ coclass, event_source(com) ]
struct E {
   __event __interface I;   // C4683
};
```
