---
title: Types standard
ms.date: 11/04/2016
f1_keywords:
- __time64_t
- _diskfree_t
- _CRT_DUMP_CLIENT
- _fsize_t
- __timeb64
- File
- __utimeb64
- jmp_buf
- __finddata64_t
- _wfinddata_t
- _finddata_t
- utimbuf64
- wint_t
- wctrans_t
- wctype_t
- _HFILE
- _secerr_handler_func
- clock_t
- fpos_t
- _dev_t
- time64_t
- wfinddata64_t
- stat64
- ldiv_t
- _EXCEPTION_POINTERS
- terminate_function
- size_t
- timeb64
- tm
- _HEAPINFO
- unexpected_function
- _CrtMemState
- _se_translator_function
- sig_atomic_t
- _CRT_REPORT_HOOK
- _complex
- _w_finddatai64_t
- _timeb
- _onexit_t
- _RTC_ErrorNumber
- lconv
- _PNH
- _off_t
- ptrdiff_t
- time_t
- _FPIEEE_RECORD
- _exception
- __w_finddata64_t
- __stat64
- _utimbuf
- __utimbuf64
- div_t
- _CRT_ALLOC_HOOK
- int8_t
- uint8_t
- int16_t
- uint16_t
- int32_t
- uint32_t
- int64_t
- int_least8_t
- uint_least8_t
- int_least16_t
- uint_least16_t
- int_least32_t
- uint_least32_t
- int_least64_t
- uint_least64_t
- int_fast8_t
- uint_fast8_t
- int_fast16_t
- uint_fast16_t
- int_fast32_t
- uint_fast32_t
- int_fast64_t
- uint_fast64_t
- intmax_t
- uintmax_t
helpviewer_keywords:
- __timeb64 type
- tm type
- clock_t type
- intptr_t type
- diskfree_t type
- wctype_t type
- CRT_DUMP_CLIENT type
- sig_atomic_t type
- _PNH type
- time_t type
- wfinddata_t type
- timeb64
- CRT, standard types
- wint_t type
- _RTC_ErrorNumber type
- _diskfree_t type
- _dev_t type
- _wfinddata_t type
- HFILE type
- __utimbuf64 type
- div_t type
- _onexit_t type
- _secerr_handler_func type
- FPIEEE_RECORD type
- HEAPINFO type
- PNH type
- _CRT_ALLOC_HOOK type
- _se_translater_function type
- va_list type
- wctrans_t type
- secerr_handler_func type
- _locale_t type
- timeb type
- lconv type
- utimbuf type
- dev_t type
- unexpected_function typedef
- _complex type
- _off_t type
- off_t type
- RTC_ErrorNumber type
- _FPIEEE_RECORD type
- exception type
- _CRT_REPORT_HOOK type
- _HEAPINFO type
- ldiv_t type
- terminate_function type
- uintptr_t type
- _CRT_DUMP_CLIENT type
- _utimbuf type
- wfinddatai64_t type
- fpos_t type
- wchar_t type
- CRT_ALLOC_HOOK type
- _HFILE type
- __time64_t type
- _timeb type
- CrtMemState type
- __finddata64_t type
- _exception type
- stat type
- onexit_t type
- FILE constant
- _stat type
- finddata_t type
- __wfinddata64_t type
- ptrdiff_t type
- complex types
- _wfinddatai64_t type
- _EXCEPTION_POINTERS type
- jmp_buf type
- se_translater_function type
- size_t type
- EXCEPTION_POINTERS type
- __stat64 type
- _fsize_t type
- CRT_REPORT_HOOK type
- _finddata_t type
ms.assetid: 23312dd2-4a6a-4d70-9b48-2a5d0d8c9f28
ms.openlocfilehash: 38906579a449941d6dad767afa97a32d63fe3445
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231271"
---
# <a name="standard-types"></a>Types standard

La bibliothèque Runtime Microsoft définit les types et typedefs standard suivants.

### <a name="fixed-width-integral-types-stdinth"></a>Types intégraux de largeur fixe (stdint.h)

|Nom|Type intégré équivalent|
|----------|-------------------------------|
|int8\_t, uint8\_t|signed char, unsigned char|
|int16\_t, uint16\_t|short, unsigned short|
|int32\_t, uint32\_t|int, unsigned int|
|int64\_t, uint64\_t|long long, unsigned long long|
|int_least8_t, uint_least8_t|signed char, unsigned char|
|int_least16_t, uint_least16_t|short, unsigned short|
|int_least32_t, uint_least32_t|int, unsigned int|
|int_least64_t, uint_least64_t|long long, unsigned long long|
|int_fast8_t, uint_fast8_t|signed char, unsigned char|
|int_fast16_t, uint_fast16_t|int, unsigned int|
|int_fast32_t, uint_fast32_t|int, unsigned int|
|int_fast64_t, uint_fast64_t|long long, unsigned long long|
|intmax_t, uintmax_t|long long, unsigned long long|

