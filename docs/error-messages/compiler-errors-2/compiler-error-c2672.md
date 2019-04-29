---
title: Erreur du compilateur C2672
ms.date: 10/24/2017
f1_keywords:
- C2672
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
ms.openlocfilehash: df0f656c9db23739ec62629088b9cc5f7950a92d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386861"
---
# <a name="compiler-error-c2672"></a>Erreur du compilateur C2672

> «*fonction*' : fonction aucun correspondante ne surchargée introuvable

Le compilateur n’a pas pu trouver une fonction surchargée qui correspond à la fonction spécifiée. Aucune fonction n’a été trouvée que prend correspondant aux paramètres, ou aucune fonction correspondante a l’accessibilité requise dans le contexte.

Lorsqu’il est utilisé par certains conteneurs de bibliothèque standard ou les algorithmes, vos types doivent fournir des membres accessibles ou des fonctions friend qui répondent aux exigences du conteneur ou de l’algorithme. Par exemple, vos types d’itérateur doivent dériver de `std::iterator<>`. Opérations de comparaison ou l’utilisation d’autres opérateurs sur les types d’élément de conteneur peut nécessiter le type d’être considéré comme un gauche et un opérande de droite. Utiliser le type comme un opérande de droite peut nécessiter l’implémentation de l’opérateur comme une fonction non membre du type.

## <a name="example"></a>Exemple

Les versions du compilateur avant Visual Studio 2017 n’a pas effectué sur les noms qualifiés dans certains contextes de modèle de contrôle d’accès. Cela peut interférer avec le comportement attendu de la fonctionnalité SFINAE où la substitution est supposée échouer en raison de l’inaccessibilité d’un nom. Cette situation peut entraîner un incident ou un comportement inattendu au moment de l’exécution en raison de l’appel par le compilateur de la surcharge incorrecte de l’opérateur. Dans Visual Studio 2017, une erreur de compilateur est générée.

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