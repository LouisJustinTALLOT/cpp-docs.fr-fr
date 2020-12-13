---
description: 'En savoir plus sur : classe type_index'
title: type_index, classe
ms.date: 11/04/2016
f1_keywords:
- typeindex/std::type_index
helpviewer_keywords:
- type_index class
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
ms.openlocfilehash: 4e9156420811d2712a5b9331d0ece0e7847103e9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142686"
---
# <a name="type_index-class"></a>type_index, classe

La classe `type_index` encapsule un pointeur dans la [classe type_info](../cpp/type-info-class.md) pour faciliter l’indexation par ces objets.

la classe type_index {public : type_index (const type_info& TINFO), const char * Name () const ; size_t hash_code () const ; bool, opérateur = = (const type_info& droite) const ; bool, opérateur ! = (const type_info& droite) const ; bool, opérateur< (const type_info& droite) const ; bool, opérateur \<=(const type_info& right) const;
   bool operator> (const type_info& droite) const ; opérateur bool>= (const type_info& droite) const ;};

Le constructeur initialise `ptr` à `&tinfo`.

`name` retourne `ptr->name()`.

`hash_code` retourne `ptr->hash_code().`

`operator==` retourne `*ptr == right.ptr`.

`operator!=` retourne `!(*this == right)`.

`operator<` retourne `*ptr->before(*right.ptr)`.

`operator<=` retourne `!(right < *this).`

`operator>` retourne `right < *this`.

`operator>=` retourne `!(*this < right)`.

## <a name="see-also"></a>Voir aussi

[Informations de type au moment de l’exécution](../cpp/run-time-type-information.md)\
[\<typeindex>](../standard-library/typeindex.md)
