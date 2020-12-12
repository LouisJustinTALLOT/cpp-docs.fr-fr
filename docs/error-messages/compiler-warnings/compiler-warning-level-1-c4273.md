---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4273'
title: Avertissement du compilateur (niveau 1) C4273
ms.date: 11/04/2016
f1_keywords:
- C4273
helpviewer_keywords:
- C4273
ms.assetid: cc18611d-9454-40a4-ad73-69823d5888fb
ms.openlocfilehash: a7b36d8154f5f97a9497b79a91b2684fbad0d677
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266024"
---
# <a name="compiler-warning-level-1-c4273"></a>Avertissement du compilateur (niveau 1) C4273

'fonction' : liaison DLL incohérente

Deux définitions dans un fichier diffèrent au niveau de leur utilisation de [DllImport](../../cpp/dllexport-dllimport.md).

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C4273.

```cpp
// C4273.cpp
// compile with: /W1 /c
char __declspec(dllimport) c;
char c;   // C4273, delete this line or the line above to resolve
```

L’exemple suivant génère l’C4273.

```cpp
// C4273_b.cpp
// compile with: /W1 /clr /c
#include <stdio.h>
extern "C" int printf_s(const char *, ...);   // C4273
```
