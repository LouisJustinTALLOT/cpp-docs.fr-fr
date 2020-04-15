---
title: _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson
ms.date: 4/2/2020
api_name:
- _invalid_parameter
- _invalid_parameter_noinfo
- _invalid_parameter_noinfo_noreturn
- _invoke_watson
- _o__invalid_parameter_noinfo
- _o__invalid_parameter_noinfo_noreturn
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CORECRT/_invalid_parameter
- _invalid_parameter
- CORECRT/_invalid_parameter_noinfo
- _invalid_parameter_noinfo
- CORECRT/_invalid_parameter_noinfo_noreturn
- _invalid_parameter_noinfo_noreturn
- CORECRT/_invoke_watson
- _invoke_watson
ms.assetid: a4d6f1fd-ce56-4783-8719-927151a7a814
ms.openlocfilehash: 0f0a3ea3e1f2e43d53650b4017905c696269ce20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343941"
---
# <a name="_invalid_parameter-_invalid_parameter_noinfo-_invalid_parameter_noinfo_noreturn-_invoke_watson"></a>_invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson

Ces fonctions sont utilisées par la bibliothèque Runtime C pour gérer les paramètres non valides transmis aux fonctions de la bibliothèque CRT. Votre code peut également utiliser ces fonctions pour prendre en charge la gestion personnalisable ou par défaut des paramètres non valides.

## <a name="syntax"></a>Syntaxe

```C
extern "C" void __cdecl
_invalid_parameter(
    wchar_t const* const expression,
    wchar_t const* const function_name,
    wchar_t const* const file_name,
    unsigned int   const line_number,
    uintptr_t      const reserved);

extern "C" void __cdecl
_invalid_parameter_noinfo(void);

extern "C" __declspec(noreturn) void __cdecl
_invalid_parameter_noinfo_noreturn(void);

extern "C" __declspec(noreturn) void __cdecl
_invoke_watson(
    wchar_t const* const expression,
    wchar_t const* const function_name,
    wchar_t const* const file_name,
    unsigned int   const line_number,
    uintptr_t      const reserved);
```

## <a name="parameters"></a>Paramètres

*expression*<br/>
Chaîne représentant l’expression de paramètre de code source qui n’est pas valide.

*function_name*<br/>
Nom de la fonction qui a appelé le gestionnaire.

*File_name*<br/>
Fichier de code source dans lequel le gestionnaire a été appelé.

*line_number*<br/>
Numéro de ligne dans le code source où le gestionnaire a été appelé.

*Réservés au*<br/>
Inutilisé.

## <a name="return-value"></a>Valeur de retour

Ces fonctions ne retournent pas de valeur. Les fonctions **_invalid_parameter_noinfo_noreturn** et **_invoke_watson** ne reviennent pas à l’appelant et, dans certains cas, **_invalid_parameter** et **_invalid_parameter_noinfo** peuvent ne pas revenir à l’appelant.

## <a name="remarks"></a>Notes

Quand des paramètres non valides sont passés aux fonctions de la bibliothèque runtime C, celles-ci appellent un *gestionnaire de paramètres non valides*, fonction qui peut être spécifiée par le programmeur pour effectuer plusieurs actions. Par exemple, il peut signaler le problème à l’utilisateur, écrire dans un journal, marquer un arrêt dans un débogueur, mettre fin au programme ou ne rien faire du tout. Si aucune fonction n’est spécifiée par le programmeur, un gestionnaire par défaut, **_invoke_watson**, est appelé.

Par défaut, lorsqu’un paramètre non valide est identifié dans le code de débogé, les fonctions de bibliothèque CRT appellent la fonction **_invalid_parameter** à l’aide de paramètres verbeux. Dans le code non-débogé, la fonction **_invalid_parameter_noinfo** est appelée, qui appelle la fonction **_invalid_parameter** en utilisant des paramètres vides. Si la fonction de bibliothèque CRT non-débbug nécessite la résiliation du programme, la fonction **_invalid_parameter_noinfo_noreturn** est appelée, qui appelle la fonction **_invalid_parameter** en utilisant des paramètres vides, suivie d’un appel à la fonction **_invoke_watson** pour forcer la terminaison du programme.

La **fonction _invalid_parameter** vérifie si un gestionnaire de paramètres invalide défini par l’utilisateur a été défini et, dans l’affirmative, l’appelle. Par exemple, si un gestionnaire de thread local défini par l’utilisateur a été défini par un appel à [set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) dans le thread actuel, il est appelé, puis la fonction retourne le contrôle. Sinon, si un gestionnaire de paramètres non valides global défini par l’utilisateur a été défini par un appel à [set_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md), il est appelé, puis la fonction retourne le contrôle. Dans le cas contraire, le gestionnaire par défaut **_invoke_watson** est appelé. Le comportement par défaut de **_invoke_watson** est de mettre fin au programme. Les gestionnaires définis par l’utilisateur peuvent arrêter le programme ou retourner le contrôle. Il est recommandé que les gestionnaires définis par l’utilisateur terminent le programme, sauf si la récupération est certaine.

Lorsque le gestionnaire par défaut **_invoke_watson** est appelé, si le processeur prend en charge une [opération __fastfail,](../../intrinsics/fastfail.md) il est invoqué à l’aide d’un paramètre de **FAST_FAIL_INVALID_ARG** et le processus se termine. Sinon, une exception d’échec rapide est déclenchée, qui peut être interceptée par un débogueur attaché. Si le processus est autorisé à se poursuivre, il est résilié par un appel à la fonction Windows **TerminateProcess** en utilisant un statut de code d’exception de **STATUS_INVALID_CRUNTIME_PARAMETER**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|------------------|
|**_invalid_parameter**, **_invalid_parameter_noinfo**, **_invalid_parameter_noinfo_noreturn**, **_invoke_watson**|\<corecrt.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Validation des paramètres](../../c-runtime-library/parameter-validation.md)<br/>
