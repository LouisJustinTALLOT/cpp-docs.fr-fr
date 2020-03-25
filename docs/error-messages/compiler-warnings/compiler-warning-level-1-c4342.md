---
title: Avertissement du compilateur (niveau 1) C4342
ms.date: 11/04/2016
f1_keywords:
- C4342
helpviewer_keywords:
- C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
ms.openlocfilehash: 8ac00d3d57f8cf7d6c85f3106dbe9b8c3cb9adf0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162918"
---
# <a name="compiler-warning-level-1-c4342"></a>Avertissement du compilateur (niveau 1) C4342

changement de comportement : '*Function*'appelé, mais un opérateur de membre a été appelé dans les versions précédentes

Dans les versions de C++ Visual antérieures à visual studio 2002, un membre a été appelé, mais ce comportement a été modifié et le compilateur trouve maintenant la meilleure correspondance dans la portée de l’espace de noms.

Si un opérateur de membre a été trouvé, le compilateur ne tient pas compte des opérateurs de portée d’espace de noms. S’il existe une meilleure correspondance au niveau de la portée de l’espace de noms, le compilateur actuel l’appelle correctement, alors que les compilateurs précédents ne le considèrent pas.

Cet avertissement doit être désactivé une fois que vous avez correctement effectué le portage de votre code vers la version actuelle.  Le compilateur peut fournir des faux positifs, générant cet avertissement pour le code où il n’y a aucun changement de comportement.

Cet avertissement est désactivé par défaut. Pour plus d'informations, consultez [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

L’exemple suivant génère l’C4342 :

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
