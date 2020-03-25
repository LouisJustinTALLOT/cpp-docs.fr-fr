---
title: Avertissement du compilateur C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: c125fa84119c62e3090611c9a841f46eee759711
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165208"
---
# <a name="compiler-warning-c4439"></a>Avertissement du compilateur C4439

'fonction' : la définition de fonction avec un type managé dans la signature doit avoir une convention d’appel __clrcall

Le compilateur a remplacé implicitement une convention d’appel avec [__clrcall](../../cpp/clrcall.md). Pour résoudre cet avertissement, supprimez la Convention d’appel `__cdecl` ou `__stdcall`.

C4439 est toujours émis en tant qu’erreur. Vous pouvez désactiver cet avertissement avec le `#pragma warning` ou **/WD**; Pour plus d’informations, consultez [Warning](../../preprocessor/warning.md) ou [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/WO,/WV,/WX (niveau d’avertissement)](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4439.

```cpp
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```
