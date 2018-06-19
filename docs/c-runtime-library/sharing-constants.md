---
title: Partage de constantes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _SH_DENYNO
- _SH_DENYRD
- _SH_DENYRW
- _SH_DENYWR
- _SH_COMPAT
dev_langs:
- C++
helpviewer_keywords:
- _SH_DENYRW constant
- SH_DENYRD constant
- _SH_COMPAT constant
- _SH_DENYRD constant
- SH_DENYRW constant
- sharing constants
- SH_DENYNO constant
- _SH_DENYWR constant
- SH_DENYWR constant
- _SH_DENYNO constant
- SH_COMPAT constant
ms.assetid: 95fadc3a-55dc-473d-98b5-e8211900465d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41060a9dbd3d2bc8176a2b13233db54933a6428b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409701"
---
# <a name="sharing-constants"></a>Partage de constantes
Constantes pour les modes de partage de fichiers.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <share.h>  
  
```  
  
## <a name="remarks"></a>Notes  
 L’argument *shflag* détermine le mode de partage, qui se compose d’une ou plusieurs des constantes manifestes. Elles peuvent être combinées avec les arguments *oflag* (voir [Constantes de fichier](../c-runtime-library/file-constants.md)).  
  
 Le tableau suivant répertorie les constantes et leur signification :  
  
|Constante|Signification|  
|--------------|-------------|  
|`_SH_DENYRW`|Refuse l'accès en lecture et en écriture à un fichier|  
|`_SH_DENYWR`|Refuse l'accès en écriture à un fichier|  
|`_SH_DENYRD`|Refuse l'accès en lecture à un fichier|  
|`_SH_DENYNO`|Autorise l'accès en lecture et en écriture|  
|`_SH_SECURE`|Définit le mode sécurisé (lecture partagée, accès en écriture exclusif).|  
  
## <a name="see-also"></a>Voir aussi  
 [_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)