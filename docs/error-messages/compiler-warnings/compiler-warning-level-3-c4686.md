---
title: Avertissement du compilateur (niveau 3) C4686
description: Avertissement du compilateur Microsoft C++ C4686.
ms.date: 08/29/2020
f1_keywords:
- C4686
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
ms.openlocfilehash: 6886ae7f413de630457b53e85b5cd75c4542ee19
ms.sourcegitcommit: 3628707bc17c99aac7aac27eb126cc2eaa4d07b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2020
ms.locfileid: "89194495"
---
# <a name="compiler-warning-level-3-c4686"></a>Avertissement du compilateur (niveau 3) C4686

> '*type défini par l’utilisateur*' : changement de comportement possible, modification de la Convention d’appel de retour UDT

## <a name="remarks"></a>Remarques

Une spécialisation de modèle de classe n’a pas été définie avant d’être utilisée dans un type de retour. Tout ce qui instancie la classe résout C4686 ; la déclaration d’une instance ou l’accès à un membre (par exemple, `C<int>::some_member` ) sont également des options.

Cet avertissement est désactivé par défaut. Pour plus d’informations, consultez [avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

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
