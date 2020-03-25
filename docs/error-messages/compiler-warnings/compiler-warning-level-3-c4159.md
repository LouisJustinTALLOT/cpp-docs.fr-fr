---
title: Avertissement du compilateur (niveau 3) C4159
ms.date: 11/04/2016
f1_keywords:
- C4159
helpviewer_keywords:
- C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
ms.openlocfilehash: 20d6010cb83107946c00f2f7b00cda771b2e70b9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199015"
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
