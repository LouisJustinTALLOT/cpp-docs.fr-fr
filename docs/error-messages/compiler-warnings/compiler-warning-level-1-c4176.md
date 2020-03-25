---
title: Avertissement du compilateur (niveau 1) C4176
ms.date: 11/04/2016
f1_keywords:
- C4176
helpviewer_keywords:
- C4176
ms.assetid: cfffb934-219a-4a63-9df6-ba54405bf766
ms.openlocfilehash: e7efe17b9840179bd21a432c2654fadd7e9230c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199990"
---
# <a name="compiler-warning-level-1-c4176"></a>Avertissement du compilateur (niveau 1) C4176

'sous-composant' : sous-composant inconnu pour #pragma component (browser)

Le pragma **component** contient un sous-composant non valide. Pour exclure les références à un nom en particulier, vous devez utiliser l’option **references** avant ce nom.

## <a name="example"></a>Exemple

```cpp
// C4176.cpp
// compile with: /W1 /LD
#pragma component(browser, off, i)  // C4176
#pragma component(browser, off, references, i) // ok
```
