---
title: is_trivially_copy_assignable, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f7c4c748d7328f534aebfb2133c72635bbdc36f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953964"
---
# <a name="istriviallycopyassignable-class"></a>is_trivially_copy_assignable, classe

Teste si le type a un opérateur d'assignation de copie trivial.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Paramètres

*T* type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est une classe qui a un copie trivial opérateur d’assignation, sinon, sa valeur est false.

Un constructeur d’assignation pour une classe *T* est trivial s’il est fourni implicitement, la classe *T* n’a aucune fonction virtuelle, la classe *T* n’a aucune bases virtuelles, les classes de tous les membres de données non statiques de type de classe possèdent des opérateurs d’assignation triviaux, et les classes de tous les membres de données non statiques de type tableau de classe possèdent des opérateurs d’assignation triviaux.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
