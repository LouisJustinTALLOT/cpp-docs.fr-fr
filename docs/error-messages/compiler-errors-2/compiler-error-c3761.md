---
description: 'En savoir plus sur : erreur du compilateur C3761'
title: Erreur du compilateur C3761
ms.date: 11/04/2016
f1_keywords:
- C3761
helpviewer_keywords:
- C3761
ms.assetid: 0c16f093-7a78-4838-b90b-0c67ef6e9270
ms.openlocfilehash: c3fd33d7a27d8ae85582a5711b7bdd1e15c93393
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255455"
---
# <a name="compiler-error-c3761"></a>Erreur du compilateur C3761

'fonction' : 'retval’ne peut figurer que sur le dernier argument d’une fonction

L’attribut [retVal](../../windows/attributes/retval.md) a été utilisé sur un argument de fonction qui n’est pas le dernier argument de la liste.

L’exemple suivant génère l’C3761 :

```cpp
// C3761.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[ module(name=test) ];

[dispinterface]
__interface I
{
   [id(1)] HRESULT func([out, retval] int* i, [in] int j);
   // try the following line instead
   // [id(1)] HRESULT func([in] int i, [out, retval] int* j);
};

[coclass]
struct C : I {   // C3761
   HRESULT func(int* i, int j)
   // try the following line instead
   // HRESULT func(int j, int* i)
   {
      return S_OK;
   }
};

int main()
{
}
```
