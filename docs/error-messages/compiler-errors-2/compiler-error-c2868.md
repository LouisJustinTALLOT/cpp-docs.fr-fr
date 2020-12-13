---
description: 'En savoir plus sur : erreur du compilateur C2868'
title: Erreur du compilateur C2868
ms.date: 11/04/2016
f1_keywords:
- C2868
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
ms.openlocfilehash: c6a6368fbdfe61014a606fadce92322234e438f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333787"
---
# <a name="compiler-error-c2868"></a>Erreur du compilateur C2868

> '*identificateur*' : syntaxe non conforme pour la déclaration using ; nom qualifié ATTENDU

Une [déclaration using](../../cpp/using-declaration.md) requiert un *nom qualifié*, une `::` séquence de noms d’espaces de noms, de classes ou d’énumérations séparés par un opérateur Scope () qui se termine par le nom de l’identificateur. Un opérateur de résolution de portée unique peut être utilisé pour introduire un nom à partir de l’espace de noms global.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2868 et affiche également l’utilisation correcte :

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
