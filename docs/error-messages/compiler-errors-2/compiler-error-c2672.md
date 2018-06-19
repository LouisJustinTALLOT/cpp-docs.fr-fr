---
title: C2672 d’erreur du compilateur | Documents Microsoft
ms.date: 10/24/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2672
dev_langs:
- C++
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98c569c8b9b1466f184b44d345e76341d1476935
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236116"
---
# <a name="compiler-error-c2672"></a>C2672 d’erreur du compilateur

> '*fonction*' : aucune correspondance de trouver la fonction ne surchargée

Le compilateur n’a pas pu trouver une fonction surchargée qui correspond à la fonction spécifiée. Aucune fonction n’a été trouvée que prend correspondant aux paramètres, ou aucune fonction correspondante a l’accessibilité requise dans le contexte.

Lorsqu’il est utilisé par certains conteneurs de bibliothèque standard ou les algorithmes, vos types doivent fournir des membres accessibles ou des fonctions friend qui satisfont aux exigences du conteneur ou de l’algorithme. Par exemple, vos types d’itérateur doivent dériver de `std::iterator<>`. Opérations de comparaison ou l’utilisation d’autres opérateurs sur les types d’élément de conteneur peut nécessiter le type d’être considéré comme une partie gauche et un opérande de droite. Utiliser le type comme un opérande de droite peut nécessiter l’implémentation de l’opérateur comme une fonction non membre du type.

## <a name="example"></a>Exemple

Versions du compilateur avant Visual Studio 2017 n’a pas effectué sur les noms qualifiés dans certains contextes de modèle de contrôle d’accès. Cela peut interférer avec le comportement attendu de la fonctionnalité SFINAE où la substitution est supposée échouer en raison de l’inaccessibilité d’un nom. Cette situation peut entraîner un incident ou un comportement inattendu au moment de l’exécution en raison de l’appel par le compilateur de la surcharge incorrecte de l’opérateur. Dans Visual Studio 2017, une erreur de compilateur est générée.

Cet exemple se compile dans Visual Studio 2015, mais génère une erreur dans Visual Studio 2017. Pour résoudre ce problème, vérifiez le membre de paramètre de modèle accessible où elle est évaluée.

```cpp
#include <type_traits>

template <class T> class S {
// public:    // Uncomment this line to fix
    typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x)
{
    return (x == 0);
}

int main()
{
    f(10); // C2672: No matching overloaded function found.
}
```