---
title: Avertissement du compilateur (niveau 3) C4686
ms.date: 08/27/2018
f1_keywords:
- C4686
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
ms.openlocfilehash: 5e23e6aa69fe8a59e3dfd22af7e33780c223cdd3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584516"
---
# <a name="compiler-warning-level-3-c4686"></a>Avertissement du compilateur (niveau 3) C4686

> «*type défini par l’utilisateur*' : changement de comportement possible, changement retour UDT convention d’appel

## <a name="remarks"></a>Notes

Une spécialisation de modèle de classe n’a pas été est définie avant d’être utilisé dans un type de retour. Tout ce qui instancie la classe résoudra C4686 ; déclaration d’une instance ou l’accès à un membre (C\<int > :: quoi que ce soit) sont également possibles.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

## <a name="example"></a>Exemple

Essayez ce qui suit à la place :

```cpp
// C4686.cpp
// compile with: /W3
#pragma warning (default : 4686)
template <class T>
class C;

template <class T>
C<T> f(T);

template <class T>
class C {};

int main() {
   f(1);   // C4686
}

template <class T>
C<T> f(T) {
   return C<int>();
}
```