---
title: Compilateur avertissement (niveau 1) C4342 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4342
dev_langs:
- C++
helpviewer_keywords:
- C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6aeb582ff891cc9d186604af5d2ca2c2844b1cb0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016258"
---
# <a name="compiler-warning-level-1-c4342"></a>Avertissement du compilateur (niveau 1) C4342

changement de comportement : '*fonction*' appelé, mais un opérateur de membre a été appelé dans les versions précédentes

Dans les versions de Visual C++ antérieures à Visual Studio 2002, un membre a été appelé, mais ce comportement a été modifié et le compilateur recherche désormais la meilleure correspondance dans la portée espace de noms.

Si un opérateur de membre a été trouvé, le compilateur aurait précédemment considère pas n’importe quel espace de noms des opérateurs de portée. S’il existe une meilleure correspondance dans la portée espace de noms, le compilateur actuel appelle correctement, alors que les compilateurs précédents personnes la considèrent comme.

Cet avertissement doit être désactivé une fois que vous avez porté votre code vers la version actuelle.  Le compilateur peut fournir des faux positifs, générer cet avertissement pour le code où il n’existe aucune modification du comportement.

Cet avertissement est désactivé par défaut. Pour plus d'informations, consultez [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

L’exemple suivant génère l’erreur C4342 :

```cpp
// C4342.cpp
// compile with: /EHsc /W1
#include <fstream>
#pragma warning(default: 4342)
using namespace std;
struct X : public ofstream {
   X();
};

X::X() {
   open( "ofs_bug_ev.txt." );
   if ( is_open() ) {
      *this << "Text" << "<-should be text" << endl;   // C4342
      *this << ' ' << "<-should be space symbol" << endl;   // C4342
   }
}

int main() {
   X b;
   b << "Text" << "<-should be text" << endl;
   b << ' ' << "<-should be space symbol" << endl;
}
```