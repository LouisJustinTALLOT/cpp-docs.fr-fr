---
title: Avertissement du compilateur C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: 7cab2e55fca640438051fbb79ac933e83d5f3cbb
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623652"
---
# <a name="compiler-warning-c4439"></a>Avertissement du compilateur C4439

'fonction' : la définition de fonction avec un type managé dans la signature doit avoir une convention d’appel _ _ clrcall

Le compilateur a remplacé implicitement une convention d’appel avec [_ _ clrcall](../../cpp/clrcall.md). Pour résoudre cet avertissement, supprimez la Convention d’appel `__cdecl` ou `__stdcall`.

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