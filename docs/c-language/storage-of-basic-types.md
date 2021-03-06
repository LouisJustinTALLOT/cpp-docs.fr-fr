---
description: 'En savoir plus sur : stockage des types de base'
title: Stockage de types de base
ms.date: 10/02/2019
helpviewer_keywords:
- specifiers [C++], type
- integral types, storage
- storage [C++], types
- floating-point numbers, storage
- type specifiers [C++], sizes
- arithmetic operations [C++], types
- int data type
- short data type
- signed types [C++], storage
- long double keyword [C], storage
- long keyword [C]
- double data type, storage
- types [C], arithmetic
- integral types
- data types [C], specifiers
- storing types [C++]
- unsigned types [C++], storage
- data types [C], storage
ms.assetid: bd1f33c1-c6b9-4558-8a72-afb21aef3318
ms.openlocfilehash: c8ae057de19e04327491fd73e45bcd32c1db7738
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296639"
---
# <a name="storage-of-basic-types"></a>Stockage des types de base

Le tableau suivant résume le stockage associé à chaque type de base.

## <a name="sizes-of-fundamental-types"></a>Tailles des types fondamentaux

|Type|Stockage|
|----------|-------------|
|**`char`**, **`unsigned char`**, **`signed char`**|1 octet|
|**`short`**, **`unsigned short`**|2 octets|
|**`int`**, **`unsigned int`**|4 octets|
|**`long`**, **`unsigned long`**|4 octets|
|**`long long`**, **`unsigned long long`**|8 octets|
|**`float`**|4 octets|
|**`double`**|8 octets|
|**`long double`**|8 octets|

Les types de données C sont répartis dans des catégories générales. Les *types intégraux* incluent **`int`** , **`char`** ,, **`short`** **`long`** et **`long long`** . Ces types peuvent être qualifiés avec **`signed`** ou **`unsigned`** , et **`unsigned`** peuvent être utilisés comme raccourcis pour **`unsigned int`** . Les types énumération ( **`enum`** ) sont également traités comme des types intégraux dans la plupart des cas. Les *types flottants* incluent **`float`** , **`double`** et **`long double`** . Les *types arithmétiques* incluent tous les types flottants et intégraux.

## <a name="see-also"></a>Voir aussi

[Déclarations et types](../c-language/declarations-and-types.md)
