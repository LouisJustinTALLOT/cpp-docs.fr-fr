---
title: regex_traits&lt;wchar_t&gt;, classe
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_traits<wchar_t>
helpviewer_keywords:
- regex_traits<wchar_t> class
ms.assetid: 288d6fdb-fb8e-4a4d-904a-53916be7f95b
ms.openlocfilehash: dd0b54470f026635c1e09829f37d02bbe8b3f0c0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217556"
---
# <a name="regex_traitsltwchar_tgt-class"></a>regex_traits&lt;wchar_t&gt;, classe

Spécialisation de `regex_traits` pour **`wchar_t`** .

## <a name="syntax"></a>Syntaxe

```cpp
template <>
class regex_traits<wchar_t>
```

## <a name="remarks"></a>Notes

La classe est une spécialisation explicite de la [regex_traits](../standard-library/regex-traits-class.md) de modèle de classe pour les éléments de type **`wchar_t`** (afin qu’elle puisse tirer parti des fonctions de bibliothèque qui manipulent des objets de ce type).

## <a name="requirements"></a>Spécifications

**En-tête :**\<regex>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<regex>](../standard-library/regex.md)\
[Classe regex_constants](../standard-library/regex-constants-class.md)\
[Classe regex_error](../standard-library/regex-error-class.md)\
[\<regex>Mission](../standard-library/regex-functions.md)\
[Classe regex_iterator](../standard-library/regex-iterator-class.md)\
[\<regex>Operator](../standard-library/regex-operators.md)\
[Classe regex_token_iterator](../standard-library/regex-token-iterator-class.md)\
[Classe regex_traits](../standard-library/regex-traits-class.md)\
[\<regex>typedefs](../standard-library/regex-typedefs.md)
