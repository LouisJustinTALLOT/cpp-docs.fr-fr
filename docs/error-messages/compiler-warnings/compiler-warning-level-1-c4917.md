---
title: Avertissement du compilateur (niveau 1) C4917
ms.date: 11/04/2016
f1_keywords:
- C4917
helpviewer_keywords:
- C4917
ms.assetid: c05e2610-4a5d-4f4b-a99b-c15fd7f1d5f1
ms.openlocfilehash: 97f6f0a08c8ef292d81471cb5d0d94e359466933
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466792"
---
# <a name="compiler-warning-level-1-c4917"></a>Avertissement du compilateur (niveau 1) C4917

'déclarateur' : un GUID ne peut être associé à une classe, d’interface ou espace de noms

Une structure définie par l’utilisateur autre que [classe](../../cpp/class-cpp.md), [interface](../../cpp/interface.md), ou [espace de noms](../../cpp/namespaces-cpp.md) ne peut pas avoir un GUID.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

## <a name="example"></a>Exemple

L’exemple de code suivant génère C4917 :

```cpp
// C4917.cpp
// compile with: /W1
#pragma warning(default : 4917)
__declspec(uuid("00000000-0000-0000-0000-000000000001")) struct S
{
} s;   // C4917, don't put uuid on a struct

int main()
{
}
```