---
description: 'En savoir plus sur : avertissement du compilateur C4439'
title: Avertissement du compilateur C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: 123f42ca495faeccc995dc1ac87572180d1dce70
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180745"
---
# <a name="compiler-warning-c4439"></a>Avertissement du compilateur C4439

'fonction' : la définition de fonction avec un type managé dans la signature doit avoir une convention d’appel __clrcall

Le compilateur a remplacé implicitement une convention d’appel par [`__clrcall`](../../cpp/clrcall.md) . Pour résoudre cet avertissement, supprimez **`__cdecl`** la **`__stdcall`** Convention d’appel ou.

C4439 est toujours émis en tant qu’erreur. Vous pouvez désactiver cet avertissement avec le `#pragma warning` ou **`/wd`** . pour plus d’informations, consultez [Warning](../../preprocessor/warning.md) [,/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/WO,/WV,/WX (niveau d’avertissement)](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4439.

```cpp
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```