|Type|Description|Déclaré dans|
|----------|-----------------|-----------------|
|`clock_t` (long)|Stocke les valeurs d'heure ; utilisé par [l'horloge](../c-runtime-library/reference/clock.md).|TIME.H|
|Structure `_complex`|Stocke les parties réels et imaginaires des nombres complexes ; utilisé par [_cabs](../c-runtime-library/reference/cabs.md).|MATH.H|
|`_CRT_ALLOC_HOOK`|Définition de type pour la nouvelle fonction de raccordement définie par l'utilisateur. Utilisé dans [_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md).|CRTDBG.H|
|`_CRT_DUMP_CLIENT`,<br /><br /> `_CRT_DUMP_CLIENT_M`|Une définition de type pour une fonction de rappel qui sera appelée dans [_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md).|CRTDBG.H|
|Structure `_CrtMemState`|Fournit des informations sur l'état actuel du tas de débogage de la bibliothèque Runtime C.|CRTDBG.H|
|`_CRT_REPORT_HOOK`,<br /><br /> `_CRT_REPORT_HOOKW`,<br /><br /> `_CRT_REPORT_HOOKW_M`|Une définition de type pour une fonction de rappel qui sera appelée dans [_CrtDbgReport](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).<br /><br /> Les paramètres de cette fonction sont : le type de rapport, le message de sortie et la valeur de retour de la fonction de rappel.|CRTDBG.H|
|`dev_t`, `_dev_t` entier court ou entier non signé|Représente les handles du périphérique.|SYS\TYPES.H|
|Structure `_diskfree_t`|Contient des informations à propos d'un lecteur de disque. Utilisé par [_getdiskfree](../c-runtime-library/reference/getdiskfree.md)**.**|DOS.H et DIRECT.H|
|Structures `div_t`, `ldiv_t` et `lldiv_t`|Stockent les valeurs retournées par [div](../c-runtime-library/reference/div.md), [ldiv](../c-runtime-library/reference/ldiv-lldiv.md) et [lldiv](../c-runtime-library/reference/ldiv-lldiv.md), respectivement.|STDLIB.H|
|Entier `errno_t`|Utilisé pour un type de résultat ou un paramètre de fonction qui traite les codes d'erreur de `errno`.|STDDEF.H,<br /><br /> CRTDEFS.H|
|Structure `_exception`|Stocke les informations sur l'erreur pour [_matherr](../c-runtime-library/reference/matherr.md).|MATH.H|
|`_EXCEPTION_POINTERS`|Contient un enregistrement d'exception. Pour plus d'informations, consultez [EXCEPTION_POINTERS](/windows/win32/api/winnt/ns-winnt-exception_pointers).|FPIEEE.H|
|Structure `FILE`|Stocke les informations sur l'état actuel du flux ; utilisé dans toutes les opérations d'E/S de flux.|STDIO.H|
|Structures `_finddata_t`, `_wfinddata_t`, `_finddata32_t`, `_wfinddata32_t`, `_finddatai64_t`, `_wfinddatai64_t`, `__finddata64_t`, `__wfinddata64_t`, `__finddata32i64_t`, `__wfinddata32i64_t`, `__finddata64i32_t`, `__wfinddata64i32_t`|Stockent les informations d'attribut de fichier retournées par [_findfirst, _wfindfirst, and related functions](../c-runtime-library/reference/findfirst-functions.md) and [_findnext, _wfindnext et les fonctions liées](../c-runtime-library/reference/findnext-functions.md). Pour plus d'informations sur les membres de structures, consultez [Fonctions _find, _wfind](../c-runtime-library/filename-search-functions.md).|IO.H, WCHAR.H|
|Structure `_FPIEEE_RECORD`|Contient des informations concernant l'exception à virgule flottante IEEE ; passé au gestionnaire d'interruptions défini par l'utilisateur par [_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md).|FPIEEE.H|
|`fpos_t`(entier long, **`__int64`** , ou structure, selon la plateforme cible)|Utilisé par [fgetpos](../c-runtime-library/reference/fgetpos.md) et [fsetpos](../c-runtime-library/reference/fsetpos.md) pour enregistrer des informations afin de spécifier de manière unique chaque position dans un fichier.|STDIO.H|
|`_fsize_t` (entier long non signé)|Utilisé pour représenter la taille d'un fichier.|IO.H,<br /><br /> WCHAR.H|
|Structure `_HEAPINFO`|Contient des informations sur l'entrée suivante du tas pour [_heapwalk](../c-runtime-library/reference/heapwalk.md).|MALLOC.H|
|`_HFILE` (void \*)|Handle de fichiers du système d'exploitation.|CRTDBG.H|
|`imaxdiv_t`|Type de valeur retournée par la fonction [imaxdiv](../c-runtime-library/reference/imaxdiv.md), contenant le quotient et le reste.|inttypes.h|
|`ino_t`, `_ino_t` (court non signé)|Pour retourner les informations d'état.|WCHAR.H|
|`intmax_t`|Un type d'entier signé capable de représenter toute valeur d'un type d'entier signé.|stdint.h|
|`intptr_t`(entier long ou **`__int64`** , selon la plateforme cible)|Stocke un pointeur (ou le HANDLE) sur des plateformes Win32 et Win64.|STDDEF.H et d'autres fichiers Include|
|`jmp_buf` tableau|Utilisé par [setjmp](../c-runtime-library/reference/setjmp.md) et [longjmp](../c-runtime-library/reference/longjmp.md) pour enregistrer et restaurer l'environnement de programme.|SETJMP.H|
|Structure `lconv`|Contient des règles de mise en forme des valeurs numériques dans plusieurs pays ou régions. Utilisé par [localeconv](../c-runtime-library/reference/localeconv.md).|LOCALE.H|
|`_LDOUBLE`,<br /><br /> `_LONGDOUBLE`,<br /><br /> `_LDBL12` (long double ou tableau de caractères non signé)|Utilisé pour représenter une valeur longue double.|STDLIB.H|
|Structure `_locale_t`|Stocke les valeurs actuelles de paramètres régionaux ; utilisé dans toutes les bibliothèques spécifiques du moteur d'exécution C de paramètres régionaux.|CRTDEFS.H|
|`mbstate_t`|Suit l'état d'une conversion en caractères multioctets.|WCHAR.H|
|Entier long `off_t`, `_off_t`|Représente la valeur d'offset du fichier .|WCHAR.H, SYS\TYPES.H|
|`_onexit_t`,<br /><br /> Pointeur `_onexit_m_t`|Retourné par [_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md).|STDLIB.H|
|Pointeur de fonction `_PNH`|Type d’argument pour [_set_new_handler](../c-runtime-library/reference/set-new-handler.md).|NEW.H|
|`ptrdiff_t`(entier long ou **`__int64`** , selon la plateforme cible)|Résultat de la soustraction de deux pointeurs.|CRTDEFS.H|
|`_purecall_handler`,<br /><br /> `_purecall_handler_m`|Une définition de type pour une fonction de rappel qui est appelée lorsqu'une fonction virtuelle pure est appelée. Utilisé par [_get_purecall_handler, _set_purecall_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md). Une fonction `_purecall_handler` doit avoir un type de retour void.|STDLIB.H|
|Définition de type `_RTC_error_fn`|Une définition de type pour une fonction qui gérera les vérifications des erreurs d'exécution. Utilisé dans [_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md).|RTCAPI.H|
|Définition de type `_RTC_error_fnW`|Une définition de type pour une fonction qui gérera les vérifications des erreurs d'exécution. Utilisé dans [_RTC_SetErrorFuncW](../c-runtime-library/reference/rtc-seterrorfuncw.md).|RTCAPI.H|
|Énumération `_RTC_ErrorNumber`|Définit les conditions d'erreur pour [_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md) et [_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md).|RTCAPI.H|
|`_se_translator_function`|Une définition de type pour une fonction de rappel qui traduit une exception. Le premier paramètre est le code de l'exception et le deuxième paramètre est l'enregistrement de l'exception. Utilisé par [_set_se_translator](../c-runtime-library/reference/set-se-translator.md).|EH.H|
|Entier `sig_atomic_t`|Type d'objet qui peut être modifié en tant qu'entité atomique, même en présence d'interruptions asynchrones ; utilisé avec [signal](../c-runtime-library/reference/signal.md).|SIGNAL.H|
|`size_t` (unsigned__int64 non signé ou entier non signé, selon la plateforme cible)|Résultat de l' **`sizeof`** opérateur.|CRTDEFS.H et d'autres fichiers Include|
|Structure `_stat`|Contient les informations sur l'état des fichiers retournées par [_stat](../c-runtime-library/reference/stat-functions.md) et [_fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md).|SYS\STAT.H|
|Structure `__stat64`|Contient les informations sur l'état des fichiers retournées par [_fstat64](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md) et [_stat64](../c-runtime-library/reference/stat-functions.md) et [_wstat64](../c-runtime-library/reference/stat-functions.md).|SYS\STAT.H|
|Structure `_stati64`|Contient les informations sur l'état des fichiers retournées par [_fstati64](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md), [_stati64](../c-runtime-library/reference/stat-functions.md), et [_wstati64](../c-runtime-library/reference/stat-functions.md).|SYS\STAT.H|
|Définition de type `terminate_function`|Une définition de type pour une fonction de rappel qui est appelée lorsque [terminer](../c-runtime-library/reference/terminate-crt.md) est appelé. Utilisé par [set_terminate](../c-runtime-library/reference/set-terminate-crt.md).|EH.H|
|`time_t` (__int64 ou entier long)|Représente les valeurs d’heure dans [mktime](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [time](../c-runtime-library/reference/time-time32-time64.md), [ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md), [ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) et [gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md). Nombre de secondes depuis le 1er janvier 1970, 0h00 UTC. Si _USE_32BIT_TIME_T est défini, `time_t` est un entier long. S'il n'est pas défini, c'est un entier 64 bits.|TIME.H,<br /><br /> SYS\STAT.H,<br /><br /> SYS\TIMEB.H|
|`__time32_t` (entier long)|Représente les valeurs d’heure dans [mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md), [gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) et [localtime, _localtime32, _localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md).|CRTDEFS.H, SYS\STAT.H,<br /><br /> SYS\TIMEB.H|
|`__time64_t` (**`__int64`**)|Représente les valeurs d’heure dans [mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [_ctime64, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md), [_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md) et [_time64](../c-runtime-library/reference/time-time32-time64.md).|TIME.H,<br /><br /> SYS\STAT.H,<br /><br /> SYS\TIMEB.H|
|Structure `_timeb`|Utilisé par [_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md) et [_ftime_s, _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) pour stocker l'heure système actuelle.|SYS\TIMEB.H|
|Structure `__timeb32`|Utilisé par [_ftime, _ftime32, _ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md) et [_ftime_s, _ftime64_s, _ftime32_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) pour stocker l'heure système actuelle.|SYS\TIMEB.H|
|Structure `__timeb64`|Utilisé par [_ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md) et [_ftime_s, _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) pour stocker l'heure système actuelle.|SYS\TIMEB.H|
|Structure `tm`|Utilisé par [asctime, _wasctime](../c-runtime-library/reference/asctime-wasctime.md), [asctime_s, _wasctime_s](../c-runtime-library/reference/asctime-s-wasctime-s.md), [gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [gmtime_s, _gmtime32_s, _gmtime64_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md), [localtime, _localtime32, _localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md), [localtime_s, _localtime32_s, _localtime64_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), [mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md) et [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour stocker et récupérer les informations d'heure.|TIME.H|
|`uintmax_t`|Un type d'entier non signé capable de représenter toute valeur d'un type d'entier non signé.|stdint.h|
|`uintptr_t`(entier long ou **`__int64`** , selon la plateforme cible)|Entier non signé ou une version unsigned__int64 de `intptr_t`.|STDDEF.H et d'autres fichiers Include|
|`unexpected_function`|Une définition de type pour une fonction de rappel qui est appelée lorsque [inattendue](../c-runtime-library/reference/unexpected-crt.md) est appelé. Utilisé par [set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md).|EH.H|
|Structure `_utimbuf`|Stocke les heures d'accès et de modification des fichiers utilisées par [_utime, _wutime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) et [_futime, _futime32, _futime64](../c-runtime-library/reference/futime-futime32-futime64.md) pour modifier les dates de modification des fichiers.|SYS\UTIME.H|
|Structure `_utimbuf32`|Stocke les heures d'accès et de modification des fichiers utilisées par [_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) et [_futime, _utime32, _utime64](../c-runtime-library/reference/futime-futime32-futime64.md) pour modifier les dates de modification des fichiers.|SYS\UTIME.H|
|Structure `__utimbuf64`|Utilisé par [_utime64, _wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) et [_futime64](../c-runtime-library/reference/futime-futime32-futime64.md) pour stocker l'heure actuelle.|SYS\UTIME.H|
|Structure `va_list`|Utilisé pour stocker les informations requises par [va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) et des macros de [va_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md). La fonction appelée déclare la variable de type `va_list` qui peut être passée comme argument pour une autre fonction.|STDARG.H,<br /><br /> CRTDEFS.H|
|**`wchar_t`** caractère élargi|Pratique pour écrire vos programmes portables destinés aux marchés internationaux.|STDDEF.H, STDLIB.H,<br /><br /> CRTDEFS.H,<br /><br /> SYS\STAT.H|
|Entier `wctrans_t`|Représente les mappages de caractères spécifiques aux paramètres régionaux.|WCTYPE.H|
|Entier `wctype_t`|Peut représenter tous les caractères de n'importe quel jeu de caractères de langue.|WCHAR.H,<br /><br /> CRTDEFS.H|
|Entier `wint_t`|Objet de type de données qui peut contenir n'importe quel valeur de caractère large ou de fin de fichier large.|WCHAR.H,<br /><br /> CRTDEFS.H|

## <a name="see-also"></a>Voir aussi

[Référence de la bibliothèque Runtime C](../c-runtime-library/c-run-time-library-reference.md)
