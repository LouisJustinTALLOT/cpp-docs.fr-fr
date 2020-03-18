---
title: '&lt;system_error&gt;, fonctions'
ms.date: 03/15/2019
f1_keywords:
- system_error/std::generic_category
- system_error/std::make_error_code
- system_error/std::make_error_condition
- system_error/std::system_category
ms.assetid: 57d6f15f-f0b7-4e2f-80fe-31d3c320ee33
helpviewer_keywords:
- std::generic_category
- std::make_error_code
- std::make_error_condition
- std::system_category
ms.openlocfilehash: ab4d0d1ee810df8f719bba762262eb03bf899408
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422422"
---
# <a name="ltsystem_errorgt-functions"></a>&lt;system_error&gt;, fonctions

## <a name="generic_category"></a>generic_category

Représente la catégorie des erreurs génériques.

```cpp
const error_category& generic_category() noexcept;
```

### <a name="remarks"></a>Notes

L’objet `generic_category` est une implémentation de [error_category](../standard-library/error-category-class.md).

## <a name="is_error_code_enum_v"></a>is_error_code_enum_v

```cpp
template <class T> 
    inline constexpr bool is_error_code_enum_v = is_error_code_enum<T>::value;
```

## <a name="is_error_condition_enum_v"></a>is_error_condition_enum_v

```cpp
template <class T> 
    inline constexpr bool is_error_condition_enum_v = is_error_condition_enum<T>::value;
```

## <a name="make_error_code"></a>make_error_code

Crée un objet de code d’erreur.

```cpp
error_code make_error_code(std::errc error) noexcept;
```

### <a name="parameters"></a>Paramètres

*erreur*\
`std::errc` valeur d’énumération à stocker dans l’objet de code d’erreur.

### <a name="return-value"></a>Valeur de retour

L’objet de code d’erreur.

### <a name="remarks"></a>Notes

## <a name="make_error_condition"></a>make_error_condition

Crée un objet de condition d’erreur.

```cpp
error_condition make_error_condition(std::errc error) noexcept;
```

### <a name="parameters"></a>Paramètres

*erreur*\
`std::errc` valeur d’énumération à stocker dans l’objet de code d’erreur.

### <a name="return-value"></a>Valeur de retour

L’objet de condition d’erreur.

### <a name="remarks"></a>Notes

## <a name="system_category"></a>system_category

Représente la catégorie des erreurs provoquées par des dépassements de capacité du système de bas niveau.

```cpp
const error_category& system_category() noexcept;
```

### <a name="remarks"></a>Notes

L’objet `system_category` est une implémentation de [error_category](../standard-library/error-category-class.md).
