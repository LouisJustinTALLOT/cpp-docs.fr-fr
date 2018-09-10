---
title: is_trivially_default_constructible, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_default_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73bdd8186f2ce56e4a6ecec0fa4f9468d9da8e8c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102705"
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible, classe

Teste si le type a un constructeur par défaut trivial.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_default_constructible;
```

### <a name="parameters"></a>Paramètres

*Ty*<br/>
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *Ty* est une classe qui a un constructeur trivial, sinon, sa valeur est false.

Un constructeur par défaut pour une classe *Ty* est trivial si :

- il s'agit d'un constructeur par défaut déclaré implicitement ;

- la classe *Ty* n’a aucune fonction virtuelle

- la classe *Ty* n’a aucune base virtuelle ;

- toutes les bases directes de la classe *Ty* ont des constructeurs triviaux

- les classes de tous les membres de données non statiques de type de classe ont des constructeurs triviaux ;

- les classes de tous les membres de données non statiques de type tableau de classe ont des constructeurs triviaux.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
