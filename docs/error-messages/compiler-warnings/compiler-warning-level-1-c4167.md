---
title: Avertissement du compilateur (niveau 1) C4167
ms.date: 11/04/2016
f1_keywords:
- C4167
helpviewer_keywords:
- C4167
ms.assetid: 74a420bd-9371-4167-b1ee-74dd8680f97b
ms.openlocfilehash: aa81dc0cba264dd6ff37d3bdd521fce477b8b70d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624838"
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