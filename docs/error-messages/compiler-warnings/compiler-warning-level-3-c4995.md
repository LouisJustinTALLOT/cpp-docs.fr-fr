---
title: Avertissement du compilateur (niveau 3) C4995
ms.date: 11/04/2016
f1_keywords:
- C4995
helpviewer_keywords:
- C4995
ms.assetid: c6b61755-4730-4947-ad4d-d1c2bc82585a
ms.openlocfilehash: 4c31023fbcb36c53a7d0f5138c280ff12c4d495e
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541177"
---
# <a name="compiler-warning-level-3-c4995"></a>Avertissement du compilateur (niveau 3) C4995

'fonction' : le nom a été marqué comme #pragma dépréciée

Le compilateur a rencontré une fonction qui était marquée avec le pragma [Deprecated](../../preprocessor/deprecated-c-cpp.md). La fonction ne sera peut-être plus prise en charge dans une future mise en production. Vous pouvez désactiver cet avertissement avec le pragma [Warning](../../preprocessor/warning.md) (exemple ci-dessous).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4995 :

```cpp
// C4995.cpp
// compile with: /W3
#include <stdio.h>

// #pragma warning(disable : 4995)
void func1(void)
{
    printf("\nIn func1");
}

int main()
{
    func1();
    #pragma deprecated(func1)
    func1();   // C4995
}
```