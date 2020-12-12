---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4683'
title: Avertissement du compilateur (niveau 1) C4683
ms.date: 08/27/2018
f1_keywords:
- C4683
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
ms.openlocfilehash: e7f2c76e7f15bb7342e60b2aa390cf0bd1a8ce05
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285238"
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
