---
title: Avertissement du compilateur (niveau 1) C4683
ms.date: 08/27/2018
f1_keywords:
- C4683
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
ms.openlocfilehash: 264753ece6cbabded21df8e6b9dbb463f811e8a2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375156"
---
# <a name="compiler-warning-level-1-c4683"></a>Avertissement du compilateur (niveau 1) C4683

> «*fonction*' : source de l’événement a un 'out'-paramètre ; faites attention lorsque vous raccordez plusieurs gestionnaires d’événements

## <a name="remarks"></a>Notes

Si plus d’un récepteur d’événements est à l’écoute à une source d’événements COM, la valeur de paramètre de sortie peut être ignorée.

N’oubliez pas qu’une fuite de mémoire se produit dans les situations suivantes :

1. Si une méthode a un paramètre de sortie qui est affecté en interne, par exemple un BSTR *.

2. Si l’événement a plusieurs gestionnaires (est un événement multidiffusion).

La raison de la fuite de mémoire est que le paramètre de sortie est défini par plusieurs gestionnaires, mais retourné sur le site d’appel par le dernier gestionnaire uniquement.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4683 et montre comment la corriger :

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