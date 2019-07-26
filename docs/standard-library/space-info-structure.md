---
title: space_info, structure
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::space_info
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
ms.openlocfilehash: 2a9856746a8bbc796871663a81bd8911d34dcd4a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457558"
---
# <a name="spaceinfo-structure"></a>space_info, structure

Contient des informations sur un volume.

## <a name="syntax"></a>Syntaxe

```cpp
struct space_info
{
    uintmax_t capacity;
    uintmax_t free;
    uintmax_t available;
};
```

## <a name="members"></a>Membres

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|`unsigned long long capacity`|Représente le nombre total d’octets que le volume peut représenter.|
|`unsigned long long free`|Représente le nombre d’octets qui ne sont pas utilisés pour représenter des données sur le volume.|
|`unsigned long long available`|Représente le nombre d’octets qui sont disponibles pour représenter des données sur le volume.|

## <a name="requirements"></a>Configuration requise

**En-tête:** \<> de système de fichiers

**Espace de noms :** std::experimental::filesystem

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md)
