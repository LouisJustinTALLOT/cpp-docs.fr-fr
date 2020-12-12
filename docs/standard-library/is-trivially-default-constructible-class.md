---
description: 'En savoir plus sur : classe is_trivially_default_constructible'
title: is_trivially_default_constructible, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_default_constructible
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
ms.openlocfilehash: 3686dab86b8bf04fe7629b53651988d7ccef161e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118405"
---
# <a name="is_trivially_default_constructible-class"></a>is_trivially_default_constructible, classe

Teste si le type a un constructeur par défaut trivial.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_default_constructible;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *Ty* est une classe qui a un constructeur trivial. sinon, sa valeur est false.

Un constructeur par défaut pour une classe *Ty* est trivial si :

- il s'agit d'un constructeur par défaut déclaré implicitement ;

- la classe *Ty* n’a pas de fonctions virtuelles

- la classe *Ty* n’a aucune base virtuelle

- toutes les bases directes de la classe *Ty* ont des constructeurs simples

- les classes de tous les membres de données non statiques de type de classe ont des constructeurs triviaux ;

- les classes de tous les membres de données non statiques de type tableau de classe ont des constructeurs triviaux.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
