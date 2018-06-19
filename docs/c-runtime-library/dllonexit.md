---
title: __dllonexit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __dllonexit
apilocation:
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcr120_clr0400.dll
apitype: DLLExport
f1_keywords:
- __dllonexit
dev_langs:
- C++
helpviewer_keywords:
- __dllonexit
ms.assetid: 708f2ceb-f95c-46b0-a58d-d68b3fa36f12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c0105ccc5a40c4e5fe789814adfabe6c9749650
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450717"
---
# <a name="dllonexit"></a>__dllonexit
Enregistre une routine à appeler au moment de la sortie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_onexit_t __dllonexit(   _onexit_t func,  
   _PVFV **  pbegin,   
   _PVFV **  pend   
   )  
```  
  
#### <a name="parameters"></a>Paramètres  
 `func`  
 Pointeur vers une fonction à exécuter à la sortie.  
  
 `pbegin`  
 Pointeur vers une variable qui pointe vers le début d’une liste de fonctions à exécuter au moment du détachement.  
  
 `pend`  
 Pointeur vers une variable qui pointe vers la fin d’une liste de fonctions à exécuter au moment du détachement.  
  
## <a name="return-value"></a>Valeur de retour  
 Si l’opération réussit, pointeur vers la fonction de l’utilisateur. Dans le cas contraire, pointeur **NULL**.  
  
## <a name="remarks"></a>Notes  
 La fonction `__dllonexit` est analogue à la fonction [_onexit](../c-runtime-library/reference/onexit-onexit-m.md) sauf que les variables globales utilisées par cette fonction ne sont pas visibles pour cette routine. Au lieu de variables globales, cette fonction utilise les paramètres `pbegin` et `pend`.  
  
 Les fonctions `_onexit` et `atexit` dans une DLL liée à MSVCRT.LIB doivent conserver leur propre liste atexit/_onexit. Cette routine est le processus de travail appelé par de telles DLL.  
  
 Le type `_PVFV` est défini en tant que `typedef void (__cdecl *_PVFV)(void)`.  
  
## <a name="requirements"></a>Configuration requise  
  
|Routine|Fichier obligatoire|  
|-------------|-------------------|  
|__dllonexit|onexit.c|  
  
## <a name="see-also"></a>Voir aussi  
 [_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)