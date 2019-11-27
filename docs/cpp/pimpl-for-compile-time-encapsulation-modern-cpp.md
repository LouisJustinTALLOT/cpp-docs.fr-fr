---
title: Pimpl pour l'encapsulation au moment de la compilation (Modern C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
ms.openlocfilehash: f1eb06ad3a52be486f085babf699677951b1ee71
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245174"
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>Pimpl pour l'encapsulation au moment de la compilation (Modern C++)

L' *idiome PIMPL* est une technique C++ moderne pour masquer l’implémentation, réduire le couplage et séparer les interfaces. PIMPL est short pour « pointeur vers implémentation ». Vous vous êtes peut-être déjà familiarisé avec le concept, mais vous le connaissez par d’autres noms tels que Cheshire Cat ou un idiome de pare-feu du compilateur.

## <a name="why-use-pimpl"></a>Pourquoi utiliser PIMPL ?

Voici comment l’idiome PIMPL peut améliorer le cycle de vie du développement de logiciels :

- Réduction des dépendances de compilation.

- Séparation de l’interface et de l’implémentation.

- Portabilité.

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

Définissez la classe `impl` dans le fichier. cpp.

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

## <a name="best-practices"></a>meilleures pratiques recommandées.

Déterminez s’il faut ajouter la prise en charge de la spécialisation d’échange sans levée.

## <a name="see-also"></a>Voir aussi

[Bienvenue dansC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
