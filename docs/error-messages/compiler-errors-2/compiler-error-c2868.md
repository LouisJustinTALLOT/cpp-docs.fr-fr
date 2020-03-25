---
title: Erreur du compilateur C2868
ms.date: 11/04/2016
f1_keywords:
- C2868
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
ms.openlocfilehash: 0cbcf7dc80aedc554594f88992059f98b7091c21
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201632"
---
# <a name="compiler-error-c2868"></a>Erreur du compilateur C2868

> '*identificateur*' : syntaxe non conforme pour la déclaration using ; nom qualifié ATTENDU

Une [déclaration using](../../cpp/using-declaration.md) requiert un *nom qualifié*, un opérateur d’étendue (`::`) une séquence séparée d’espaces de noms, de classes ou d’énumérations qui se termine par le nom de l’identificateur. Un opérateur de résolution de portée unique peut être utilisé pour introduire un nom à partir de l’espace de noms global.

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
