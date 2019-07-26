---
title: is_trivially_default_constructible, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_default_constructible
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
ms.openlocfilehash: 19a5e8afedf3e59d5dafa937af4f7d35343eb7d9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459650"
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible, classe

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

Un constructeur par défaut pour une classe *Ty* est trivial si:

- il s'agit d'un constructeur par défaut déclaré implicitement ;

- la classe *Ty* n’a pas de fonctions virtuelles

- la classe *Ty* n’a aucune base virtuelle

- toutes les bases directes de la classe *Ty* ont des constructeurs simples

- les classes de tous les membres de données non statiques de type de classe ont des constructeurs triviaux ;

- les classes de tous les membres de données non statiques de type tableau de classe ont des constructeurs triviaux.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
