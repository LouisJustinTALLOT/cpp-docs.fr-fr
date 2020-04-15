---
title: _strdate_s, _wstrdate_s
description: _strdate_s et _wstrdate_s sont des versions CRT sécurisées des fonctions _strdate et _wstrdate qui placent la date actuelle dans un tampon.
ms.date: 4/2/2020
api_name:
- _strdate_s
- _wstrdate_s
- _o__strdate_s
- _o__wstrdate_s
api_location:
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _strdate_s
- wstrdate_s
- _wstrdate_s
- strdate_s
- _tstrdate_s
helpviewer_keywords:
- dates, copying
- tstrdate_s function
- wstrdate_s function
- _tstrdate_s function
- strdate_s function
- copying dates
- _strdate_s function
- _wstrdate_s function
ms.assetid: d41d8ea9-e5ce-40d4-864e-1ac29b455991
ms.openlocfilehash: b4d977ba3546eae17218c63b1786fd26c784d340
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359819"
---
# <a name="_strdate_s-_wstrdate_s"></a>_strdate_s, _wstrdate_s

Copient la date système actuelle dans une mémoire tampon. Ces fonctions sont des versions de [_strdate, _wstrdate](strdate-wstrdate.md) avec des améliorations de sécurité comme décrit dans [les caractéristiques de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _strdate_s(
   char *buffer,
   size_t size
);
errno_t _wstrdate_s(
   wchar_t *buffer,
   size_t size
);
template <size_t size>
errno_t _strdate_s(
   char (&buffer)[size]
); // C++ only
template <size_t size>
errno_t _wstrdate_s(
   wchar_t (&buffer)[size]
); // C++ only
```

### <a name="parameters"></a>Paramètres

*Tampon*\
Un pointeur à un tampon pour mettre la chaîne de date formatée.

*Taille*\
Taille du tampon dans les unités de caractère.

## <a name="return-value"></a>Valeur retournée

Zéro si l’opération réussit. La valeur de retour est un code d’erreur s’il y a un échec. Les codes d’erreur sont définis dans ERRNO.H. Consultez le tableau ci-dessous pour en savoir plus sur les erreurs générées exactement par cette fonction. Pour plus d’informations sur les codes d’erreur, consultez [errno](../../c-runtime-library/errno-constants.md).

## <a name="error-conditions"></a>Conditions d’erreur

|*buffer*|*Taille*|Renvoie|Contenu du *tampon*|
|--------------|------------------------|------------|--------------------------|
|**Null**|(indifférent)|**EINVAL (EN)**|Non modifiée|
|Non **NULL** (pointant vers le tampon valide)|0|**EINVAL (EN)**|Non modifiée|
|Non **NULL** (pointant vers le tampon valide)|0 taille < *<* 9|**EINVAL (EN)**|Chaîne vide|
|Non **NULL** (pointant vers le tampon valide)|*taille* >9|0|Date actuelle au format spécifié dans la section Notes|

## <a name="security-issues"></a>Problèmes de sécurité

Le passage d’une valeur non valide et non-NULL pour *le tampon* entraîne une violation de l’accès si le paramètre *de taille* est supérieur à neuf.

Passer une valeur pour *une taille* supérieure à la taille réelle du *tampon* entraîne un dépassement de mémoire tampon.

## <a name="remarks"></a>Notes

Ces fonctions fournissent des versions plus sécurisées de **_strdate** et **_wstrdate**. La fonction **_strdate_s** copie la date actuelle du système à la mémoire tampon indiquée par *tampon*. Il `mm/dd/yy`est formaté `mm` , où est `dd` le mois à deux `yy` chiffres, est le jour à deux chiffres, et est les deux derniers chiffres de l’année. Par exemple, la chaîne `12/05/99` représente le 5 décembre 1999. Le tampon doit être d’au moins neuf caractères de long.

**_wstrdate_s** est une version à caractère large de **_strdate_s**; l’argument et la valeur de retour de **_wstrdate_s** sont des chaînes de caractère large. Ces fonctions se comportent sinon de façon identique.

Lorsque *le tampon* est un pointeur **NULL,** ou la *taille* est inférieure à neuf caractères, le gestionnaire de paramètres invalide est invoqué. Il est décrit dans [La validation des paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions renvoient -1. Ils ont mis **errno** à **EINVAL** si le tampon est **NULL** ou si la *taille* est inférieure ou égale à 0. Ou, ils ont mis **errno** à **ERANGE** si *la taille* est inférieure à 9.

Dans le C, l’utilisation de ces fonctions est simplifiée par des surcharges de modèles. Les surcharges peuvent déduire automatiquement la longueur du tampon, ce qui élimine la nécessité de spécifier un argument *de taille.* De plus, ils peuvent remplacer automatiquement les fonctions non sécurisées par leurs homologues plus récents et plus sûrs. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Les versions de bibliothèque de débogé de ces fonctions remplissent d’abord le tampon avec 0xFE. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Cartographie de routine de texte générique :

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate_s**|**_strdate_s**|**_strdate_s**|**_wstrdate_s**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_strdate**|\<time.h>|
|**_wstrdate**|\<time.h> ou \<wchar.h>|
|**_strdate_s**|\<time.h>|

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [time](time-time32-time64.md).

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)\
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)\
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)\
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)\
[temps, _time32, _time64](time-time32-time64.md)\
[_tzset](tzset.md)
