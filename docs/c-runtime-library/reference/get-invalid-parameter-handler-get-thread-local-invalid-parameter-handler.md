---
description: 'En savoir plus sur : _get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler'
title: _get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler
ms.date: 4/2/2020
api_name:
- _get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
- _o__get_invalid_parameter_handler
- _o__get_thread_local_invalid_parameter_handler
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_invalid_parameter_handler
- stdlib/_get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
- stdlib/_get_thread_local_invalid_parameter_handler
helpviewer_keywords:
- _get_thread_local_invalid_parameter_handler function
- _get_invalid_parameter_handler function
ms.assetid: a176da0e-38ca-4d99-92bb-b0e2b8072f53
ms.openlocfilehash: ecb39588ea2776d661f391596d3f482628eddd7a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213375"
---
# <a name="_get_invalid_parameter_handler-_get_thread_local_invalid_parameter_handler"></a>_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler

Obtient la fonction qui est appelée quand la bibliothèque CRT détecte un argument non valide.

## <a name="syntax"></a>Syntaxe

```C
_invalid_parameter_handler _get_invalid_parameter_handler(void);
_invalid_parameter_handler _get_thread_local_invalid_parameter_handler(void);
```

## <a name="return-value"></a>Valeur de retour

Un pointeur désignant la fonction de gestionnaire de paramètres non valides définie, ou un pointeur Null si aucune n’a été définie.

## <a name="remarks"></a>Notes

La fonction **_get_invalid_parameter_handler** obtient le gestionnaire de paramètres non valides globaux actuellement définis. Elle retourne un pointeur Null si aucun gestionnaire de paramètres non valides global n’a été défini. De même, le **_get_thread_local_invalid_parameter_handler** obtient le gestionnaire de paramètres non valides local de thread actuel du thread sur lequel il est appelé, ou un pointeur null si aucun gestionnaire n’a été défini. Pour plus d’informations sur la façon de définir des gestionnaires de paramètres non valides globaux et locaux de thread, consultez [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

Le pointeur de la fonction de gestionnaire de paramètres non valides retourné a le type suivant :

```C
typedef void (__cdecl* _invalid_parameter_handler)(
    wchar_t const*,
    wchar_t const*,
    wchar_t const*,
    unsigned int,
    uintptr_t
    );
```

Pour plus d’informations sur le gestionnaire de paramètres non valides, consultez le prototype dans [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_get_invalid_parameter_handler**, **_get_thread_local_invalid_parameter_handler**|Secteur \<stdlib.h><br /><br /> C++ : \<cstdlib> ou \<stdlib.h>|

Les fonctions **_get_invalid_parameter_handler** et **_get_thread_local_invalid_parameter_handler** sont spécifiques à Microsoft. Pour plus d’informations sur la compatibilité, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Versions à sécurité améliorée des fonctions CRT](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
