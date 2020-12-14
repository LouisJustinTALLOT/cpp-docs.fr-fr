---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4538'
title: Avertissement du compilateur (niveau 3) C4538
ms.date: 11/04/2016
f1_keywords:
- C4538
helpviewer_keywords:
- C4538
ms.assetid: 747e3d51-b6d0-41c1-a726-7af3253b59d7
ms.openlocfilehash: 4f5d6ee8b6144db4fad519f1484d00fe325591a2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257847"
---
# <a name="compiler-warning-level-3-c4538"></a>Avertissement du compilateur (niveau 3) C4538

'type' : les qualificateurs const/volatile sur ce type ne sont pas pris en charge

Un mot clé de qualificateur a été appliqué de façon incorrecte à un tableau. Pour plus d'informations, consultez [tableau](../../extensions/arrays-cpp-component-extensions.md).

L’exemple suivant génère l’C4538 :

```cpp
// C4538.cpp
// compile with: /clr /W3 /LD
const array<int> ^f1();   // C4538
array<const int> ^f2();   // OK
```
