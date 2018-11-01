---
title: Erreur du compilateur C2868
ms.date: 11/04/2016
f1_keywords:
- C2868
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
ms.openlocfilehash: 4cb259ed0f43831226fb7e1a1ccf7b28bcef7819
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614771"
---
# <a name="compiler-error-c2868"></a>Erreur du compilateur C2868

> «*identificateur*' : syntaxe de déclaration using non conforme ; nom qualifié attendu

Un [à l’aide de la déclaration](../../cpp/using-declaration.md) nécessite un *nom qualifié*, un opérateur de portée (`::`) séparés de séquence de noms d’espace de noms, classe ou d’énumération qui se termine par le nom d’identificateur. Un opérateur de résolution de portée unique peut être utilisé pour introduire un nom à partir de l’espace de noms global.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2868 et illustre également l’utilisation correcte :

```cpp
// C2868.cpp
class X {
public:
   int i;
};

class Y : X {
public:
   using X::i;   // OK
};

int main() {
   using X;   // C2868
}
```