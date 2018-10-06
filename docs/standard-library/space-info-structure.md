---
title: space_info, structure | Microsoft Docs
ms.custom: ''
ms.date: 09/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::tr2::sys::space_info
dev_langs:
- C++
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9bfbcbe990effa20fc91494e5586d3c34d47a0d5
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821234"
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

**En-tête :** \<filesystem >

**Espace de noms :** std::experimental::filesystem

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md)<br/>
