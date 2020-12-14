---
description: 'En savoir plus sur : erreur du compilateur C3738'
title: Erreur du compilateur C3738
ms.date: 11/04/2016
f1_keywords:
- C3738
helpviewer_keywords:
- C3738
ms.assetid: dd3ee011-e204-4264-bf3a-da32c4ef7038
ms.openlocfilehash: 7ec94d2be4faa0324563b723eb8a674c2d2d274f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244925"
---
# <a name="compiler-error-c3738"></a>Erreur du compilateur C3738

'calling_convention' : la Convention d’appel de l’instanciation explicite doit correspondre à celle du modèle instancié

Il est recommandé de ne pas spécifier de convention d’appel sur une instanciation explicite. Si vous devez, toutefois, les conventions d’appel doivent correspondre.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3738.

```cpp
// C3738.cpp
// compile with: /clr
// processor: x86
#include <stdio.h>
template< class T >
void f ( T arg ) {   // by default calling convention is __cdecl
   printf ( "f: %s\n", __FUNCSIG__ );
}

template
void __stdcall f< int > ( int arg );   // C3738
// try the following line instead
// void f< int > ( int arg );

int main () {
   f(1);
   f< int > ( 1 );
}
```
