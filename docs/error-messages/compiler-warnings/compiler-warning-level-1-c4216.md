---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4216'
title: Avertissement du compilateur (niveau 4) C4216
ms.date: 11/04/2016
f1_keywords:
- C4216
helpviewer_keywords:
- C4216
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
ms.openlocfilehash: b570863653ea64d159cbb2f4a11138b2361ce149
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266479"
---
# <a name="compiler-warning-level-1-c4216"></a>Avertissement du compilateur (niveau 4) C4216

extension non standard utilisée : float long

Les extensions Microsoft par défaut (/Ze) traitent la valeur **float long** comme **`double`** . Compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)). Utilisez **`double`** pour maintenir la compatibilité. L’exemple suivant génère l’C4216 :

```cpp
// C4216.cpp
// compile with: /W1
float long a;   // C4216

// use the line below to resolve the warning
// double a;

int main() {
}
```
