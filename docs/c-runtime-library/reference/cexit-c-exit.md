---
title: _cexit, _c_exit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _c_exit
- _cexit
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _cexit
- c_exit
- _c_exit
- cexit
dev_langs:
- C++
helpviewer_keywords:
- cleanup operations during processes
- cexit function
- _c_exit function
- _cexit function
- c_exit function
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: a68b803ee7dc444439d7a62f43cf7157e7fbf505
ms.contentlocale: fr-fr
ms.lasthandoff: 03/29/2017

---
# <a name="cexit-cexit"></a>_cexit, _c_exit
Effectue des opérations de nettoyage et retourne le contrôle sans mettre fin au processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void _cexit( void );  
void _c_exit( void );  
```  
  
## <a name="remarks"></a>Notes  
 La fonction `_cexit` appelle, dans l’ordre « dernier entré, premier sorti » (LIFO), les fonctions enregistrées par `atexit` et `_onexit`. Ensuite, `_cexit` vide toutes les mémoires tampons d’E/S et ferme tous les flux ouverts avant de retourner le contrôle. `_c_exit` est identique à `_exit`, mais retourne le contrôle au processus appelant sans traiter `atexit` ou `_onexit` ou vider de mémoires tampons de flux. Le comportement de `exit`,`_exit`, `_cexit` et `_c_exit`est indiqué dans le tableau suivant.  
  
|Fonction|Comportement|  
|--------------|--------------|  
|`exit`|Exécute les procédures d’arrêt complètes de la bibliothèque C, termine le processus et quitte avec le code d’état fourni.|  
|`_exit`|Exécute les procédures d’arrêt rapides de la bibliothèque C, termine le processus et quitte avec le code d’état fourni.|  
|`_cexit`|Exécute les procédures d’arrêt complètes de la bibliothèque C et retourne à l’appelant, mais ne termine pas le processus.|  
|`_c_exit`|Exécute les procédures d’arrêt rapides de la bibliothèque C et retourne à l’appelant, mais ne termine pas le processus.|  
  
 Quand vous appelez la fonction `_cexit` ou `_c_exit`, les destructeurs pour les objets temporaires ou automatiques qui existent au moment de l’appel ne sont pas appelés. Un objet automatique est un objet défini dans une fonction où l’objet n’est pas déclaré comme statique. Un objet temporaire est un objet créé par le compilateur. Pour détruire un objet automatique avant d’appeler `_cexit` ou `_c_exit`, appelez explicitement le destructeur de l’objet, comme suit :  
  
```  
myObject.myClass::~myClass( );  
```  
  
## <a name="requirements"></a>Spécifications  
  
|Routine|En-tête requis|  
|-------------|---------------------|  
|`_cexit`|\<process.h>|  
|`_c_exit`|\<process.h>|  
  
 Pour plus d’informations sur la compatibilité, consultez [Compatibilité](../../c-runtime-library/compatibility.md) dans l’introduction.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [_exec, _wexec, fonctions](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit, _onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_spawn, _wspawn, fonctions](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)
