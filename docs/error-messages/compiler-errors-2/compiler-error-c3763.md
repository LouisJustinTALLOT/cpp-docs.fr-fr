---
description: 'En savoir plus sur : erreur du compilateur C3763'
title: Erreur du compilateur C3763
ms.date: 11/04/2016
f1_keywords:
- C3763
helpviewer_keywords:
- C3763
ms.assetid: 58b1f079-cd1d-46e0-9431-ea18210106b7
ms.openlocfilehash: 9423c2f0db133c58fc7680b475a450c7190423f4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285433"
---
# <a name="compiler-error-c3763"></a>Erreur du compilateur C3763

'type' : 'retval’et’out’ne peuvent figurer que sur un type pointeur de données

Les attributs [out](../../windows/attributes/out-cpp.md) ou [retVal](../../windows/attributes/retval.md) peuvent uniquement apparaître sur les paramètres de type pointer. Supprimez l’attribut ou définissez le paramètre de type pointeur.

L’exemple suivant génère l’C3763 :

```cpp
// C3763.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlplus.h>
#include <atlcom.h>

[ module(name=test) ];

[ dispinterface, uuid("00000000-0000-0000-0000-000000000001") ]
__interface IF84 : IDispatch
{
   [id(0x00000002)]HRESULT m2([out]unsigned char);
};

[ coclass, uuid("00000000-0000-0000-0000-000000000002") ]
class CF84 : public IF84
{   // C3763
public:
   HRESULT __stdcall m2(unsigned char i)
   {
      return S_OK;
   }
};

int main()
{
}
```
