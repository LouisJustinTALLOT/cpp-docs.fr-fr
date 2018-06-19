---
title: Flux d'octets et flux larges | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- Byte and Wide Streams
dev_langs:
- C++
helpviewer_keywords:
- byte streams
- wide streams
ms.assetid: 61ef0587-4cbc-4eb8-aae5-4c298dbbc6f9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de026c8887e19e76bbce533db8997193679d1371
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389882"
---
# <a name="byte-and-wide-streams"></a>Flux d'octets et flux larges
Un flux d'octets traite un fichier comme une séquence d'octets. Dans le programme, le flux est la même séquence d’octets.  
  
 En revanche, un flux large traite un fichier comme une séquence de caractères multioctets généralisés, qui peut avoir un large éventail de règles de codage. (Les fichiers texte et binaires sont toujours lus et écrits comme décrit précédemment.) Dans le programme, le flux ressemble à la séquence correspondante de caractères larges. Des conversions entre les deux représentations se produisent dans la bibliothèque C standard. Les règles de conversion peuvent, en principe, être modifiées par un appel à [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) qui modifie la catégorie `LC_CTYPE`. Chaque flux large détermine ses règles de conversion au moment où il devient orienté large et les conserve même si la catégorie `LC_CTYPE` change ultérieurement.  
  
 Le positionnement dans un flux large subit les mêmes limitations que pour les flux de texte. En outre, l’indicateur de position de fichier peut également avoir à traiter avec un encodage dépendant de l’état. En règle générale, il inclut à la fois un décalage d’octets dans le flux de données et un objet de type `mbstate_t`. Par conséquent, la seule méthode fiable pour obtenir une position de fichier dans un flux large est d’appeler [fgetpos](../c-runtime-library/reference/fgetpos.md), et la seule méthode fiable pour restaurer un emplacement obtenu de cette façon est d’appeler [fsetpos](../c-runtime-library/reference/fsetpos.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers et flux](../c-runtime-library/files-and-streams.md)   
 [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)