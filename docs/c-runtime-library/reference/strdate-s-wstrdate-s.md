---
title: _strdate_s, _wstrdate_s
ms.date: 11/04/2016
api_name:
- _strdate_s
- _wstrdate_s
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
ms.openlocfilehash: fadd30ec81cff59d675212e59c8513656c7b2f35
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940749"
---
# <a name="_strdate_s-_wstrdate_s"></a>_strdate_s, _wstrdate_s

Copient la date système actuelle dans une mémoire tampon. Ces versions de [_strdate, _wstrdate](strdate-wstrdate.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _strdate_s(
   char *buffer,
   size_t numberOfElements
);
errno_t _wstrdate_s(
   wchar_t *buffer,
   size_t numberOfElements
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

*buffer*<br/>
Pointeur désignant une mémoire tampon qui sera remplie avec la chaîne de date mise en forme.

*numberOfElements*<br/>
Taille de la mémoire tampon.

## <a name="return-value"></a>Valeur de retour

Zéro si l’opération réussit. En cas d’échec, la valeur de retour est un code d’erreur. Les codes d’erreur sont définis dans ERRNO.H. Consultez le tableau ci-dessous pour en savoir plus sur les erreurs générées exactement par cette fonction. Pour plus d’informations sur les codes d’erreur, consultez [errno](../../c-runtime-library/errno-constants.md).

## <a name="error-conditions"></a>Conditions d’erreur

|*buffer*|*numberOfElements*|Renvoie|Contenu de la *mémoire tampon*|
|--------------|------------------------|------------|--------------------------|
|**NULL**|(indifférent)|**EINVAL**|Non modifiée|
|Not **null** (pointant vers une mémoire tampon valide)|0|**EINVAL**|Non modifiée|
|Not **null** (pointant vers une mémoire tampon valide)|0 < *numberOfElements* < 9|**EINVAL**|Chaîne vide|
|Not **null** (pointant vers une mémoire tampon valide)|*numberOfElements* >= 9|0|Date actuelle au format spécifié dans la section Notes|

## <a name="security-issues"></a>Problèmes de sécurité

Le passage d’une valeur non **null** non valide pour la mémoire tampon entraîne une violation d’accès si le paramètre *NumberOfElements* est supérieur à 9.

Le passage de valeurs pour une taille supérieure à la taille réelle de la *mémoire tampon* entraîne un dépassement de mémoire tampon.

## <a name="remarks"></a>Notes

Ces fonctions fournissent des versions plus sécurisées de **_strdate** et **_wstrdate**. La fonction **_strdate_s** copie la date système actuelle dans la mémoire tampon vers laquelle pointe la *mémoire tampon*, avec la mise en forme **mm**/**JJ**/**AA**, où **mm** est deux chiffres représentant le mois, **JJ** est deux chiffres représentant le jour et **YY** les deux derniers chiffres de l’année. Par exemple, la chaîne **12/05/99** représente le 5 décembre 1999. La chaîne doit comporter au moins 9 caractères.

**_wstrdate_s** est une version à caractères larges de **_strdate_s**; l’argument et la valeur de retour de **_wstrdate_s** sont des chaînes à caractères larges. Ces fonctions se comportent sinon de façon identique.

Si *la mémoire tampon* est un pointeur **null** ou si la valeur de *NumberOfElements* est inférieure à 9 caractères, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent-1 et attribuent à **errno** la valeur **EINVAL** si la mémoire tampon a la **valeur null** ou si *NumberOfElements* est inférieur ou égal à 0, ou affectez à **errno** la valeur **ERANGE** si *NumberOfElements* est inférieur à 9.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument taille) et peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalentes plus récentes et sécurisées. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mapping"></a>Mappage de routines de texte générique :

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate_s**|**_strdate_s**|**_strdate_s**|**_wstrdate_s**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_strdate**|\<time.h>|
|**_wstrdate**|\<time.h> ou \<wchar.h>|
|**_strdate_s**|\<time.h>|

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [time](time-time32-time64.md).

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
