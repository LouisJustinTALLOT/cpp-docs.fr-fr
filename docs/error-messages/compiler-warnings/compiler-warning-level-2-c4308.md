---
title: Avertissement du compilateur (niveau 2) C4308
ms.date: 11/04/2016
f1_keywords:
- C4308
helpviewer_keywords:
- C4308
ms.assetid: d4e5c53c-71b2-4bbc-8a7c-3a2a3180d9d9
ms.openlocfilehash: 43bdfa1181ff45d80236ef1f07279eea67ebce0a
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052073"
---
# <a name="compiler-warning-level-2-c4308"></a>Avertissement du compilateur (niveau 2) C4308

constante intégrale négative convertie en type non signé

Une expression convertit une constante entière négative en type non signé. Le résultat de l’expression est probablement inutile.

## <a name="example"></a>Exemple

```cpp
// C4308.cpp
// compile with: /W2
unsigned int u = (-5 + 3U);   // C4308

int main()
{
}
```