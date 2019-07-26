---
title: is_error_code_enum, structure
ms.date: 11/04/2016
f1_keywords:
- future/std::is_error_code_enum
ms.assetid: 84ae4b99-66d2-41ba-9b50-645fcbe14630
ms.openlocfilehash: f2a9f0d6b812b430ba3fca2d39343f912791da6f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452613"
---
# <a name="iserrorcodeenum-structure"></a>is_error_code_enum, structure

Spécialisation qui indique que [future_errc](../standard-library/future-enums.md#future_errc) est adapté au stockage d’un [error_code](../standard-library/error-code-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <>
struct is_error_code_enum<Future_errc> : public true_type;
```

## <a name="requirements"></a>Configuration requise

**En-tête:** \<> à venir

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<future>](../standard-library/future.md)
