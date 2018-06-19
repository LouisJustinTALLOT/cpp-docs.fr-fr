---
title: is_trivially_copy_constructible, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01c95007f1db1bcaf549398fa8865a9e51fe23d1
ms.sourcegitcommit: 96cdc2da0d8c3783cc2ce03bd280a5430e1ac01d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33954100"
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible, classe

Teste si le type a un constructeur de copie trivial.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_trivially_copy_constructible;
```

### <a name="parameters"></a>Paramètres

`T` Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type `T` est une classe qui a un constructeur de copie trivial. Sinon, sa valeur est false.

Un constructeur de copie d’une classe `T` est trivial s’il est déclaré implicitement, si la classe `T` n’a aucune ou aucune base virtuelle, si toutes les bases directes de la classe `T` ont des constructeurs de copie triviaux, si les classes de toutes les données membres non statiques de type classe ont des constructeurs de copie triviaux, et si les classes de toutes les données membres non statiques de type tableau de classe ont des constructeurs de copie triviaux.

## <a name="requirements"></a>Spécifications

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
