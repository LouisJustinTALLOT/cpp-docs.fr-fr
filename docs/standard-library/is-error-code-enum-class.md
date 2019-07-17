---
title: is_error_code_enum, classe
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_code_enum
helpviewer_keywords:
- is_error_code_enum class
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
ms.openlocfilehash: bc4ed7cd2e058414448c9366011b9efab97ee3d5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245191"
---
# <a name="iserrorcodeenum-class"></a>is_error_code_enum, classe

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

[<type_traits>](../standard-library/type-traits.md)<br/>
