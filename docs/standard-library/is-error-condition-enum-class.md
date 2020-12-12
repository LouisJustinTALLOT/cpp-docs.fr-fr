---
description: 'En savoir plus sur : classe is_error_condition_enum'
title: is_error_condition_enum, classe
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_condition_enum
helpviewer_keywords:
- is_error_condition_enum class
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
ms.openlocfilehash: 3fd4f95e06ebee66a1f4d7d0e7de039d26b9f1fe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323726"
---
# <a name="is_error_condition_enum-class"></a>is_error_condition_enum, classe

Représente un prédicat de type qui teste l’énumération [error_condition](../standard-library/error-condition-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <_Enum>
    class is_error_condition_enum;
```

## <a name="remarks"></a>Notes

Une instance de ce [prédicat de type](../standard-library/type-traits.md) contient la valeur true si le type `_Enum` est une valeur d’énumération adaptée au stockage dans un objet de type `error_condition`.

Il est permis d’ajouter des spécialisations à ce type pour les types définis par l’utilisateur.

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
