---
title: Compilateur avertissement (niveau 1) C4683 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4683
dev_langs:
- C++
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a157d3beb7c2efa7f1144a961973652e2ce384f7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194195"
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