---
title: Avertissement du compilateur (niveau 1) C4399
ms.date: 11/04/2016
f1_keywords:
- C4399
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
ms.openlocfilehash: a556fbffad41d04b3eb0ea1acfd5e8739ddd5b68
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186801"
---
# <a name="compiler-warning-level-1-c4399"></a>Avertissement du compilateur (niveau 1) C4399

> '*symbol*' : le symbole par processus ne doit pas être marqué avec __declspec (dllimport) lorsqu’il est compilé avec/clr : pure

## <a name="remarks"></a>Notes

L’option de compilateur **/clr : pure** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017.

Les données d’une image native ou d’une image avec des constructions natives et CLR ne peuvent pas être importées dans une image pure. Pour résoudre cet avertissement, compilez avec **/CLR** (et non **/clr : pure**) ou supprimez `__declspec(dllimport)`.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4399.

```cpp
// C4399.cpp
// compile with: /clr:pure /doc /W1 /c
__declspec(dllimport) __declspec(process) extern const int i;   // C4399
```
