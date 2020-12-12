---
description: 'En savoir plus sur : _CrtSetAllocHook'
title: _CrtSetAllocHook
ms.date: 11/04/2016
api_name:
- _CrtSetAllocHook
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CrtSetAllocHook
- CrtSetAllocHook
helpviewer_keywords:
- _CrtSetAllocHook function
- CrtSetAllocHook function
ms.assetid: 405df37b-2fd1-42c8-83bc-90887f17f29d
ms.openlocfilehash: a60024eff510f457cfc16f4afa3035efef37cca4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319662"
---
# <a name="_crtsetallochook"></a>_CrtSetAllocHook

Installe une fonction d’allocation définie par le client en la raccordant au processus d’allocation de mémoire de débogage du runtime C (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
_CRT_ALLOC_HOOK _CrtSetAllocHook(
   _CRT_ALLOC_HOOK allocHook
);
```

### <a name="parameters"></a>Paramètres

*allocHook*<br/>
Nouvelle fonction d’allocation définie par le client à raccorder au processus d’allocation de mémoire de débogage du runtime C

## <a name="return-value"></a>Valeur renvoyée

Retourne la fonction de raccordement d’allocation définie précédemment, ou **null** si *AllocHook* a la **valeur null**.

## <a name="remarks"></a>Notes

**_CrtSetAllocHook** permet à une application de raccorder sa propre fonction d’allocation au processus d’allocation de mémoire de la bibliothèque de débogage du runtime C. Ainsi, chaque appel à une fonction d’allocation de débogage pour allouer, réallouer ou libérer un bloc de mémoire déclenche un appel à la fonction de raccordement de l’application. **_CrtSetAllocHook** fournit à une application une méthode simple pour tester la façon dont l’application gère les situations de mémoire insuffisante, la possibilité d’examiner les modèles d’allocation et la possibilité de journaliser les informations d’allocation pour une analyse ultérieure. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtSetAllocHook** sont supprimés lors du prétraitement.

La fonction **_CrtSetAllocHook** installe la nouvelle fonction d’allocation définie par le client spécifiée dans *allocHook* et retourne la fonction de raccordement précédemment définie. L’exemple suivant montre comment un raccordement d’allocation défini par le client doit être prototypé :

```C
int YourAllocHook( int allocType, void *userData, size_t size,
                   int blockType, long requestNumber,
                   const unsigned char *filename, int lineNumber);
```

L’argument **allocType** spécifie le type d’opération d’allocation (**_HOOK_ALLOC**, **_HOOK_REALLOC** et **_HOOK_FREE**) qui a déclenché l’appel à la fonction de raccordement de l’allocation. Lorsque le type d’allocation de déclenchement est **_HOOK_FREE**, *UserData* est un pointeur vers la section des données utilisateur du bloc de mémoire sur le point d’être libéré. Toutefois, lorsque le type d’allocation de déclenchement est **_HOOK_ALLOC** ou **_HOOK_REALLOC**, *UserData* a la **valeur null** car le bloc de mémoire n’a pas encore été alloué.

*Size* spécifie la taille du bloc de mémoire en octets, *Blocktype* indique le type du bloc de mémoire, *requestNumber* est le numéro d’ordre d’allocation d’objet du bloc de mémoire et, si disponible, *filename* et **LineNumber** spécifient le nom du fichier source et le numéro de ligne où l’opération d’allocation de déclenchement a été initiée.

Une fois que la fonction de raccordement a terminé le traitement, elle doit retourner une valeur booléenne, qui indique la marche à suivre au processus d’allocation du runtime C principal. Quand la fonction de raccordement souhaite que le processus d’allocation principal se poursuive comme si la fonction de raccordement n’avait jamais été appelée, la fonction de raccordement doit retourner **true**. Ainsi, l’opération d’allocation de déclenchement d’origine est exécutée. À l’aide de cette implémentation, la fonction de raccordement peut rassembler et enregistrer les informations d’allocation pour une analyse ultérieure, sans interférer avec l’opération d’allocation actuelle ou l’état du tas de débogage.

Quand la fonction de raccordement souhaite que le processus d’allocation principal se poursuive comme si l’opération d’allocation de déclenchement était appelée et échoue, la fonction de raccordement doit retourner **false**. À l’aide de cette implémentation, la fonction de raccordement peut simuler un large éventail de conditions de mémoire et d’états de tas de débogage pour tester comment l’application gère chaque situation.

Pour effacer la fonction de raccordement, transmettez la **valeur null** à **_CrtSetAllocHook**.

Pour plus d’informations sur la façon dont **_CrtSetAllocHook** peut être utilisé avec d’autres fonctions de gestion de la mémoire ou comment écrire vos propres fonctions de raccordement définies par le client, consultez écriture d’une [fonction de raccordement de débogage](/visualstudio/debugger/debug-hook-function-writing).

> [!NOTE]
> **_CrtSetAllocHook** n’est pas pris en charge sous **/clr : pure**. Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et supprimées dans Visual Studio 2017.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtSetAllocHook**|\<crtdbg.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de **_CrtSetAllocHook**, consultez [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetAllocHook](crtgetallochook.md)<br/>
