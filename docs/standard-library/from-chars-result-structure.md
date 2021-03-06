---
description: 'En savoir plus sur : struct from_chars_result'
title: from_chars_result, struct
ms.date: 7/23/2020
f1_keywords:
- std::from_chars_result
helpviewer_keywords:
- from_chars_result class
- from_chars_result structure
ms.openlocfilehash: 894a687a4395e22538b384675af5b4ce57731f78
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232276"
---
# <a name="from_chars_result-struct"></a>from_chars_result, struct

## <a name="syntax"></a>Syntaxe

```cpp
struct from_chars_result {
    const char* ptr;
    errc ec;
};
```

|Membre|Description|
|--|--|
|`ptr`| Si `ec` est égal à `errc{}` , la conversion a réussi et `ptr` pointe vers le premier caractère qui ne fait pas partie du nombre reconnu. |
|`ec` | Code d’erreur de conversion. Pour obtenir des codes d’erreur spécifiques, consultez [`errc`](system-error-enums.md#errc) .|

### <a name="remarks"></a>Notes

Exemple : `"1729cats"` l’analyse en tant qu’entier décimal est réussie et `ptr` pointe vers `'c'` qui est le premier non-chiffre et est également un-passé-le-fin de `"1729"` .

Si aucun caractère ne correspond à un modèle de nombre, `from_chars_result.ptr` pointe vers `first` et `from_chars_result.ec` est `errc::invalid_argument` .

Si seuls certains caractères correspondent à un modèle de nombre, `from_chars_result.ptr` pointe vers le premier caractère qui ne correspond pas au modèle, ou a la valeur du `last` paramètre si tous les caractères correspondent.

Si la valeur analysée ne correspond pas à la plage pour le type de conversion effectué, `from_chars_result.ec` est `errc::result_out_of_range` .

## <a name="requirements"></a>Spécifications

**En-tête :**\<charconv>

**Espace de noms :** std

**Option du compilateur :** /std : c++ 17, ou version ultérieure, est requis

## <a name="see-also"></a>Voir aussi

[from_chars](charconv-functions.md#from_chars)
