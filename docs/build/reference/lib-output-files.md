---
title: Fichiers de sortie LIB | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- output files, LIB
ms.assetid: e73d2f9b-a42d-402b-b7e3-3a94bebb317e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8caa26685d6132cbc1ffd8a2467f8615bffd42f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32370486"
---
# <a name="lib-output-files"></a>Fichiers de sortie LIB
Les fichiers de sortie produits par LIB dépendent du mode dans lequel il est utilisé, comme indiqué dans le tableau suivant.  
  
|Mode|Sortie|  
|----------|------------|  
|Par défaut (création ou modification d’une bibliothèque)|Bibliothèque COFF (.lib)|  
|Extraction d’un membre avec /EXTRACT|Fichier objet (.obj)|  
|Création d’une exportation de fichier et de bibliothèque avec /DEF d’importation|Bibliothèque d’importation (.lib) et fichier d’exportation (.exp)|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de LIB](../../build/reference/overview-of-lib.md)