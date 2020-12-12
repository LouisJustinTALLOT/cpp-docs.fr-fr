---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4159'
title: Avertissement du compilateur (niveau 3) C4159
ms.date: 11/04/2016
f1_keywords:
- C4159
helpviewer_keywords:
- C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
ms.openlocfilehash: 153bd7ee7bc634ab10e0e6eb872a8f055e6470e9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326461"
---
# <a name="compiler-warning-level-3-c4159"></a>Avertissement du compilateur (niveau 3) C4159

> #<a name="pragma-pragmapop--has-popped-previously-pushed-identifier-identifier"></a>pragma pragma (,... pop) : a le dépileur ayant précédemment fait l’objet d’un push de l’identificateur'*identifier*'

## <a name="remarks"></a>Notes

Votre code source contient une instruction **Push** avec un identificateur pour un pragma suivi d’une instruction **pop** sans identificateur. Par conséquent, l' *identificateur* est dépilé, et les utilisations ultérieures de l' *identificateur* peuvent entraîner un comportement inattendu.

## <a name="example"></a>Exemple

Pour éviter cet avertissement, indiquez un identificateur dans l’instruction **pop** . Par exemple :

```cpp
// C4159.cpp
// compile with: /W3
#pragma pack(push, f)
#pragma pack(pop)   // C4159

// using the identifier resolves the warning
// #pragma pack(pop, f)

int main()
{
}
```
