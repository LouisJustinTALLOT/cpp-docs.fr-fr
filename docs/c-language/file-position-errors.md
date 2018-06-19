---
title: Erreurs de position de fichier | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- file pointers [C++], file position errors
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71c059939891680b638e8644f7902d54452f5332
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383215"
---
# <a name="file-position-errors"></a>Erreurs de position de fichier
**ANSI 4.9.9.1, 4.9.9.4** Valeur à laquelle la macro `errno` est définie par la fonction `fgetpos` ou `ftell` en cas d'échec  
  
 Lorsque `fgetpos` ou `ftell` échoue, `errno` prend comme valeur la constante de manifeste `EINVAL` si la position n’est pas valide ou `EBADF` si le numéro de fichier est incorrect. Les constantes sont définies dans ERRNO.H.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions des bibliothèques](../c-language/library-functions.md)
