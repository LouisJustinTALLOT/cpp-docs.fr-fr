---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4167'
title: Avertissement du compilateur (niveau 1) C4167
ms.date: 11/04/2016
f1_keywords:
- C4167
helpviewer_keywords:
- C4167
ms.assetid: 74a420bd-9371-4167-b1ee-74dd8680f97b
ms.openlocfilehash: 8d0b08ea4d97c6e85f5e07ce4844abdae7afafbd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266986"
---
# <a name="compiler-warning-level-1-c4167"></a>Avertissement du compilateur (niveau 1) C4167

function : uniquement disponible comme fonction intrinsèque

La **fonction #pragma** tente de forcer le compilateur à utiliser un appel conventionnel à une fonction qui doit être utilisée au format intrinsèque. Le pragma est ignoré.

Pour éviter cet avertissement, supprimez la **fonction #pragma**.

## <a name="example"></a>Exemple

```cpp
// C4167.cpp
// compile with: /W1
#include <malloc.h>
#pragma function(_alloca )   // C4167: _alloca() is intrinsic only
int main(){}
```
