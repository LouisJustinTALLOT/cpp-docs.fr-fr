---
title: _free_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _free_dbg
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
- _free_dbg
- free_dbg
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, deallocating
- freeing memory
- _free_dbg function
- free_dbg function
ms.assetid: fc5e8299-616d-48a0-b979-e037117278c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa485eea6f0ffda05b0ef33a808d5ec837255514
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400042"
---
# <a name="freedbg"></a>_free_dbg

Libère un bloc de mémoire dans le tas (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
void _free_dbg(
   void *userData,
   int blockType
);
```

### <a name="parameters"></a>Paramètres

*userData* pointeur vers le bloc de mémoire alloué à libérer.

*blockType* Type de bloc de mémoire alloué à libérer : **_CLIENT_BLOCK**, **_NORMAL_BLOCK**, ou **_IGNORE_BLOCK**.

## <a name="remarks"></a>Notes

Le **_free_dbg** fonction est une version debug de la [libre](free.md) (fonction). Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, chaque appel à **_free_dbg** est réduit à un appel à **libre**. Les deux **libre** et **_free_dbg** libérer un bloc de mémoire dans le tas de base, mais **_free_dbg** gère deux fonctionnalités de débogage : la capacité à conserver libérés blocs dans du tas liste liée pour simuler des conditions de mémoire insuffisante et un paramètre de type de bloc pour libérer des types d’allocation spécifiques.

**_free_dbg** effectue une vérification de validité sur tous les fichiers spécifiés et les emplacements de blocs avant d’effectuer l’opération libre. Il n'est pas prévu que l'application fournisse ces informations. Quand un bloc de mémoire est libéré, le gestionnaire de tas de débogage vérifie automatiquement l'intégrité des mémoires tampons de chaque côté de la partie utilisateur et émet un rapport d'erreurs si un remplacement a eu lieu. Si le **_CRTDBG_DELAY_FREE_MEM_DF** champ de bits de le [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) indicateur est défini, le bloc libéré est renseigné avec la valeur 0xDD, affectée le **_FREE_BLOCK** type, de bloc et conservés dans la liste du tas lié de blocs de mémoire.

Si une erreur se produit pendant la libération de la mémoire, **errno** est défini avec les informations sur la nature de la défaillance du système d’exploitation. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les types de bloc d’allocation et sur leur utilisation, consultez [Types de bloc sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les différences entre l’appel à une fonction de tas standard et sa version de débogage dans la build de débogage d’une application, consultez [Versions Debug des fonctions d’allocation du tas](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_free_dbg**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple montrant comment utiliser **_free_dbg**, consultez [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
