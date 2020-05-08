---
title: _strdate_s, _wstrdate_s
description: _strdate_s et _wstrdate_s sont des versions CRT sécurisées des fonctions _strdate et _wstrdate qui placent la date actuelle dans une mémoire tampon.
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 7fe8d682ab515d5a11e90f0c26e956725644806e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916916"
---
# <a name="_strdate_s-_wstrdate_s"></a>_strdate_s, _wstrdate_s

Copient la date système actuelle dans une mémoire tampon. Ces fonctions sont des versions de [_strdate, _wstrdate](strdate-wstrdate.md) avec des améliorations de sécurité, comme décrit dans [fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*mémoire tampon*\
Pointeur vers une mémoire tampon pour placer la chaîne de Date mise en forme.

*corps*\
Taille de la mémoire tampon en unités de caractères.

## <a name="return-value"></a>Valeur retournée

Zéro si l’opération réussit. La valeur de retour est un code d’erreur en cas d’échec. Les codes d’erreur sont définis dans ERRNO.H. Consultez le tableau ci-dessous pour en savoir plus sur les erreurs générées exactement par cette fonction. Pour plus d’informations sur les codes d’erreur, consultez [errno](../../c-runtime-library/errno-constants.md).

## <a name="error-conditions"></a>Conditions d’erreur

|*buffer*|*size*|Renvoie|Contenu de la *mémoire tampon*|
|--------------|------------------------|------------|--------------------------|
|**NUL**|(indifférent)|**EINVAL**|Non modifiée|
|Not **null** (pointant vers une mémoire tampon valide)|0|**EINVAL**|Non modifiée|
|Not **null** (pointant vers une mémoire tampon valide)|0 *taille* de < < 9|**EINVAL**|Chaîne vide|
|Not **null** (pointant vers une mémoire tampon valide)|*taille* >= 9|0|Date actuelle au format spécifié dans la section Notes|

## <a name="security-issues"></a>Problèmes de sécurité

Le passage d’une valeur non NULL non valide pour la *mémoire tampon* entraîne une violation d’accès si le paramètre de *taille* est supérieur à neuf.

La transmission d’une *valeur supérieure à la taille réelle* de la *mémoire tampon* entraîne un dépassement de mémoire tampon.

## <a name="remarks"></a>Notes 

Ces fonctions fournissent des versions plus sécurisées de **_strdate** et **_wstrdate**. La fonction **_strdate_s** copie la date système actuelle dans la mémoire tampon vers laquelle pointe la *mémoire tampon*. Il est mis `mm/dd/yy`en forme `mm` , où est le mois à deux `dd` chiffres, est le jour à deux chiffres `yy` et est les deux derniers chiffres de l’année. Par exemple, la chaîne `12/05/99` représente le 5 décembre 1999. La mémoire tampon doit avoir une longueur d’au moins neuf caractères.

**_wstrdate_s** est une version à caractères larges de **_strdate_s**; l’argument et la valeur de retour de **_wstrdate_s** sont des chaînes à caractères larges. Ces fonctions se comportent sinon de façon identique.

Lorsque *buffer* est un pointeur **null** ou que la *taille* est inférieure à neuf caractères, le gestionnaire de paramètre non valide est appelé. Il est décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent-1. Elles définissent **errno** sur **EINVAL** si la mémoire tampon est **null** ou si la *taille* est inférieure ou égale à 0. Ou, ils définissent **errno** sur **ERANGE** si la *taille* est inférieure à 9.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle. Les surcharges peuvent déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de *taille* . Ils peuvent remplacer automatiquement les fonctions non sécurisées par leurs équivalents plus récents et plus sécurisés. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Les versions de la bibliothèque de débogage de ces fonctions remplissent d’abord la mémoire tampon avec 0xFE. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Mappage de routines de texte générique :

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate_s**|**_strdate_s**|**_strdate_s**|**_wstrdate_s**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_strdate**|\<time.h>|
|**_wstrdate**|\<time.h> ou \<wchar.h>|
|**_strdate_s**|\<time.h>|

## <a name="example"></a> Exemple

Consultez l’exemple relatif à [time](time-time32-time64.md).

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)\
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)\
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)\
[gmtime_s, _gmtime32_s _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s, _localtime32_s _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)\
[heure, _time32, _time64](time-time32-time64.md)\
[_tzset](tzset.md)
