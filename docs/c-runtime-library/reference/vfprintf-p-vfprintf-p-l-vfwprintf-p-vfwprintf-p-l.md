---
title: _vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _vfprintf_p
- _vfwprintf_p
- _vfprintf_p_l
- _vfwprintf_p_l
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
apitype: DLLExport
f1_keywords:
- _vfwprintf_p_l
- _vfprintf_p
- vfwprintf_p_l
- vfwprintf_p
- vfprintf_p_l
- _vfwprintf_p
- _vftprintf_p
- _vfprintf_p_l
- vfprintf_p
dev_langs:
- C++
helpviewer_keywords:
- vfprintf_p_l function
- _vftprintf_p_l function
- _vfprintf_p function
- vfprintf_p function
- vftprintf_p_l function
- _vfprintf_p_l function
- _vftprintf_p function
- _vfwprintf_p_l function
- vfwprintf_p_l function
- _vfwprintf_p function
- vftprintf_p function
- formatted text [C++]
- vfwprintf_p function
ms.assetid: 4d4a0914-4175-4b65-9ca1-037c4ef29147
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bdbb916ef756d3437c8d4df1af725fc49fdfff6d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="vfprintfp-vfprintfpl-vfwprintfp-vfwprintfpl"></a>_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l
Écrivent la sortie mise en forme en utilisant un pointeur désignant une liste d’arguments, avec la possibilité de spécifier l’ordre dans lequel les arguments sont utilisés dans la chaîne de format.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _vfprintf_p(  
   FILE *stream,  
   const char *format,  
   va_list argptr   
);  
int _vfprintf_p_l(  
   FILE *stream,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int _vfwprintf_p(  
   FILE *stream,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vfwprintf_p_l(  
   FILE *stream,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `stream`  
 Pointeur vers la structure `FILE` .  
  
 `format`  
 Spécification de format.  
  
 `argptr`  
 Pointeur vers la liste d'arguments.  
  
 `locale`  
 Paramètres régionaux à utiliser.  
  
 Pour plus d'informations, consultez [Spécifications de format](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## <a name="return-value"></a>Valeur de retour  
 `_vfprintf_p` et `_vfwprintf_p` retournent le nombre de caractères écrits, sans le caractère Null de fin, ou une valeur négative si une erreur de sortie se produit.  
  
## <a name="remarks"></a>Notes  
 Chacune de ces fonctions prend un pointeur désignant une liste d’arguments, puis met en forme et écrit les données fournies dans `stream`. Ces fonctions se distinguent des versions `_vfprint_s` et `_vfwprint_s` uniquement par le fait qu’elles prennent en charge les paramètres positionnels. Pour plus d’informations, consultez [Paramètres positionnels printf_p](../../c-runtime-library/printf-p-positional-parameters.md).  
  
 `_vfwprintf_p` est la version à caractères larges de `_vprintf_p` ; les deux fonctions se comportent de la même manière si le flux est ouvert en mode ANSI. `_vprintf_p` ne prend pas en charge la sortie vers un flux UNICODE pour l’instant.  
  
 Les versions de ces fonctions avec le suffixe `_l` sont identiques, sauf qu'elles utilisent les paramètres régionaux passés au lieu des paramètres régionaux du thread actuel.  
  
> [!IMPORTANT]
>  Assurez-vous que `format` n'est pas une chaîne définie par l'utilisateur. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
 Si `stream` ou `format` est un pointeur Null ou si la chaîne de format contient des caractères de mise en forme non valides, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l'exécution est autorisée à se poursuivre, ces fonctions retournent -1 et définissent `errno` avec la valeur `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique  
  
|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vftprintf_p`|`_vfprintf_p`|`_vfprintf_p`|`_vfwprintf_p`|  
|`_vftprintf_p_l`|`_vfprintf_p_l`|`_vfprintf_p_l`|`_vfwprintf_p_l`|  
  
## <a name="requirements"></a>Configuration requise  
  
|Routine|En-tête requis|En-têtes facultatifs|  
|-------------|---------------------|----------------------|  
|`_vfprintf_p`, `_vfprintf_p_l`|\<stdio.h> et \<stdarg.h>|\<varargs.h>*|  
|`_vfwprintf_p`, `_vfwprintf_p_l`|\<stdio.h> ou \<wchar.h> et \<stdarg.h>|\<varargs.h>*|  
  
 \** Nécessaire pour la compatibilité avec UNIX V.  
  
 Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md) dans l'introduction.  
  
## <a name="see-also"></a>Voir aussi  
 [E/S de flux](../../c-runtime-library/stream-i-o.md)   
 [vprintf, fonctions](../../c-runtime-library/vprintf-functions.md)   
 [fprintf, _fprintf_l, fwprintf, _fwprintf_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, _printf_l, wprintf, _wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va_arg, va_copy, va_end, va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)   
 [Paramètres positionnels printf_p](../../c-runtime-library/printf-p-positional-parameters.md)   
 [_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l](../../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)   
 [_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l](../../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)   
 [_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l](../../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)