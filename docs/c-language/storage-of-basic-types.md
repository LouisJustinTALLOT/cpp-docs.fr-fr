---
title: Stockage des types de base | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dff8df934a0c812ca798d5a1e87188e2468902ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="storage-of-basic-types"></a>Stockage de types de base
Le tableau suivant résume le stockage associé à chaque type de base.  
  
### <a name="sizes-of-fundamental-types"></a>Tailles des types fondamentaux  
  
|Type|Stockage|  
|----------|-------------|  
|`char`, `unsigned char`, **signed char**|1 octet|  
|**short**, **unsigned short**|2 octets|  
|`int`, `unsigned int`|4 octets|  
|**long**, `unsigned long`|4 octets|  
|**float**|4 octets|  
|**double**|8 octets|  
|`long double`|8 octets|  
  
 Les types de données C sont répartis dans des catégories générales. Les « types intégraux » incluent `char`, `int`, **short**, **long**, **signed**, `unsigned` et `enum`. Les « types flottants » sont **float**, **double** et `long double`. Les « types arithmétiques » incluent tous les types flottants et intégraux.  
  
## <a name="see-also"></a>Voir aussi  
 [Déclarations et types](../c-language/declarations-and-types.md)