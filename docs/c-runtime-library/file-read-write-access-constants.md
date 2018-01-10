---
title: "Constantes d'accès fichier en lecture/écriture | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.constants.file
dev_langs: C++
helpviewer_keywords:
- read/write access constants
- write access constants
- access constants for file read/write
- constants [C++], file attributes
- file read/write access constants
ms.assetid: 56cd1d22-39a5-4fcf-bea2-7046d249e8ee
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 789d0ae6b0b9b38312896adf079e7c10dcde7556
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="file-readwrite-access-constants"></a>Constantes d'accès fichier en lecture/écriture
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <stdio.h>  
```  
  
## <a name="remarks"></a>Notes  
 Ces constantes spécifient le type d’accès (« a », « r » ou « w ») demandé pour le fichier. Le [mode de traduction](../c-runtime-library/file-translation-constants.md) (« b » ou « t ») et le [mode commit-to-disk](../c-runtime-library/commit-to-disk-constants.md) (« c » ou « n ») peut tous deux être spécifiés avec le type d’accès.  
  
 Les types d’accès sont décrits ci-dessous.  
  
 **"a"**  
 Ouvre pour l'écriture à la fin du fichier (ajout) ; crée d'abord le fichier s'il n'existe pas. Toutes les opérations d’écriture se produisent à la fin du fichier. Même si le pointeur de fichier peut être repositionné à l'aide de `fseek` ou **rewind**, mais il est toujours redéplacé à la fin du fichier avant toute opération d'écriture.  
  
 **"a+"**  
 Comme ci-dessus, mais permet aussi la lecture.  
  
 **"r"**  
 Ouvre pour l'accès en lecture. Si le fichier n'existe pas ou est introuvable, l'appel pour ouvert le fichier échoue.  
  
 **"r+"**  
 Ouvre pour l'accès en lecture et en écriture. Si le fichier n'existe pas ou est introuvable, l'appel pour ouvert le fichier échoue.  
  
 **"w"**  
 Ouvre un fichier vide pour l'accès en écriture. Si le fichier spécifié existe, son contenu est détruit.  
  
 **"w+"**  
 Ouvre un fichier vide pour l'accès en lecture et en écriture. Si le fichier spécifié existe, son contenu est détruit.  
  
 Quand le type d'accès « r+ », « w+ » ou « a+ » est spécifié, la lecture et l'écriture sont autorisées (on dit que le fichier est ouvert pour mise à jour). Cependant, quand vous basculez entre lecture et écriture, une opération intermédiaire `fflush`, `fsetpos`, `fseek` ou **rewind** doit exister. La position actuelle peut être spécifiée pour l'opération `fsetpos` ou `fseek`.  
  
## <a name="see-also"></a>Voir aussi  
 [_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)   
 [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)