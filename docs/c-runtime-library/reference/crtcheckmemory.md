---
description: 'En savoir plus sur : _CrtCheckMemory'
title: _CrtCheckMemory
ms.date: 11/04/2016
api_name:
- _CrtCheckMemory
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
- CrtCheckMemory
- _CrtCheckMemory
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
ms.openlocfilehash: f2537997a9adc1c2346560d3b65eecc633933616
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221590"
---
# <a name="_crtcheckmemory"></a>_CrtCheckMemory

Confirme l’intégrité des blocs de mémoire alloués dans le tas de débogage (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C

int _CrtCheckMemory( void );
```

## <a name="return-value"></a>Valeur de retour

En cas de réussite, **_CrtCheckMemory** retourne la valeur true ; dans le cas contraire, la fonction retourne FALSe.

## <a name="remarks"></a>Notes

La fonction **_CrtCheckMemory** valide la mémoire allouée par le gestionnaire de tas de débogage en vérifiant le tas de base sous-jacent et en inspectant chaque bloc de mémoire. Si une erreur ou une incohérence de mémoire est rencontrée dans le tas de base sous-jacent, les informations d’en-tête de débogage ou les mémoires tampons de remplacement, **_CrtCheckMemory** génère un rapport de débogage avec des informations décrivant la condition d’erreur. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtCheckMemory** sont supprimés lors du prétraitement.

Le comportement de **_CrtCheckMemory** peut être contrôlé en définissant les champs de bits de l’indicateur de [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) à l’aide de la fonction [_CrtSetDbgFlag](crtsetdbgflag.md) . Le fait de transformer le champ de bits **_CRTDBG_CHECK_ALWAYS_DF** sur entraîne l’appel de **_CrtCheckMemory** à chaque fois qu’une opération d’allocation de mémoire est demandée. Bien que cette méthode ralentisse l’exécution, il est utile d’intercepter rapidement les erreurs. Si vous désactivez le champ de bits **_CRTDBG_ALLOC_MEM_DF** , **_CrtCheckMemory** ne pas vérifier le tas et retourner immédiatement la **valeur true**.

Étant donné que cette fonction retourne **true** ou **false**, elle peut être passée à l’une des macros [_ASSERT](assert-asserte-assert-expr-macros.md) pour créer un mécanisme de gestion des erreurs de débogage simple. L’exemple suivant provoque un échec d’assertion si l’altération est détectée dans le tas :

```C
_ASSERTE( _CrtCheckMemory( ) );
```

Pour plus d’informations sur la façon dont **_CrtCheckMemory** peut être utilisé avec d’autres fonctions de débogage, consultez [fonctions de rapport d’État du tas](/visualstudio/debugger/crt-debug-heap-details). Pour obtenir une vue d’ensemble de la gestion de la mémoire et du tas de débogage, consultez [Détails du tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtCheckMemory**|\<crtdbg.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de **_CrtCheckMemory**, consultez [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
