---
title: _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson
ms.date: 11/04/2016
apiname:
- _invalid_parameter
- _invalid_parameter_noinfo
- _invalid_parameter_noinfo_noreturn
- _invoke_watson
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: e43d5caaeebb6303d209d870c804357117812985
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157537"
---
# <a name="invalidparameter-invalidparameternoinfo-invalidparameternoinfonoreturn-invokewatson"></a>_invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson

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

*file_name*<br/>
Fichier de code source dans lequel le gestionnaire a été appelé.

*line_number*<br/>
Numéro de ligne dans le code source où le gestionnaire a été appelé.

*reserved*<br/>
Non utilisé.

## <a name="return-value"></a>Valeur de retour

Ces fonctions ne retournent pas de valeur. Le **_invalid_parameter_noinfo_noreturn** et **_invoke_watson** fonctions ne retournent pas à l’appelant et dans certains cas, **_invalid_parameter** et **_invalid_parameter_noinfo** ne peut pas retourner à l’appelant.

## <a name="remarks"></a>Notes

Quand des paramètres non valides sont passés aux fonctions de la bibliothèque runtime C, celles-ci appellent un *gestionnaire de paramètres non valides*, fonction qui peut être spécifiée par le programmeur pour effectuer plusieurs actions. Par exemple, il peut signaler le problème à l’utilisateur, écrire dans un journal, marquer un arrêt dans un débogueur, mettre fin au programme ou ne rien faire du tout. Si aucune fonction n’est spécifiée par le programmeur, un gestionnaire par défaut, **_invoke_watson**, est appelée.

Par défaut, lorsqu’un paramètre non valide est identifié dans le code de débogage, fonctions de la bibliothèque CRT appellent la fonction **_invalid_parameter** à l’aide des paramètres détaillés. Dans le code sans débogage, le **_invalid_parameter_noinfo** fonction est appelée, qui appelle le **_invalid_parameter** fonction à l’aide de paramètres vides. Si la fonction de bibliothèque CRT sans débogage nécessite l’arrêt du programme, le **_invalid_parameter_noinfo_noreturn** fonction est appelée, qui appelle le **_invalid_parameter** fonction à l’aide de vide les paramètres, suivis par un appel à la **_invoke_watson** (fonction) pour forcer l’arrêt du programme.

Le **_invalid_parameter** fonction vérifie si un gestionnaire de paramètre non valide défini par l’utilisateur a été défini et si tel est le cas, il appelle. Par exemple, si un gestionnaire de thread local défini par l’utilisateur a été défini par un appel à [set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) dans le thread actuel, il est appelé, puis la fonction retourne le contrôle. Sinon, si un gestionnaire de paramètres non valides global défini par l’utilisateur a été défini par un appel à [set_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md), il est appelé, puis la fonction retourne le contrôle. Sinon, le gestionnaire par défaut **_invoke_watson** est appelée. Le comportement par défaut de **_invoke_watson** consiste à mettre fin au programme. Les gestionnaires définis par l’utilisateur peuvent arrêter le programme ou retourner le contrôle. Il est recommandé que les gestionnaires définis par l’utilisateur terminent le programme, sauf si la récupération est certaine.

Lorsque le gestionnaire par défaut **_invoke_watson** est appelée, si le processeur prend en charge un [__fastfail](../../intrinsics/fastfail.md) opération, il est appelé à l’aide d’un paramètre de **FAST_FAIL_INVALID_ARG** et le processus se termine. Sinon, une exception d’échec rapide est déclenchée, qui peut être interceptée par un débogueur attaché. Si le processus est autorisé à se poursuivre, elle est arrêtée par un appel à la Windows **TerminateProcess** à l’aide d’un état du code d’exception de la fonction **STATUS_INVALID_CRUNTIME_PARAMETER**.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|------------------|
|**_invalid_parameter**, **_invalid_parameter_noinfo**, **_invalid_parameter_noinfo_noreturn**, **_invoke_watson**|\<corecrt.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Validation de paramètre](../../c-runtime-library/parameter-validation.md)<br/>
