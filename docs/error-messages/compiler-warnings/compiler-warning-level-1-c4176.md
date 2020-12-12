---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4176'
title: Avertissement du compilateur (niveau 1) C4176
ms.date: 11/04/2016
f1_keywords:
- C4176
helpviewer_keywords:
- C4176
ms.assetid: cfffb934-219a-4a63-9df6-ba54405bf766
ms.openlocfilehash: 9ba6e0ec6dff72d875aecc74e51d6f9a7e1c05e3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266895"
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
