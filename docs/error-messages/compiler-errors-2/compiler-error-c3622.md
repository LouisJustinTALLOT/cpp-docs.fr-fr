---
title: Erreur du compilateur C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: 8775ff6fd78f1092ae931921a2b15ed2f8b166e9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214540"
---
# <a name="compiler-error-c3622"></a>Erreur du compilateur C3622

'classe' : une classe déclarée comme’keyword’ne peut pas être instanciée

Une tentative a été effectuée pour instancier une classe marquée comme [abstract](../../extensions/abstract-cpp-component-extensions.md). Une classe marquée comme **`abstract`** peut être une classe de base, mais elle ne peut pas être instanciée.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3622.

```cpp
// C3622.cpp
// compile with: /clr
ref class a abstract {};

int main() {
   a aa;   // C3622
}
```
