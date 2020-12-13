---
description: 'En savoir plus sur : erreur du compilateur C3373'
title: Erreur du compilateur C3373
ms.date: 11/04/2016
f1_keywords:
- C3373
helpviewer_keywords:
- C3373
ms.assetid: 6e7586c3-1a15-4773-ad20-f90090a400dc
ms.openlocfilehash: ab066f10adac654578d1705af1aa01bd93b41b31
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150733"
---
# <a name="compiler-error-c3373"></a>Erreur du compilateur C3373

l’attribut 'attribute' n’accepte aucun argument sauf sur une coclasse

Certains attributs peuvent être appliqués à plusieurs constructions C++, mais les arguments de l’attribut peuvent uniquement être autorisés sur certaines constructions.

L’exemple suivant génère l’erreur C3373 :

```cpp
// C3373.cpp
#include <windows.h>

[module(name="MyModule")];

[ object, uuid(373a1a4c-469b-11d3-a6b0-00c04f79ae8f) ]
__interface IMyIface
{
   // arguments to source and restricted are not allowed when
   // these attributes are applied to an interface
   [source(IMyIface)] HRESULT f1();
   [restricted(IMyIface)] HRESULT f2(); // C3373
};

[ coclass, uuid(373a1a4d-469b-11d3-a6b0-00c04f79ae8f) ]
class CMyClass : public IMyIface {
};

int main() {
}
```
