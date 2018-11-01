---
title: Avertissement du compilateur (niveau 1) C4326
ms.date: 08/27/2018
f1_keywords:
- C4326
helpviewer_keywords:
- C4326
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
ms.openlocfilehash: d14a1902db4dcf2224ce6a58db120a81ebb5620f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601160"
---
# <a name="compiler-warning-level-1-c4326"></a>Avertissement du compilateur (niveau 1) C4326

> type de retour de '*fonction*'doit être'*type1*« au lieu de »*type2*'

## <a name="remarks"></a>Notes

Une fonction a retourné un type autre que *type1*. Par exemple, à l’aide de [/Za](../../build/reference/za-ze-disable-language-extensions.md), **principal** n’a pas retourné un **int**.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4326 et montre comment la corriger :

```cpp
// C4326.cpp
// compile with: /Za /W1
char main()
{
    // C4326, instead use int main()
}
```