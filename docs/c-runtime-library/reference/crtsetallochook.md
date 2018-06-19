---
title: _CrtSetAllocHook | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtSetAllocHook
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
apitype: DLLExport
f1_keywords:
- _CrtSetAllocHook
- CrtSetAllocHook
dev_langs:
- C++
helpviewer_keywords:
- _CrtSetAllocHook function
- CrtSetAllocHook function
ms.assetid: 405df37b-2fd1-42c8-83bc-90887f17f29d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d86072ceb41b966adfca298152b6209450aace3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402063"
---
# <a name="crtsetallochook"></a>_CrtSetAllocHook

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

## <a name="return-value"></a>Valeur de retour

Retourne la fonction de raccordement d’allocation défini précédemment, ou **NULL** si *allocHook* est **NULL**.

## <a name="remarks"></a>Notes

**_CrtSetAllocHook** permet à une application pour le raccordement de sa propre fonction d’allocation dans le processus d’allocation mémoire bibliothèque C Runtime debug. Ainsi, chaque appel à une fonction d’allocation de débogage pour allouer, réallouer ou libérer un bloc de mémoire déclenche un appel à la fonction de raccordement de l’application. **_CrtSetAllocHook** fournit une application avec une méthode simple pour tester comment l’application gère les situations de mémoire insuffisante, la possibilité d’examiner les modèles d’allocation et la possibilité d’enregistrer les informations d’allocation des plus tard analyse. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtSetAllocHook** sont supprimés lors du prétraitement.

Le **_CrtSetAllocHook** fonction installe la nouvelle fonction d’allocation définie par le client spécifiée dans *allocHook* et retourne la fonction de raccordement précédemment défini. L’exemple suivant montre comment un raccordement d’allocation défini par le client doit être prototypé :

```C
int YourAllocHook( int allocType, void *userData, size_t size,
                   int blockType, long requestNumber,
                   const unsigned char *filename, int lineNumber);
```

Le **allocType** argument spécifie le type de l’opération d’allocation (**_HOOK_ALLOC**, **_HOOK_REALLOC**, et **_HOOK_FREE**) qui déclenche l’appel à la fonction de raccordement de l’allocation. Lorsque le type d’allocation de déclenchement est **_HOOK_FREE**, *userData* est un pointeur vers la section de données utilisateur du bloc de mémoire sur le point d’être libérées. Toutefois, lorsque le type d’allocation de déclenchement est **_HOOK_ALLOC** ou **_HOOK_REALLOC**, *userData* est **NULL** , car le bloc de la mémoire a pas encore été affectés.

*taille* spécifie la taille de la mémoire de bloc en octets, *blockType* indique le type du bloc de mémoire, *requestNumber* est le numéro d’ordre d’objet d’allocation du bloc de mémoire et, le cas disponible, *nom de fichier* et **lineNumber** spécifier le nombre de nom et de la ligne de fichier source où l’opération de déclenchement d’allocation a été initiée.

Une fois que la fonction de raccordement a terminé le traitement, elle doit retourner une valeur booléenne, qui indique la marche à suivre au processus d’allocation du runtime C principal. Lorsque la fonction de raccordement veut le processus de répartition principale à poursuivre si la fonction de raccordement n’avait jamais été appelée, la fonction de raccordement doit retourner **TRUE**. Ainsi, l’opération d’allocation de déclenchement d’origine est exécutée. À l’aide de cette implémentation, la fonction de raccordement peut rassembler et enregistrer les informations d’allocation pour une analyse ultérieure, sans interférer avec l’opération d’allocation actuelle ou l’état du tas de débogage.

Lorsque la fonction de raccordement veut le processus de répartition principale pour continuer, car si l’opération de déclenchement d’allocation a été appelée et il a échoué, la fonction de raccordement doit retourner **FALSE**. À l’aide de cette implémentation, la fonction de raccordement peut simuler un large éventail de conditions de mémoire et d’états de tas de débogage pour tester comment l’application gère chaque situation.

Pour désactiver la fonction de raccordement, passer **NULL** à **_CrtSetAllocHook**.

Pour plus d’informations sur la façon **_CrtSetAllocHook** peut être utilisé avec d’autres fonctions de gestion de mémoire ou d’écrire vos propres fonctions de raccordement définie par le client, voir [écriture de fonctions de raccordement de débogage](/visualstudio/debugger/debug-hook-function-writing).

> [!NOTE]
> **_CrtSetAllocHook** n’est pas pris en charge sous **/CLR : pure**. Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et supprimées dans Visual Studio 2017.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtSetAllocHook**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple montrant comment utiliser **_CrtSetAllocHook**, consultez [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetAllocHook](crtgetallochook.md)<br/>
