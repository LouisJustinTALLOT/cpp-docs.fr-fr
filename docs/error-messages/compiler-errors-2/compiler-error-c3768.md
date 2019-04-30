---
title: Erreur du compilateur C3768
ms.date: 11/04/2016
f1_keywords:
- C3768
helpviewer_keywords:
- C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
ms.openlocfilehash: e9c385fd178dc967e72f5e0ca7fab27b28ad962f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400212"
---
# <a name="compiler-error-c3768"></a>Erreur du compilateur C3768

> ne peut pas prendre l’adresse d’une fonction vararg virtuelle dans le code managé pur

## <a name="remarks"></a>Notes

Le **/CLR : pure** option du compilateur est déconseillée dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Lors de la compilation avec **/CLR : pure**, vous ne pouvez pas prendre l’adresse d’une machine virtuelle `vararg` (fonction).

## <a name="example"></a>Exemple

L’exemple suivant génère C3768 :

```cpp
// C3768.cpp
// compile with: /clr:pure
struct A
{
   virtual void f(...);
};

int main()
{
   &(A::f);   // C3768
}
```