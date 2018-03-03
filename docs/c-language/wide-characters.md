---
title: "Caractères larges | Microsoft Docs"
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
- wide characters
ms.assetid: 165c4a12-8ab9-45fb-9964-c55e9956194c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ab885d5d807fe81b3058d533a70cdbaa9e3e523a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="wide-characters"></a>Caractères étendus
**ANSI 3.1.3.4** Valeur d'une constante caractère entière qui contient plusieurs caractères ou d'une constante à caractères larges qui contient plusieurs caractères multioctets  
  
 La constante à caractères normaux, 'ab', a la valeur entière (int) 0x6162. Dans le cas de plusieurs octets, les octets lus précédemment sont décalés à gauche de la valeur de **CHAR_BIT** et l'octet suivant est comparé à l'aide de l'opérateur de bits OR aux bits de poids faible de **CHAR_BIT**. Le nombre d'octets dans la constante caractère multioctet ne peut pas dépasser sizeof(int), qui est de 4 pour un code cible 32 bits.  
  
 La constante caractère multioctet est lue comme ci-dessus et est convertie en constante à caractères larges au moyen de la fonction runtime `mbtowc`. Si le résultat n'est pas une constante à caractères larges valide, une erreur est émise. Dans tous les cas, le nombre d'octets examinés par la fonction `mbtowc` est limité à la valeur de `MB_CUR_MAX`.  
  
## <a name="see-also"></a>Voir aussi  
 [Caractères](../c-language/characters.md)