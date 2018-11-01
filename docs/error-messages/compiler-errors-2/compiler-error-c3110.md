---
title: Erreur du compilateur C3110
ms.date: 11/04/2016
f1_keywords:
- C3110
helpviewer_keywords:
- C3110
ms.assetid: 821dc71f-896e-4b2d-af0e-aa9932934b7b
ms.openlocfilehash: d067fb958f3bb00ef3e62097225881af9ec91dd6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570467"
---
# <a name="compiler-error-c3110"></a>Erreur du compilateur C3110

'nom_fonction' : vous ne pouvez pas surcharger une méthode d’interface COM

Une interface qui est précédée d’un attribut d’interface, tel que :

- [custom](../../windows/custom-cpp.md)

- [dispinterface](../../windows/dispinterface.md)

- [dual](../../windows/dual.md)

- [object](../../windows/object-cpp.md)

ne peut pas être surchargé. Exemple :

```
// C3110.cpp
#include <unknwn.h>
[ object, uuid= "4F98A180-EF37-11D1-978D-0000F805D73B" ]
__interface ITestInterface
{
   HRESULT mf1(void);
   HRESULT mf1(BSTR); // C3110
};

int main()
{
}
```