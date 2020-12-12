---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4399'
title: Avertissement du compilateur (niveau 1) C4399
ms.date: 11/04/2016
f1_keywords:
- C4399
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
ms.openlocfilehash: a1d0fab62d13c08fb2117279d9173786c65d846f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311134"
---
# <a name="compiler-warning-level-1-c4399"></a>Avertissement du compilateur (niveau 1) C4399

> '*symbol*' : le symbole par processus ne doit pas être marqué avec __declspec (dllimport) lorsqu’il est compilé avec/clr : pure

## <a name="remarks"></a>Notes

L’option de compilateur **/clr : pure** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017.

Les données d’une image native ou d’une image avec des constructions natives et CLR ne peuvent pas être importées dans une image pure. Pour résoudre cet avertissement, compilez avec **/CLR** (not **/clr : pure**) ou Delete `__declspec(dllimport)` .

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4399.

```cpp
// C4399.cpp
// compile with: /clr:pure /doc /W1 /c
__declspec(dllimport) __declspec(process) extern const int i;   // C4399
```
