---
title: Erreur du compilateur C2868 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2868
dev_langs:
- C++
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2de22b34f9dc564ef89d7776af86718af70d51eb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037864"
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