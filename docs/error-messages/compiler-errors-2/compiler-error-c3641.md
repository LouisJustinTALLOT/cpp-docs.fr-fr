---
title: Erreur du compilateur C3641
ms.date: 11/04/2016
f1_keywords:
- C3641
helpviewer_keywords:
- C3641
ms.assetid: e8d3613e-5e8d-46fe-a516-eb7d1de7cd21
ms.openlocfilehash: f6c27067e4f07c89b4226cf4d26adf2afb0b07ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648576"
---
# <a name="compiler-error-c3641"></a>Erreur du compilateur C3641

> «*fonction*' : non valide de convention d’appel 'convention_appel' pour la fonction compilée avec/clr : pure ou/CLR : safe

## <a name="remarks"></a>Notes

Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Uniquement [__clrcall](../../cpp/clrcall.md) convention d’appel est autorisée avec [/CLR : pure](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3641 :

```cpp
// C3641.cpp
// compile with: /clr:pure /c
void __cdecl f() {}   // C3641
```