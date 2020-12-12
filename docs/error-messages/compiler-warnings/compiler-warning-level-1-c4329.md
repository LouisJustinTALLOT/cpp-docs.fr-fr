---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4329'
title: Avertissement du compilateur (niveau 1) C4329
ms.date: 11/04/2016
f1_keywords:
- C4329
helpviewer_keywords:
- C4329
ms.assetid: 4316f51a-2c56-4b3f-831e-65d24b83b65c
ms.openlocfilehash: 210395694c581f7d37e1612bbdcb60e29f5e0bba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311563"
---
# <a name="compiler-warning-level-1-c4329"></a>Avertissement du compilateur (niveau 1) C4329

__declspec (align ()) est ignoré sur enum

L’utilisation du mot clé [align](../../cpp/align-cpp.md) du modificateur [__declspec](../../cpp/declspec.md) n’est pas autorisée sur un **`enum`** . L’exemple suivant génère l’C4329 :

```cpp
// C4329.cpp
// compile with: /W1 /LD
enum __declspec(align(256)) TestEnum {   // C4329
   TESTVAL1,
   TESTVAL2,
   TESTVAL3
};
__declspec(align(256)) enum TestEnum1;
```
