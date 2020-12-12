---
description: 'En savoir plus sur : struct to_chars_result'
title: to_chars_result, struct
ms.date: 07/22/2020
f1_keywords:
- charconv/std::to_chars_result
helpviewer_keywords:
- to_chars_result class
- to_chars_result structure
ms.openlocfilehash: fb043ba928f086549aea326419ec3a2d673723ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167186"
---
# <a name="to_chars_result-struct"></a>to_chars_result, struct

## <a name="syntax"></a>Syntaxe

```cpp
struct to_chars_result {
    char* ptr;
    errc ec;
};
```

## <a name="members"></a>Membres

|Membre|Description|
|--|--|
|`ptr`| Si `ec` est égal à `errc{}` , la conversion a réussi et `ptr` est le pointeur un-à-un-après---end des caractères écrits. Sinon, `ptr` a la valeur du `to_chars()` paramètre `last` et le contenu de la plage \[ First, Last) n’est pas spécifié.|
|`ec` | Code d’erreur de conversion. Pour obtenir des codes d’erreur spécifiques, consultez [`errc`](system-error-enums.md#errc) .|

## <a name="requirements"></a>Spécifications

**En-tête :**\<charconv>

**Espace de noms :** std

**Option du compilateur :** /std : c++ 17, ou version ultérieure, est requis

## <a name="see-also"></a>Voir aussi

[to_chars](charconv-functions.md#to_chars)
