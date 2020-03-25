---
title: Avertissement du compilateur (niveau 3) C4686
ms.date: 08/27/2018
f1_keywords:
- C4686
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
ms.openlocfilehash: a8eae1ddeb875d267b82c67e989cb41e8c9b2afb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185449"
---
# <a name="compiler-warning-level-3-c4686"></a>Avertissement du compilateur (niveau 3) C4686

> '*type défini par l’utilisateur*' : changement de comportement possible, modification de la Convention d’appel de retour UDT

## <a name="remarks"></a>Notes

Une spécialisation de modèle de classe n’a pas été définie avant d’être utilisée dans un type de retour. Tout ce qui instancie la classe permet de résoudre C4686 ; la déclaration d’une instance ou l’accès à un membre (C\<int >:: n’importe quoi) sont également des options.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

## <a name="example"></a>Exemple

Essayez plutôt les opérations suivantes :

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
