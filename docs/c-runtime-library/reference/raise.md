---
title: raise | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- raise
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
- Raise
dev_langs:
- C++
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
ms.assetid: a3ccd3ad-f68f-4a7b-a005-c3ebfb217e8b
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 9cfcedc524b94d0aa6c381416c445cf62f9cf2fb
ms.contentlocale: fr-fr
ms.lasthandoff: 03/29/2017

---
# <a name="raise"></a>raise
Envoie un signal au programme en cours d’exécution.  
  
> [!NOTE]
>  N'utilisez pas cette méthode pour arrêter une application [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)], sauf dans les scénarios de test ou de débogage. Les façons de fermer une application [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] par programmation ou via l’interface utilisateur ne sont pas autorisées d’après la section 3.6 des [Critères de certification pour les applications Windows 8](http://go.microsoft.com/fwlink/?LinkId=262889). Pour plus d’informations, consultez [Cycle de vie de l’application (applications du Windows Store)](http://go.microsoft.com/fwlink/?LinkId=262853).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      int raise(  
int sig   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sig*  
 Signal à déclencher.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, **raise** retourne 0. Dans le cas contraire, une valeur différente de zéro est retournée.  
  
## <a name="remarks"></a>Notes  
 La fonction **raise** envoie *sig* au programme en cours d’exécution. Si un appel précédent à **signal** a installé une fonction de gestion de signal pour *sig*, **raise** exécute cette fonction. Si aucune fonction de gestionnaire n’a été installée, l’action par défaut associée à la valeur de signal *sig* est effectuée, comme suit.  
  
|Signal|Signification|Default|  
|------------|-------------|-------------|  
|`SIGABRT`|Arrêt anormal|Termine le programme appelant avec le code de sortie 3|  
|`SIGFPE`|Erreur de virgule flottante|Termine le programme appelant|  
|`SIGILL`|Instruction non conforme|Termine le programme appelant|  
|`SIGINT`|Interruption CTRL+C|Termine le programme appelant|  
|`SIGSEGV`|Accès au stockage non conforme|Termine le programme appelant|  
|`SIGTERM`|Demande d’arrêt envoyée au programme|Ignore le signal|  
  
 Si l’argument n’est pas un signal valide tel que spécifié ci-dessus, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). S’il n’est pas géré, la fonction affecte à `errno` la valeur `EINVAL` et retourne une valeur différente de zéro.  
  
## <a name="requirements"></a>Spécifications  
  
|Routine|En-tête requis|  
|-------------|---------------------|  
|**raise**|\<signal.h>|  
  
 Pour plus d’informations sur la compatibilité, consultez [Compatibilité](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Bibliothèques  
 Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [signal](../../c-runtime-library/reference/signal.md)
