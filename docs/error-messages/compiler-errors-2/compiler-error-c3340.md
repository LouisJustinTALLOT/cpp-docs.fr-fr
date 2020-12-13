---
description: 'En savoir plus sur : erreur du compilateur C3340'
title: Erreur du compilateur C3340
ms.date: 11/04/2016
f1_keywords:
- C3340
helpviewer_keywords:
- C3340
ms.assetid: 23b12298-b92a-4717-8380-f165c998cb8a
ms.openlocfilehash: 3c944d8d61a93fb3985e85e946f147eecd56624a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337313"
---
# <a name="compiler-error-c3340"></a>Erreur du compilateur C3340

'interface' : une interface ne peut être à la fois 'restricted' et 'default' dans la coclasse 'classe'

Les attributs [restricted](../../windows/attributes/restricted.md) et [default](../../windows/attributes/default-cpp.md) s’excluent mutuellement.

L’exemple suivant génère l’erreur C3340 :

```cpp
// C3340.cpp
#include <windows.h>
[module(name="MyModule")];

[ object, uuid(373a1a4c-469b-11d3-a6b0-00c04f79ae8f) ]
__interface IMyIface
{
   HRESULT f1();
};

[ coclass, uuid(373a1a4d-469b-11d3-a6b0-00c04f79ae8f),
default(IMyIface),
source(IMyIface),restricted(IMyIface) ]
class CmyClass // C3340
{
};

int main()
{
}
```
