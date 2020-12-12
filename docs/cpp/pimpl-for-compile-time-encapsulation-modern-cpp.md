---
description: 'En savoir plus sur : PIMPL pour l’encapsulation Compile-Time (C++ moderne)'
title: Pimpl pour l'encapsulation au moment de la compilation (Modern C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
ms.openlocfilehash: 95d1ca4f377cc911e862885e86f846d8536d3b1f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145884"
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>Pimpl pour l'encapsulation au moment de la compilation (Modern C++)

L' *idiome PIMPL* est une technique C++ moderne qui permet de masquer l’implémentation, de réduire le couplage et de séparer les interfaces. PIMPL est short pour « pointeur vers implémentation ». Vous vous êtes peut-être déjà familiarisé avec le concept, mais vous le connaissez par d’autres noms tels que Cheshire Cat ou un idiome de pare-feu du compilateur.

## <a name="why-use-pimpl"></a>Pourquoi utiliser PIMPL ?

Voici comment l’idiome PIMPL peut améliorer le cycle de vie du développement de logiciels :

- Réduction des dépendances de compilation.

- Séparation de l’interface et de l’implémentation.

- Portabilité :

## <a name="pimpl-header"></a>En-tête PIMPL

```cpp
// my_class.h
class my_class {
   //  ... all public and protected stuff goes here ...
private:
   class impl; unique_ptr<impl> pimpl; // opaque type here
};
```

L’idiome PIMPL évite les régénération des cascades et des dispositions d’objets fragiles. Il convient parfaitement aux types populaires (transitivement).

## <a name="pimpl-implementation"></a>Implémentation de PIMPL

Définissez la `impl` classe dans le fichier. cpp.

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

## <a name="best-practices"></a>Meilleures pratiques

Déterminez s’il faut ajouter la prise en charge de la spécialisation d’échange sans levée.

## <a name="see-also"></a>Voir aussi

[Bienvenue dans C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
