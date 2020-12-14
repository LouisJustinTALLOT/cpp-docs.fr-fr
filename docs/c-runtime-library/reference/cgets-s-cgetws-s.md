---
description: 'En savoir plus sur : _cgets_s, _cgetws_s'
title: _cgets_s, _cgetws_s
ms.date: 4/2/2020
api_name:
- _cgetws_s
- _cgets_s
- _o__cgets_s
- _o__cgetws_s
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 827f3c8b155f58fe13396f5dc0c66e8999b5f942
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275085"
---
# <a name="_cgets_s-_cgetws_s"></a>_cgets_s, _cgetws_s

Obtient une chaîne de caractères à partir de la console. Ces versions de [_cgets et _cgetws](../../c-runtime-library/cgets-cgetws.md) intègrent des améliorations de sécurité, comme décrit dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*mémoire tampon*<br/>
Emplacement de stockage des données.

*numberOfElements*<br/>
Taille de la mémoire tampon en caractères larges ou codés sur un octet, qui correspond aussi au nombre maximal de caractères à lire.

*pSizeRead*<br/>
Nombre de caractères véritablement lus.

## <a name="return-value"></a>Valeur renvoyée

La valeur de retour est égale à zéro en cas de réussite ; sinon, un code d'erreur est retourné en cas de défaillance.

### <a name="error-conditions"></a>Conditions d'erreur

|*mémoire tampon*|*numberOfElements*|*pSizeRead*|Renvoie|Contenu de la *mémoire tampon*|
|--------------|------------------------|-----------------|------------|--------------------------|
|**NULL**|n'importe laquelle|n'importe laquelle|**EINVAL**|n/a|
|non **null**|zéro|n'importe laquelle|**EINVAL**|non modifié|
|non **null**|n'importe laquelle|**NULL**|**EINVAL**|chaîne de longueur nulle|

## <a name="remarks"></a>Notes

**_cgets_s** et **_cgetws_s** lire une chaîne à partir de la console et copier la chaîne (avec une marque de fin null) dans la *mémoire tampon*. **_cgetws_s** est la version à caractères larges de la fonction ; en dehors de la taille des caractères, le comportement de ces deux fonctions est identique. La taille maximale de la chaîne à lire est transmise en tant que paramètre *NumberOfElements* . Cette taille doit inclure un caractère supplémentaire pour le caractère null de fin. Le nombre réel de caractères lus est placé dans *pSizeRead*.

Si une erreur se produit pendant l’opération ou durant la validation des paramètres, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et **EINVAL** est retourné.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement, ce qui évite ainsi d’avoir à spécifier un argument de taille, et elles peuvent remplacer automatiquement les fonctions plus anciennes et moins sécurisées par leurs équivalents plus récents et sécurisés. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Les versions de la bibliothèque de débogage de ces fonctions remplissent d’abord la mémoire tampon avec 0xFE. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_cgetts_s**|**_cgets_s**|**_cgets_s**|**_cgetws_s**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_cgets_s**|\<conio.h>|
|**_cgetws_s**|\<conio.h> ou \<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[E/s de console et de port](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
