---
title: Constantes fseek, _lseek | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- SEEK_END
- SEEK_SET
- SEEK_CUR
dev_langs:
- C++
helpviewer_keywords:
- SEEK_SET constant
- SEEK_END constant
- SEEK_CUR constant
ms.assetid: 9deeb13e-5aa3-4c33-80d8-721c80a4de9d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fbcf0a1106610740a585b7e4f8b68e3fc9b6a8f7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32388446"
---
# <a name="fseek-lseek-constants"></a>fseek, _lseek, constantes
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <stdio.h>  
  
```  
  
## <a name="remarks"></a>Notes  
 L’argument *origin* spécifie la position initiale et peut prendre l’une des constantes manifestes suivantes :  
  
|Constante|Signification|  
|--------------|-------------|  
|`SEEK_END`|Fin du fichier|  
|`SEEK_CUR`|Position actuelle du pointeur de fichier|  
|`SEEK_SET`|Début du fichier|  
  
## <a name="see-also"></a>Voir aussi  
 [fseek, _fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)   
 [_lseek, _lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)