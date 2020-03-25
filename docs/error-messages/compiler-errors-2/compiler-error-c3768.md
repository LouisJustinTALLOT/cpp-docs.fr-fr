---
title: Erreur du compilateur C3768
ms.date: 11/04/2016
f1_keywords:
- C3768
helpviewer_keywords:
- C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
ms.openlocfilehash: 534be9e3873276313335ca921264be92c9259b93
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165741"
---
# <a name="compiler-error-c3768"></a>Erreur du compilateur C3768

> Impossible de prendre l’adresse d’une fonction vararg virtuelle dans du code managé pur

## <a name="remarks"></a>Notes

L’option de compilateur **/clr : pure** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017.

Lors de la compilation avec **/clr : pure**, vous ne pouvez pas prendre l’adresse d’une fonction de `vararg` virtuelle.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3768 :

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
