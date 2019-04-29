---
title: Avertissement du compilateur C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: d604c234b9445a7e5304118124620f0057f30975
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311343"
---
# <a name="compiler-warning-c4439"></a>Avertissement du compilateur C4439

'fonction' : définition de fonction avec un type managé dans la signature doit avoir une convention d’appel __clrcall

Le compilateur a remplacé implicitement une convention d’appel avec [__clrcall](../../cpp/clrcall.md). Pour résoudre cet avertissement, supprimez le `__cdecl` ou `__stdcall` convention d’appel.

C4439 est toujours émis en tant qu’erreur. Vous pouvez désactiver cet avertissement avec le `#pragma warning` ou **WD**; consultez [avertissement](../../preprocessor/warning.md) ou [wln, / W0, W1, W2, / w3, / W4, W1, W2, / w3, / W4, Wall, WD, / we, Wo, / WV, /WX (niveau d’avertissement)](../../build/reference/compiler-option-warning-level.md)pour plus d’informations.

## <a name="example"></a>Exemple

L’exemple suivant génère C4439.

```
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```