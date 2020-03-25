---
title: Erreur du compilateur C3641
ms.date: 11/04/2016
f1_keywords:
- C3641
helpviewer_keywords:
- C3641
ms.assetid: e8d3613e-5e8d-46fe-a516-eb7d1de7cd21
ms.openlocfilehash: 44356fb1a1818a02102d23e6b308457f2f39506b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200510"
---
# <a name="compiler-error-c3641"></a>Erreur du compilateur C3641

> '*fonction*' : Convention d’appel’calling_convention’non valide pour la fonction compilée avec/clr : pure ou/CLR : safe

## <a name="remarks"></a>Notes

Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

Seule [__clrcall](../../cpp/clrcall.md) Convention d’appel est autorisée avec [/clr : pure](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3641 :

```cpp
// C3641.cpp
// compile with: /clr:pure /c
void __cdecl f() {}   // C3641
```
