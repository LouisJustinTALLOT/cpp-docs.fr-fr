---
title: _set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _set_invalid_parameter_handler
- _set_thread_local_invalid_parameter_handler
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
- set_invalid_parameter_handler
- _set_invalid_parameter_handler
- _set_thread_local_invalid_parameter_handler
dev_langs: C++
helpviewer_keywords:
- invalid parameter handler
- set_invalid_parameter_handler function
- _set_invalid_parameter_handler function
- _set_thread_local_invalid_parameter_handler function
ms.assetid: c0e67934-1a41-4016-ad8e-972828f3ac11
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2eeda6539e10bd785e5b4ee63091e208ff159f43
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="setinvalidparameterhandler-setthreadlocalinvalidparameterhandler"></a>_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler
Définit une fonction qui doit être appelée quand la bibliothèque CRT détecte un argument non valide.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_invalid_parameter_handler _set_invalid_parameter_handler(  
   _invalid_parameter_handler pNew  
);  
_invalid_parameter_handler _set_thread_local_invalid_parameter_handler(  
   _invalid_parameter_handler pNew  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `pNew`  
 Pointeur de fonction désignant le nouveau gestionnaire de paramètre non valide.  
  
## <a name="return-value"></a>Valeur de retour  
 Pointeur désignant le gestionnaire de paramètre non valide avant l’appel.  
  
## <a name="remarks"></a>Notes  
 De nombreuses fonctions Runtime C vérifient la validité des arguments qui leur sont transmis. Si un argument non valide est transmis, la fonction peut définir le numéro d’erreur `errno` ou retourner un code d’erreur. En pareils cas, le gestionnaire de paramètre non valide est aussi appelé. Le runtime C fournit un gestionnaire de paramètre non valide global par défaut qui met fin au programme et affiche un message d’erreur de runtime. Vous pouvez utiliser `_set_invalid_parameter_handler` pour définir votre propre fonction en tant que gestionnaire de paramètre non valide global. Le Runtime C prend aussi en charge un gestionnaire de paramètre non valide de thread local. Si un gestionnaire de paramètre de thread local est défini dans un thread à l’aide de `_set_thread_local_invalid_parameter_handler`, les fonctions du Runtime C appelées à partir du thread utilisent ce gestionnaire à la place du gestionnaire global. Vous ne pouvez définir qu’une seule fonction comme gestionnaire d’argument non valide global à la fois. De la même manière, vous ne pouvez spécifier qu’une seule fonction comme gestionnaire d’argument non valide de thread local par thread. Par contre, les différents threads peuvent avoir des gestionnaires de thread local distincts. Vous pouvez ainsi remplacer le gestionnaire utilisé dans une partie de votre code sans affecter le comportement des autres threads.  
  
 Quand le runtime appelle la fonction de paramètre non valide, cela signifie généralement qu’une erreur irrécupérable s’est produite. La fonction de gestionnaire de paramètre non valide que vous fournissez doit enregistrer toutes les données qu’elle peut avant d’abandonner. Elle ne doit pas retourner le contrôle à la fonction principale, sauf si vous êtes certain que l’erreur est récupérable.  
  
 La fonction de gestionnaire de paramètre non valide doit avoir le prototype suivant :  
  
```  
void _invalid_parameter(  
   const wchar_t * expression,  
   const wchar_t * function,   
   const wchar_t * file,   
   unsigned int line,  
   uintptr_t pReserved  
);  
```  
  
 L’argument `expression` est une représentation de chaîne large de l’expression d’argument qui a généré l’erreur. L’argument `function` correspond au nom de la fonction CRT qui a reçu l’argument non valide. L’argument `file` correspond au nom du fichier source CRT qui contient la fonction. L’argument `line` correspond au numéro de ligne dans ce fichier. Le dernier argument est réservé. Les paramètres ont tous la valeur `NULL`, à moins qu’une version debug de la bibliothèque CRT soit utilisée.  
  
## <a name="requirements"></a>Spécifications  
  
|Routine|En-tête requis|  
|-------------|---------------------|  
|`_set_invalid_parameter_handler`, `_set_thread_local_invalid_parameter_handler`|C : \<stdlib.h><br /><br /> C++ : \<cstdlib> ou \<stdlib.h>|  
  
 Les fonctions `_set_invalid_parameter_handler` et `_set_thread_local_invalid_parameter_handler` sont propres à Microsoft. Pour plus d’informations sur la compatibilité, consultez [Compatibilité](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, un gestionnaire d’erreur de paramètre non valide est utilisé pour imprimer la fonction qui a reçu le paramètre non valide, ainsi que le fichier et la ligne des sources CRT. Quand la bibliothèque CRT de débogage est utilisée, les erreurs de paramètre non valide déclenchent aussi une assertion, ce qui est désactivé dans cet exemple via [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md).  
  
```C  
// crt_set_invalid_parameter_handler.c  
// compile with: /Zi /MTd  
#include <stdio.h>  
#include <stdlib.h>  
#include <crtdbg.h>  // For _CrtSetReportMode  
  
void myInvalidParameterHandler(const wchar_t* expression,  
   const wchar_t* function,   
   const wchar_t* file,   
   unsigned int line,   
   uintptr_t pReserved)  
{  
   wprintf(L"Invalid parameter detected in function %s."  
            L" File: %s Line: %d\n", function, file, line);  
   wprintf(L"Expression: %s\n", expression);  
   abort();  
}  
  
int main( )  
{  
   char* formatString;  
  
   _invalid_parameter_handler oldHandler, newHandler;  
   newHandler = myInvalidParameterHandler;  
   oldHandler = _set_invalid_parameter_handler(newHandler);  
  
   // Disable the message box for assertions.  
   _CrtSetReportMode(_CRT_ASSERT, 0);  
  
   // Call printf_s with invalid parameters.  
  
   formatString = NULL;  
   printf(formatString);  
}  
```  
  
```Output  
Invalid parameter detected in function common_vfprintf. File: minkernel\crts\ucrt\src\appcrt\stdio\output.cpp Line: 32  
Expression: format != nullptr  
```  
  
## <a name="see-also"></a>Voir aussi  
 [_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)   
 [Versions à la sécurité améliorée des fonctions CRT](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)   
 [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)