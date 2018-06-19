---
title: -TLS | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /TLS
dev_langs:
- C++
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5e510f406ceae7508f9b84f99e7ab397d22f114
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373522"
---
# <a name="tls"></a>/TLS
Affiche la structure IMAGE_TLS_DIRECTORY à partir d’un fichier exécutable.  
  
## <a name="remarks"></a>Notes  
 /TLS affiche les champs de la structure TLS ainsi que les adresses des fonctions de rappel TLS.  
  
 Si un programme n’utilise pas le stockage local des threads, son image ne contient pas de structure TLS.  Consultez [thread](../../cpp/thread.md) pour plus d’informations.  
  
 IMAGE_TLS_DIRECTORY est défini dans winnt.h.  
  
## <a name="see-also"></a>Voir aussi  
 [DUMPBIN, options](../../build/reference/dumpbin-options.md)