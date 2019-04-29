---
title: _get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler
ms.date: 11/04/2016
apiname:
- _get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_invalid_parameter_handler
- stdlib/_get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
- stdlib/_get_thread_local_invalid_parameter_handler
helpviewer_keywords:
- _get_thread_local_invalid_parameter_handler function
- _get_invalid_parameter_handler function
ms.assetid: a176da0e-38ca-4d99-92bb-b0e2b8072f53
ms.openlocfilehash: 7d1a87f9ade0845994918d5a4d59dc56e190d2b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287480"
---
# <a name="getinvalidparameterhandler-getthreadlocalinvalidparameterhandler"></a>_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler

Obtient la fonction qui est appelée quand la bibliothèque CRT détecte un argument non valide.

## <a name="syntax"></a>Syntaxe

```C
_invalid_parameter_handler _get_invalid_parameter_handler(void);
_invalid_parameter_handler _get_thread_local_invalid_parameter_handler(void);
```

## <a name="return-value"></a>Valeur de retour

Un pointeur désignant la fonction de gestionnaire de paramètres non valides définie, ou un pointeur Null si aucune n’a été définie.

## <a name="remarks"></a>Notes

Le **_get_invalid_parameter_handler** fonction obtient actuellement définis Gestionnaire de paramètre non valide global. Elle retourne un pointeur Null si aucun gestionnaire de paramètres non valides global n’a été défini. De même, le **_get_thread_local_invalid_parameter_handler** Obtient le Gestionnaire de paramètre non valide de thread local actuel du thread elle est appelée sur, ou un pointeur null si aucun gestionnaire n’a été défini. Pour plus d’informations sur la façon de définir des gestionnaires de paramètres non valides globaux et locaux de thread, consultez [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

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

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_get_invalid_parameter_handler**, **_get_thread_local_invalid_parameter_handler**|C : \<stdlib.h><br /><br /> C++ : \<cstdlib> ou \<stdlib.h>|

Le **_get_invalid_parameter_handler** et **_get_thread_local_invalid_parameter_handler** fonctions sont propres à Microsoft. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Versions à la sécurité améliorée des fonctions CRT](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
