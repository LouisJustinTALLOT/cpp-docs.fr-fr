---
title: regex_traits&lt;wchar_t&gt;, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- regex/std::regex_traits<wchar_t>
dev_langs:
- C++
helpviewer_keywords:
- regex_traits<wchar_t> class
ms.assetid: 288d6fdb-fb8e-4a4d-904a-53916be7f95b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 45710c4a1abca000b5cc8bca4a9db8032e874d9c
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958956"
---
# <a name="regextraitsltwchartgt-class"></a>regex_traits&lt;wchar_t&gt;, classe

Spécialisation de regex_traits pour wchar_t.

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

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants, classe](../standard-library/regex-constants-class.md)<br/>
[regex_error, classe](../standard-library/regex-error-class.md)<br/>
[\<regex>, fonctions](../standard-library/regex-functions.md)<br/>
[regex_iterator, classe](../standard-library/regex-iterator-class.md)<br/>
[\<regex>, opérateurs](../standard-library/regex-operators.md)<br/>
[regex_token_iterator, classe](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits, classe](../standard-library/regex-traits-class.md)<br/>
[\<regex>, typedefs](../standard-library/regex-typedefs.md)<br/>
