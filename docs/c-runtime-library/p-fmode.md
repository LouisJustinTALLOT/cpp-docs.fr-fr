---
title: __p__fmode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __p__fmode
apilocation:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- __p__fmode
dev_langs:
- C++
helpviewer_keywords:
- __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c520f81062f1bbbb295f17c6bc041afb8b5f2877
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389834"
---
# <a name="pfmode"></a>__p__fmode
Pointe vers la variable globale `_fmode`, qui spécifie le *mode de traduction de fichiers* par défaut pour les opérations d’E/S de fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
int* __p__fmode(  
   );  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Pointeur vers la variable globale `_fmode`.  
  
## <a name="remarks"></a>Notes  
 La fonction `__p__fmode` est réservé exclusivement à un usage interne et ne doit pas être appelée à partir du code utilisateur.  
  
 Le mode de traduction de fichiers spécifie une traduction `binary` ou `text` pour les opérations d’E/S [_open](../c-runtime-library/reference/open-wopen.md) et [_pipe](../c-runtime-library/reference/pipe.md). Pour plus d’informations, consultez [_fmode](../c-runtime-library/fmode.md).  
  
## <a name="requirements"></a>Configuration requise  
  
|Routine|En-tête requis|  
|-------------|---------------------|  
|__p\__fmode|stdlib.h|