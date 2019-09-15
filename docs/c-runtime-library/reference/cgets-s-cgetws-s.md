---
title: _cgets_s, _cgetws_s
ms.date: 11/04/2016
api_name:
- _cgetws_s
- _cgets_s
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
- api-ms-win-crt-conio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cgets_s
- cgets_s
- cgetws_s
- _cgetws_s
helpviewer_keywords:
- strings [C++], getting from console
- console, getting strings from
- _cgets_s function
- cget_s function
- _cgetws_s function
- cgetws_s function
ms.assetid: 38b74897-afe6-4dd9-a43f-36a3c0d72c5c
ms.openlocfilehash: 2039fc32cecb768c3c3fbc239446abedeb48f188
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939263"
---
# <a name="_cgets_s-_cgetws_s"></a>_cgets_s, _cgetws_s

Obtient une chaîne de caractères à partir de la console. Ces versions de [_cgets et _cgetws](../../c-runtime-library/cgets-cgetws.md) intègrent des améliorations de sécurité, comme décrit dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _cgets_s(
   char *buffer,
   size_t numberOfElements,
   size_t *pSizeRead
);
errno_t _cgetws_s(
   wchar_t *buffer
   size_t numberOfElements,
   size_t *pSizeRead
);
template <size_t size>
errno_t _cgets_s(
   char (&buffer)[size],
   size_t *pSizeRead
); // C++ only
template <size_t size>
errno_t _cgetws_s(
   wchar_t (&buffer)[size],
   size_t *pSizeRead
); // C++ only
```

### <a name="parameters"></a>Paramètres

*buffer*<br/>
Emplacement de stockage des données.

*numberOfElements*<br/>
Taille de la mémoire tampon en caractères larges ou codés sur un octet, qui correspond aussi au nombre maximal de caractères à lire.

*pSizeRead*<br/>
Nombre de caractères véritablement lus.

## <a name="return-value"></a>Valeur de retour

La valeur de retour est égale à zéro en cas de réussite ; sinon, un code d'erreur est retourné en cas de défaillance.

### <a name="error-conditions"></a>Conditions d’erreur

|*buffer*|*numberOfElements*|*pSizeRead*|Renvoie|Contenu de la *mémoire tampon*|
|--------------|------------------------|-----------------|------------|--------------------------|
|**NULL**|any|any|**EINVAL**|N/A|
|Non **null**|zéro|any|**EINVAL**|non modifié|
|Non **null**|any|**NULL**|**EINVAL**|chaîne de longueur nulle|

## <a name="remarks"></a>Notes

**_cgets_s** et **_cgetws_s** lisent une chaîne à partir de la console et copient la chaîne (avec une marque de fin null) dans la *mémoire tampon*. **_cgetws_s** est la version à caractères larges de la fonction ; en dehors de la taille des caractères, le comportement de ces deux fonctions est identique. La taille maximale de la chaîne à lire est transmise en tant que paramètre *NumberOfElements* . Cette taille doit inclure un caractère supplémentaire pour le caractère null de fin. Le nombre réel de caractères lus est placé dans *pSizeRead*.

Si une erreur se produit pendant l’opération ou durant la validation des paramètres, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et **EINVAL** est retourné.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement, ce qui évite ainsi d’avoir à spécifier un argument de taille, et elles peuvent remplacer automatiquement les fonctions plus anciennes et moins sécurisées par leurs équivalents plus récents et sécurisés. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_cgetts_s**|**_cgets_s**|**_cgets_s**|**_cgetws_s**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_cgets_s**|\<conio.h>|
|**_cgetws_s**|\<conio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[E/S de console et de port](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
