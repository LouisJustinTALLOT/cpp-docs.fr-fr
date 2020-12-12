---
description: 'En savoir plus sur : classe is_error_code_enum'
title: is_error_code_enum, classe
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_code_enum
helpviewer_keywords:
- is_error_code_enum class
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
ms.openlocfilehash: 359f15c3d809435df81408a721a0c9ad11c1e7e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323753"
---
# <a name="is_error_code_enum-class"></a>is_error_code_enum, classe

Représente un prédicat de type qui teste l’énumération [error_code](../standard-library/error-code-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <_Enum>
    class is_error_code_enum;
```

## <a name="remarks"></a>Notes

Une instance de ce [prédicat de type](../standard-library/type-traits.md) contient la valeur true si le type `_Enum` est une valeur d’énumération adaptée au stockage dans un objet de type `error_code`.

Il est permis d’ajouter des spécialisations à ce type pour les types définis par l’utilisateur.

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
