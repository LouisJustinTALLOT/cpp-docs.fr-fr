---
title: Constantes d’autorisations de fichier | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _S_IWRITE
- _S_IREAD
dev_langs:
- C++
helpviewer_keywords:
- S_IWRITE constant
- constants [C++], file attributes
- S_IREAD constant
- file permissions [C++]
- _S_IWRITE constant
- _S_IREAD constant
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c016664bf107b9531553ef372dfc5dc28650ef7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389366"
---
# <a name="file-permission-constants"></a>Constantes d'autorisations de fichier
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <sys/stat.h>  
  
```  
  
## <a name="remarks"></a>Notes  
 Une de ces constantes est obligatoire quand `_O_CREAT` (`_open`, `_sopen`) est spécifié.  
  
 L’argument `pmode` spécifie les paramètres d’autorisation du fichier comme suit.  
  
|Constante|Signification|  
|--------------|-------------|  
|`_S_IREAD`|Lecture autorisée|  
|`_S_IWRITE`|Écriture autorisée|  
|`_S_IREAD` &#124; `_S_IWRITE`|Lecture et écriture autorisées|  
  
 Lorsqu’elle est utilisée en tant qu’argument `pmode` pour `_umask`, la constante manifeste définit le paramètre d’autorisation, comme suit.  
  
|Constante|Signification|  
|--------------|-------------|  
|`_S_IREAD`|Écriture non autorisée (le fichier est en lecture seule)|  
|`_S_IWRITE`|Lecture non autorisée (le fichier est en écriture seule)|  
|`_S_IREAD` &#124; `_S_IWRITE`|Pas d’autorisation en lecture ou écriture|  
  
## <a name="see-also"></a>Voir aussi  
 [_open, _wopen](../c-runtime-library/reference/open-wopen.md)   
 [_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [_umask](../c-runtime-library/reference/umask.md)   
 [Types standard](../c-runtime-library/standard-types.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)