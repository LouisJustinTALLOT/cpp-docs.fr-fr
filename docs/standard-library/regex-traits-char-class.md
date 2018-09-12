---
title: regex_traits&lt;char&gt;, classe | Microsoft Docs
ms.custom: ''
ms.date: 09/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- regex/std::regex_traits<char>
dev_langs:
- C++
helpviewer_keywords:
- regex_traits<char> class
ms.assetid: ce95ebcd-3687-4ad5-bf1d-b89fdc633675
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f5d02ebae152a78bfc99682afc20e33ba71b015
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691560"
---
# <a name="regextraitsltchargt-class"></a>regex_traits&lt;char&gt;, classe

Spécialisation de `regex_traits` pour **char**.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
class regex_traits<char>
```

## <a name="remarks"></a>Notes

La classe est une spécialisation explicite de la classe de modèle [regex_traits](../standard-library/regex-traits-class.md) pour les éléments de type **char** (afin qu’elle puisse tirer parti des fonctions de bibliothèque qui manipulent des objets de ce type).

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
