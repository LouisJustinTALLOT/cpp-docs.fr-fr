---
title: Avertissement du compilateur (niveau 3) C4995
ms.date: 11/04/2016
f1_keywords:
- C4995
helpviewer_keywords:
- C4995
ms.assetid: c6b61755-4730-4947-ad4d-d1c2bc82585a
ms.openlocfilehash: c361563c2272da002a0edc185cc924c64f6b5e5c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991658"
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
