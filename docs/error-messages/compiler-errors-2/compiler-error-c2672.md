---
description: 'En savoir plus sur : erreur du compilateur C2672'
title: Erreur du compilateur C2672
ms.date: 10/24/2017
f1_keywords:
- C2672
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
ms.openlocfilehash: 2de901eaa416f3ee675c7b09c342de74dc7207fe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282079"
---
# <a name="compiler-error-c2672"></a>Erreur du compilateur C2672

> '*fonction*' : aucune fonction surchargée correspondante trouvée

Le compilateur n’a pas pu trouver une fonction surchargée qui correspond à la fonction spécifiée. Aucune fonction qui accepte des paramètres correspondants n’a été trouvée, ou aucune fonction correspondante n’a l’accessibilité requise en contexte.

Lorsqu’ils sont utilisés par certains conteneurs ou algorithmes de bibliothèque standard, vos types doivent fournir des membres accessibles ou des fonctions Friend qui répondent aux exigences du conteneur ou de l’algorithme. Par exemple, vos types itérateurs doivent dériver de `std::iterator<>` . Les opérations de comparaison ou l’utilisation d’autres opérateurs sur les types d’éléments de conteneur peuvent nécessiter que le type soit considéré à la fois comme un opérande de gauche et un opérande de droite. L’utilisation du type comme opérande de droite peut nécessiter l’implémentation de l’opérateur en tant que fonction non membre du type.

## <a name="example"></a>Exemple

Les versions du compilateur antérieures à Visual Studio 2017 n’ont pas effectué de contrôle d’accès sur les noms qualifiés dans certains contextes de modèle. Cela peut interférer avec le comportement attendu de la fonctionnalité SFINAE où la substitution est supposée échouer en raison de l’inaccessibilité d’un nom. Cette situation peut entraîner un incident ou un comportement inattendu au moment de l’exécution en raison de l’appel par le compilateur de la surcharge incorrecte de l’opérateur. Dans Visual Studio 2017, une erreur de compilateur est générée.

Cet exemple se compile dans Visual Studio 2015, mais génère une erreur dans Visual Studio 2017. Pour résoudre ce problème, rendez le membre du paramètre de modèle accessible là où il est évalué.

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
