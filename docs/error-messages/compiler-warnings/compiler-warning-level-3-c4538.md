---
title: Avertissement du compilateur (niveau 3) C4538
ms.date: 11/04/2016
f1_keywords:
- C4538
helpviewer_keywords:
- C4538
ms.assetid: 747e3d51-b6d0-41c1-a726-7af3253b59d7
ms.openlocfilehash: c68bcbfe035f12f1a2a16bbcaffbaf4db080388f
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992031"
---
# <a name="compiler-warning-level-3-c4538"></a>Avertissement du compilateur (niveau 3) C4538

'type' : const/volatile qualifiers on this type are not supported

A qualifier keyword was applied to an array incorrectly. Pour plus d'informations, consultez [tableau](../../extensions/arrays-cpp-component-extensions.md).

The following sample generates C4538:

```cpp
// C4538.cpp
// compile with: /clr /W3 /LD
const array<int> ^f1();   // C4538
array<const int> ^f2();   // OK
```
