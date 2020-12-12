---
description: 'En savoir plus sur : structure is_error_code_enum'
title: is_error_code_enum, structure
ms.date: 11/04/2016
f1_keywords:
- future/std::is_error_code_enum
ms.assetid: 84ae4b99-66d2-41ba-9b50-645fcbe14630
ms.openlocfilehash: 0de1d5562fd59e72e43c5844421f4ce6b30fe7c6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231119"
---
# <a name="is_error_code_enum-structure"></a>is_error_code_enum, structure

Spécialisation qui indique que [future_errc](../standard-library/future-enums.md#future_errc) est adapté au stockage d’un [error_code](../standard-library/error-code-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <>
struct is_error_code_enum<Future_errc> : public true_type;
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<future>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<future>](../standard-library/future.md)
