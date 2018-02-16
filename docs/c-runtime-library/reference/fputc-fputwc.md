---
title: fputc, fputwc | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- fputc
- fputwc
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fputc
- fputwc
- _fputtc
dev_langs:
- C++
helpviewer_keywords:
- streams, writing characters to
- fputtc function
- _fputtc function
- fputwc function
- fputc function
ms.assetid: 5a0a593d-43f4-4fa2-a401-ec4e23de4d2f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: af95e4b11048ebda50ac4d73fc87b6b67903494b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="fputc-fputwc"></a>fputc, fputwc
Écrit un caractère dans un flux.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int fputc(  
   int c,  
   FILE *stream   
);  
wint_t fputwc(  
   wchar_t c,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `c`  
 Caractère à écrire.  
  
 `stream`  
 Pointeur vers la structure `FILE` .  
  
## <a name="return-value"></a>Valeur de retour  
 Chacune de ces fonctions retourne le caractère écrit. Pour `fputc`, une valeur de retour égale à `EOF` indique une erreur. Pour `fputwc`, une valeur de retour égale à `WEOF` indique une erreur. Si `stream` a la valeur `NULL`, ces fonctions appellent le gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à continuer, elles retournent `EOF` et définissent `errno` sur `EINVAL`.  
  
 Consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pour plus d’informations sur ces éléments et autres codes d’erreur.  
  
## <a name="remarks"></a>Notes  
 Chacune de ces fonctions écrit le caractère unique `c` dans un fichier à la position indiquée par l’indicateur de position de fichier associé (si défini) et avance l’indicateur comme il convient. Dans le cas de `fputc` et `fputwc`, le fichier est associé `stream`. Si le fichier ne peut pas prendre en charge les demandes de positionnement ou a été ouvert en mode ajout, le caractère est ajouté à la fin du flux.  
  
 Les deux fonctions se comportent de la même façon si le flux est ouvert en mode ANSI. `fputc` ne prend actuellement pas en charge la sortie vers un flux UNICODE.  
  
 Les versions avec le suffixe `_nolock` sont identiques, à ceci près qu’elles ne sont pas protégées contre les interférences par d’autres threads. Pour plus d’informations, consultez [_fputc_nolock, _fputwc_nolock](../../c-runtime-library/reference/fputc-nolock-fputwc-nolock.md).  
  
 Voici une série de notes spécifiques aux routines.  
  
|Routine|Notes|  
|-------------|-------------|  
|`fputc`|Équivalente à `putc`, mais implémentée uniquement comme une fonction, plutôt que comme une fonction et une macro.|  
|`fputwc`|Version à caractères larges de `fputc`. Écrit `c` comme un caractère multioctet ou large selon que `stream` est ouvert en mode texte ou binaire.|  
  
### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique  
  
|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_fputtc`|`fputc`|`fputc`|`fputwc`|  
  
## <a name="requirements"></a>Configuration requise  
  
|Fonction|En-tête requis|  
|--------------|---------------------|  
|`fputc`|\<stdio.h>|  
|`fputwc`|\<stdio.h> ou \<wchar.h>|  
  
 La console n’est pas pris en charge dans les applications de plateforme Windows universelle (UWP). Les descripteurs de flux standard qui sont associés à la console :`stdin`, `stdout`, et `stderr`, doivent être redirigés avant que les fonctions d’exécution C de les utiliser dans les applications UWP. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Exemple  
  
```  
// crt_fputc.c  
// This program uses fputc  
// to send a character array to stdout.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char strptr1[] = "This is a test of fputc!!\n";  
   char *p;  
  
   // Print line to stream using fputc.   
   p = strptr1;  
   while( (*p != '\0') && fputc( *(p++), stdout ) != EOF ) ;  
  
}  
```  
  
```Output  
This is a test of fputc!!  
```  
  
## <a name="see-also"></a>Voir aussi  
 [E/S de flux](../../c-runtime-library/stream-i-o.md)   
 [fgetc, fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [putc, putwc](../../c-runtime-library/reference/putc-putwc.md)