---
title: Pimpl pour l’encapsulation au moment de la compilation (Modern C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
ms.openlocfilehash: 9a73ea1df099003061081d108a3f3f6eef601fb9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594361"
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>Pimpl pour l’encapsulation au moment de la compilation (Modern C++)

Le *pimpl idiome* est une technique de C++ moderne pour masquer l’implémentation, afin de minimiser le couplage et pour séparer les interfaces. Pimpl est l’abréviation de « pointeur vers l’implémentation ». Vous pouvez déjà être familiarisé avec le concept mais il connaître d’autres noms comme idiome malicieusement ou du compilateur pare-feu.

## <a name="why-use-pimpl"></a>Pourquoi utiliser pimpl ?

Voici comment l’idiome pimpl peut améliorer le cycle de vie de développement de logiciels :

- Réduction des dépendances de compilation.

- Séparation de l’interface et l’implémentation.

- Portabilité.

## <a name="pimpl-header"></a>Pimpl en-tête

```cpp
// my_class.h
class my_class {
   //  ... all public and protected stuff goes here ...
private:
   class impl; unique_ptr<impl> pimpl; // opaque type here
};
```

L’idiome pimpl évite les cascades de reconstruction et dispositions d’objet fragile. Il est bien adapté pour les types les plus courants (de manière transitive).

## <a name="pimpl-implementation"></a>Implémentation de Pimpl

Définir la `impl` classe dans le fichier .cpp.

```cpp
// my_class.cpp
class my_class::impl {  // defined privately here
  // ... all private data and functions: all of these
  //     can now change without recompiling callers ...
};
my_class::my_class(): pimpl( new impl )
{
  // ... set impl values ...
}
```

## <a name="best-practices"></a>Recommandations

Pensez à ajouter la prise en charge pour la spécialisation de permutation non lanceurs.

## <a name="see-also"></a>Voir aussi

[Bienvenue dans C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)