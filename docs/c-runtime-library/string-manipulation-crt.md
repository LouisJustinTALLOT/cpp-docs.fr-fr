---
title: Manipulation de chaînes (CRT)
ms.date: 11/04/2016
f1_keywords:
- c.strings
helpviewer_keywords:
- strings [C++], manipulating
- string manipulation
- manipulating strings
ms.assetid: 6545861a-59e7-408d-9d29-2ec9134fc91a
ms.openlocfilehash: 4e172cba7128655b43fba10163284a10a1a9f710
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51329577"
---
# <a name="string-manipulation-crt"></a>Manipulation de chaînes (CRT)

Ces routines fonctionnent sur les chaînes de caractères à un octet terminée par le caractère null, les chaînes de caractères larges et les chaînes de caractères multioctets. Utilisez les routines de manipulation de mémoire tampon, décrites dans [Manipulation de la mémoire tampon](../c-runtime-library/buffer-manipulation.md), pour utiliser des tableaux de caractères qui ne se terminent pas par un caractère null.

## <a name="string-manipulation-routines"></a>Routines de manipulation de chaînes

|Routine|Utilisez|
|-------------|---------|
|[strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md), [_stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md), [_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md), [_strnicoll, _wcsnicoll, _mbsnicoll, _strnicoll_l, _wcsnicoll_l, _mbsnicoll_l](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|Comparer deux chaînes de caractères à l’aide des informations de page de codes (**_mbsicoll** et **_mbsnicoll** ne respectent pas la casse)|
|[_strdec, _wcsdec, _mbsdec, _mbsdec_l](../c-runtime-library/reference/strdec-wcsdec-mbsdec-mbsdec-l.md)|Déplacer un pointeur de chaîne d’un caractère vers l’arrière|
|[_strinc, _wcsinc, _mbsinc, _mbsinc_l](../c-runtime-library/reference/strinc-wcsinc-mbsinc-mbsinc-l.md)|Avancer un pointeur de chaîne d’un caractère|
|[_mbsnbcat, _mbsnbcat_l](../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md), [_mbsnbcat_s, _mbsnbcat_s_l](../c-runtime-library/reference/mbsnbcat-s-mbsnbcat-s-l.md)|Ajouter les *n* premiers octets, au maximum, d’une chaîne de caractères à une autre|
|[_mbsnbcmp, _mbsnbcmp_l](../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)|Comparer les *n* premiers octets de deux chaînes de caractères|
|[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](../c-runtime-library/reference/strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)|Retourner le nombre d’octets de caractère du nombre de caractères fourni|
|[_mbsnbcpy, _mbsnbcpy_l](../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md), [_mbsnbcpy_s, _mbsnbcpy_s_l](../c-runtime-library/reference/mbsnbcpy-s-mbsnbcpy-s-l.md)|Copier *n* octets de chaîne|
|[_mbsnbicmp, _mbsnbicmp_l](../c-runtime-library/reference/mbsnbicmp-mbsnbicmp-l.md)|Comparer *n* octets de deux chaînes de caractères en ignorant la casse|
|[_mbsnbset, _mbsnbset_l](../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)|Définir les *n* premiers octets d’une chaîne de caractères sur un caractère spécifié|
|[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](../c-runtime-library/reference/strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)|Retourner le nombre de caractères du nombre d’octets fourni|
|[_strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l](../c-runtime-library/reference/strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)|Rechercher le caractère suivant dans la chaîne|
|[_strninc, _wcsninc, _mbsninc, _mbsninc_l](../c-runtime-library/reference/strninc-wcsninc-mbsninc-mbsninc-l.md)|Avancer un pointeur de chaîne de *n* caractères|
|[_strspnp, _wcsspnp, _mbsspnp, _mbsspnp_l](../c-runtime-library/reference/strspnp-wcsspnp-mbsspnp-mbsspnp-l.md)|Retourner un pointeur vers le premier caractère dans une chaîne donnée qui ne se trouve pas dans une autre chaîne donnée|
|[_scprintf, _scprintf_l, _scwprintf, _scwprintf_l](../c-runtime-library/reference/scprintf-scprintf-l-scwprintf-scwprintf-l.md)|Retourner le nombre de caractères d’une chaîne mise en forme|
|[_snscanf, _snscanf_l, _snwscanf, _snwscanf_l](../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md), [_snscanf_s, _snscanf_s_l, _snwscanf_s, _snwscanf_s_l](../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)|Lire les données mises en forme d'une longueur spécifiée dans le flux d'entrée standard|
|[sscanf, _sscanf_l, swscanf, _swscanf_l](../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md), [sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)|Lire les données mises en forme d'une longueur spécifiée dans le flux d'entrée standard|
|[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md), [_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|Écrire des données mises en forme dans une chaîne|
|[strcat, wcscat, _mbscat](../c-runtime-library/reference/strcat-wcscat-mbscat.md), [strcat_s, wcscat_s, _mbscat_s](../c-runtime-library/reference/strcat-s-wcscat-s-mbscat-s.md)|Ajouter une chaîne à une autre|
|[strchr, wcschr, _mbschr, _mbschr_l](../c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l.md)|Rechercher la première occurrence du caractère spécifié dans la chaîne|
|[strcmp, wcscmp, _mbscmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)|Comparer deux chaînes|
|[strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md), [_stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md), [_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md), [_strnicoll, _wcsnicoll, _mbsnicoll, _strnicoll_l, _wcsnicoll_l, _mbsnicoll_l](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|Comparer deux chaînes à l’aide des informations de page de codes des paramètres régionaux actuels (**_stricoll**, **_wcsicoll**, **_strnicoll** et **_wcsnicoll** ne respectent pas la casse)|
|[strcpy, wcscpy, _mbscpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md), [strcpy_s, wcscpy_s, _mbscpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)|Copier une chaîne dans une autre|
|[strcspn, wcscspn, _mbscspn, _mbscspn_l](../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)|Rechercher la première occurrence d’un caractère du jeu de caractères spécifié dans la chaîne|
|[_strdup, _wcsdup, _mbsdup](../c-runtime-library/reference/strdup-wcsdup-mbsdup.md), [_strdup_dbg, _wcsdup_dbg](../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md)|Dupliquer la chaîne|
|[strerror, _strerror, _wcserror, \__wcserror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md), [strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)|Mapper le numéro d’erreur à la chaîne du message|
|[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|Mettre en forme la chaîne de date et d’heure|
|[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)|Comparer deux chaînes sans tenir compte de la casse|
|[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md), [strnlen, strnlen_s, wcsnlen, wcsnlen_s, _mbsnlen, _mbsnlen_l, _mbstrnlen, _mbstrnlen_l](../c-runtime-library/reference/strnlen-strnlen-s.md)|Rechercher la longueur de la chaîne|
|[_strlwr, _wcslwr, _mbslwr, _strlwr_l, _wcslwr_l, _mbslwr_l](../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md), [_strlwr_s, _strlwr_s_l, _mbslwr_s, _mbslwr_s_l, _wcslwr_s, _wcslwr_s_l](../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)|Convertir une chaîne en minuscules|
|[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md), [strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)|Ajouter des caractères de chaîne|
|[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|Comparer les caractères de deux chaînes|
|[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md), [strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)|Copier les caractères d'une chaîne vers une autre|
|[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)|Comparer les caractères de deux chaînes sans tenir compte de la casse|
|[_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l](../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)|Définir les *n* premiers caractères d’une chaîne sur un caractère spécifié|
|[strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l](../c-runtime-library/reference/strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)|Rechercher la première occurrence d’un caractère d’une chaîne dans une autre chaîne|
|[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)|Rechercher la dernière occurrence d’un caractère donné dans la chaîne|
|[_strrev, _wcsrev, _mbsrev, _mbsrev_l](../c-runtime-library/reference/strrev-wcsrev-mbsrev-mbsrev-l.md)|Inverser la chaîne|
|[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|Définir tous les caractères d’une chaîne sur le caractère spécifié|
|[strspn, wcsspn, _mbsspn, _mbsspn_l](../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)|Rechercher dans une chaîne la première occurrence d’un caractère introuvable dans une autre chaîne|
|[strstr, wcsstr, _mbsstr, _mbsstr_l](../c-runtime-library/reference/strstr-wcsstr-mbsstr-mbsstr-l.md)|Rechercher la première occurrence de la chaîne spécifiée dans une autre chaîne|
|[strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l](../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md), [strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)|Rechercher le jeton suivant dans la chaîne|
|[_strupr, _strupr_l, _mbsupr, _mbsupr_l, _wcsupr_l, _wcsupr](../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md), [_strupr_s, _strupr_s_l, _mbsupr_s, _mbsupr_s_l, _wcsupr_s, _wcsupr_s_l](../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)|Convertir une chaîne en majuscules|
|[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|Classer une chaîne en fonction des informations spécifiques des paramètres régionaux|
|[vsprintf, _vsprintf_l, vswprintf, _vswprintf_l, \__vswprintf_l](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md), [vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md), [_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|Écrire la sortie mise en forme en utilisant un pointeur désignant une liste d'arguments|
|[vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md), [vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)|Écrire la sortie mise en forme en utilisant un pointeur désignant une liste d'arguments|

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
