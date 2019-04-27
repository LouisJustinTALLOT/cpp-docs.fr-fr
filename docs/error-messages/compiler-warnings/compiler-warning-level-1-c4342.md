---
title: Avertissement du compilateur (niveau 1) C4342
ms.date: 11/04/2016
f1_keywords:
- C4342
helpviewer_keywords:
- C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
ms.openlocfilehash: 439c4976f25688fd9220c3f58ceb933266b5f15c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187507"
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