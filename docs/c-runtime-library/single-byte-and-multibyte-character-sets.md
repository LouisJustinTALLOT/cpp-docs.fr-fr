---
title: "Jeux de caractères codés sur un octet et multioctets | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.character.multibyte
dev_langs: C++
helpviewer_keywords:
- SBCS (single byte character set)
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- character sets [C++], single byte
ms.assetid: 2cbc78ea-33c0-4cfb-b0df-7ce2458431ce
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b1ee6738d55f2a925c510ff342cd289f26bc8669
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="single-byte-and-multibyte-character-sets"></a>Jeux de caractères codés sur un octet et multioctets
Le jeu de caractères ASCII définit les caractères compris dans la plage 0x00 à 0x7F. Il existe plusieurs autres jeux de caractères, principalement européens, qui définissent les caractères de la plage 0x00 - 0x7F de la même façon que le jeu de caractères ASCII, et qui définissent également un jeu de caractères étendu de la plage 0x80 - 0xFF. Par conséquent un jeu de caractères codés sur un octet de 8 bits (`SBCS`) est suffisant pour représenter le jeu de caractères ASCII, ainsi que les jeux de caractères de nombreuses langues européennes. Toutefois, certains jeux de caractères non européens, tels que les Kanji japonais, comprennent un trop grand nombre de caractères qui ne peuvent pas être représentés dans un schéma de codage sur un octet, et nécessitent donc un encodage à l’aide du jeu de caractères multioctets (`MBCS`).  
  
> [!NOTE]
>  De nombreuses routines `SBCS` de la bibliothèque runtime Microsoft peuvent gérer les octets, les caractères et les chaînes multioctets. Plusieurs jeux de caractères multioctets définissent le jeu de caractères ASCII comme un sous-ensemble. Dans de nombreux jeux de caractères multioctets, chaque caractère de la plage 0x00-0x7F est identique au caractère qui a la même valeur dans le jeu de caractères ASCII. Par exemple, dans les chaînes de caractères `ASCII` et `MBCS`, un caractère `NULL` d’un octet ('\0') a la valeur 0x00 et représente le caractère Null de fin.  
  
 Un jeu de caractères multioctets peut contenir à la fois des caractères sur un octet et des caractères sur deux octets. Par conséquent, une chaîne de caractères multioctets peut contenir un mélange de caractères codés sur un et deux octets. Un caractère codé sur deux octets est constitué d’un octet de tête et d’un octet de fin. Dans un jeu de caractères multioctets, les octets de tête sont compris dans une plage et les octets de fin dans une autre. Lorsque ces plages se superposent, il peut être nécessaire d’évaluer le contexte afin de déterminer si un octet donné fonctionne comme un octet de tête ou un octet de fin.  
  
## <a name="see-also"></a>Voir aussi  
 [Internationalisation](../c-runtime-library/internationalization.md)   
 [Routines runtime par catégorie](../c-runtime-library/run-time-routines-by-category.md)