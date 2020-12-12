---
description: 'En savoir plus sur : erreur du compilateur C3768'
title: Erreur du compilateur C3768
ms.date: 11/04/2016
f1_keywords:
- C3768
helpviewer_keywords:
- C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
ms.openlocfilehash: 3203fe74fb1da91f24312f76ca11ac49711da8f9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291712"
---
# <a name="compiler-error-c3768"></a>Erreur du compilateur C3768

> Impossible de prendre l’adresse d’une fonction vararg virtuelle dans du code managé pur

## <a name="remarks"></a>Notes

L’option de compilateur **/clr : pure** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017.

Lors de la compilation avec **/clr : pure**, vous ne pouvez pas prendre l’adresse d’une `vararg` fonction virtuelle.

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
