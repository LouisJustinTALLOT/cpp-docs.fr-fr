---
title: Avertissement du compilateur (niveau 4) C4680
ms.date: 11/04/2016
f1_keywords:
- C4680
helpviewer_keywords:
- C4680
ms.assetid: 6e043f4c-c601-4b77-8130-920cff1d912e
ms.openlocfilehash: 9130fa2665452b85c5ec83eef0b3d1d618c995a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466707"
---
# <a name="compiler-warning-level-4-c4680"></a>Avertissement du compilateur (niveau 4) C4680

'class' : coclasse ne spécifie pas une interface par défaut

Un [par défaut](../../windows/default-cpp.md) interface n’a pas été spécifiée pour une classe qui a été marquée avec la [coclasse](../../windows/coclass.md) attribut. Dans l’ordre pour un objet soit utile, elle doit implémenter une interface.

L’exemple suivant génère l’erreur C4680 :

```
// C4680.cpp
// compile with: /W4
#include <windows.h>
[module(name="MyModule")];

[ object, uuid(373a1a4c-469b-11d3-a6b0-00c04f79ae8f) ]
__interface IMyIface1
{
   HRESULT f1();
};

[ object, uuid(37331a4c-469b-11d3-a6b0-00c04f79ae8f) ]
__interface IMyIface2
{
   HRESULT f1();
};

// to resolve C4680, specify a source interface also
// for example, default(IMyIface1, IMyface2)
[ coclass, uuid(373a1a4d-469b-11d3-a6b0-00c04f79ae8f), default(IMyIface1), source(IMyIface1) ]
class CMyClass : public IMyIface1
{   // C4680
};

int main()
{
}
```