---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4215'
title: Avertissement du compilateur (niveau 4) C4215
ms.date: 11/04/2016
f1_keywords:
- C4215
helpviewer_keywords:
- C4215
ms.assetid: f2aab64d-1bab-4f75-95ee-89e1263047b1
ms.openlocfilehash: 4d2e4d170b31c483f216fa85369c05ada38c30d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266557"
---
# <a name="compiler-warning-level-1-c4215"></a>Avertissement du compilateur (niveau 4) C4215

extension non standard utilisée : long float

Les extensions Microsoft par défaut (/Ze) traitent le **type float long** comme **`double`** . Compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)). Utilisez **`double`** pour maintenir la compatibilité.

L’exemple suivant génère l’C4215 :

```cpp
// C4215.cpp
// compile with: /W1 /LD
long float a;   // C4215

// use the line below to resolve the warning
// double a;
```
