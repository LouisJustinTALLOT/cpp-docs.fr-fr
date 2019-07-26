---
title: regex_traits&lt;wchar_t&gt;, classe
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_traits<wchar_t>
helpviewer_keywords:
- regex_traits<wchar_t> class
ms.assetid: 288d6fdb-fb8e-4a4d-904a-53916be7f95b
ms.openlocfilehash: 1a1f08509a20b5a0eabb26b715e22bf7c6de544c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451476"
---
# <a name="regextraitsltwchartgt-class"></a>regex_traits&lt;wchar_t&gt;, classe

Spécialisation `regex_traits` de pour **wchar_t**.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
class regex_traits<wchar_t>
```

## <a name="remarks"></a>Notes

La classe est une spécialisation explicite de la classe de modèle [regex_traits](../standard-library/regex-traits-class.md) pour les éléments de type **wchar_t** (afin qu’elle puisse tirer parti des fonctions de bibliothèque qui manipulent des objets de ce type).

## <a name="requirements"></a>Configuration requise

**En-tête :** \<regex>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<regex>](../standard-library/regex.md)\
[regex_constants, classe](../standard-library/regex-constants-class.md)\
[regex_error, classe](../standard-library/regex-error-class.md)\
[\<fonctions Regex >](../standard-library/regex-functions.md)\
[regex_iterator, classe](../standard-library/regex-iterator-class.md)\
[\<opérateurs > Regex](../standard-library/regex-operators.md)\
[regex_token_iterator, classe](../standard-library/regex-token-iterator-class.md)\
[regex_traits, classe](../standard-library/regex-traits-class.md)\
[\<regex>, typedefs](../standard-library/regex-typedefs.md)
