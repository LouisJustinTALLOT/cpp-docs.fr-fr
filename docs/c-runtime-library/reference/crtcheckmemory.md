---
title: _CrtCheckMemory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtCheckMemory
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
- CrtCheckMemory
- _CrtCheckMemory
dev_langs:
- C++
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b6d4b84fd717525e7206956964204794fe6b88c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396662"
---
# <a name="crtcheckmemory"></a>_CrtCheckMemory

Confirme l’intégrité des blocs de mémoire alloués dans le tas de débogage (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C

int _CrtCheckMemory( void );
```

## <a name="return-value"></a>Valeur de retour

En cas de réussite, **_CrtCheckMemory** retourne TRUE ; sinon, la fonction retourne FALSE.

## <a name="remarks"></a>Notes

Le **_CrtCheckMemory** fonction valide la mémoire allouée par le Gestionnaire de tas de débogage en vérifiant le tas de base sous-jacent et en inspectant chaque bloc de mémoire. Si une incohérence de la mémoire ou d’erreur est rencontrée dans le tas de base sous-jacente, les informations d’en-tête de débogage ou les mémoires tampons de remplacement, **_CrtCheckMemory** génère un rapport de débogage avec des informations décrivant la condition d’erreur. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtCheckMemory** sont supprimés lors du prétraitement.

Le comportement de **_CrtCheckMemory** peut être contrôlé en définissant les champs de bits de le [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) indicateur à l’aide de la [_CrtSetDbgFlag](crtsetdbgflag.md) (fonction). Activation de la **_CRTDBG_CHECK_ALWAYS_DF** entraîne sur champ de bits **_CrtCheckMemory** appelée chaque fois qu’une opération d’allocation de mémoire est demandée. Bien que cette méthode ralentisse l’exécution, il est utile d’intercepter rapidement les erreurs. Activation de la **_CRTDBG_ALLOC_MEM_DF** causes OFF de champ de bits **_CrtCheckMemory** de ne pas vérifier le tas et retourner immédiatement **TRUE**.

Comme cette fonction retourne **TRUE** ou **FALSE**, elle peut être passée à l’une des macros [_ASSERT](assert-asserte-assert-expr-macros.md) pour créer un mécanisme de gestion des erreurs de débogage simple. L’exemple suivant provoque un échec d’assertion si l’altération est détectée dans le tas :

```C
_ASSERTE( _CrtCheckMemory( ) );
```

Pour plus d’informations sur la façon **_CrtCheckMemory** peut être utilisé avec d’autres fonctions de débogage, consultez [fonctions de rapport état du tas](/visualstudio/debugger/crt-debug-heap-details). Pour obtenir une vue d’ensemble de la gestion de la mémoire et du tas de débogage, consultez [Détails du tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtCheckMemory**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple montrant comment utiliser **_CrtCheckMemory**, consultez [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
