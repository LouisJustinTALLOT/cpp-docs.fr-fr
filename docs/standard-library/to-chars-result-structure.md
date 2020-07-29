---
title: struct to_chars_result
ms.date: 07/22/2020
f1_keywords:
- charconv/std::to_chars_result
helpviewer_keywords:
- to_chars_result class
- to_chars_result structure
ms.openlocfilehash: a840b8d030f0ed0d2a4afcc57e1bef1161c76ff3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212059"
---
# <a name="to_chars_result-struct"></a>struct to_chars_result

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