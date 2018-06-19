---
title: _aligned_free_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_free_dbg
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
- _aligned_free_dbg
- aligned_free_dbg
dev_langs:
- C++
helpviewer_keywords:
- _aligned_free_dbg function
- aligned_free_dbg function
ms.assetid: eb0cb3c8-0992-4db8-bac3-65f1b8311ca6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88c7eb281ecc7a7175614c5c72c54c7267cf55e8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393457"
---
# <a name="alignedfreedbg"></a>_aligned_free_dbg

Libère un bloc de mémoire qui a été alloué avec [_aligned_malloc](aligned-malloc.md) ou [_aligned_offset_malloc](aligned-offset-malloc.md) (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
void _aligned_free_dbg(
   void *memblock
);
```

### <a name="parameters"></a>Paramètres

*memblock* un pointeur vers le bloc de mémoire qui a été retourné à la [_aligned_malloc](aligned-malloc.md) ou [_aligned_offset_malloc](aligned-offset-malloc.md) (fonction).

## <a name="remarks"></a>Notes

Le **_aligned_free_dbg** fonction est une version debug de la [_aligned_free](aligned-free.md) (fonction). Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, chaque appel à **_aligned_free_dbg** est réduit à un appel à **_aligned_free**. Les deux **_aligned_free** et **_aligned_free_dbg** libérer un bloc de mémoire dans le tas de base, mais **_aligned_free_dbg** prend en charge une fonctionnalité de débogage : la capacité à conserver libérés blocs dans la liste de liée du tas pour simuler des conditions de mémoire insuffisante.

**_aligned_free_dbg** effectue une vérification de validité sur tous les fichiers spécifiés et les emplacements de blocs avant d’effectuer l’opération libre. Il n'est pas prévu que l'application fournisse ces informations. Quand un bloc de mémoire est libéré, le gestionnaire de tas de débogage vérifie automatiquement l'intégrité des mémoires tampons de chaque côté de la partie utilisateur et émet un rapport d'erreurs si un remplacement a eu lieu. Si le **_CRTDBG_DELAY_FREE_MEM_DF** champ de bits de le [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) indicateur est défini, le bloc libéré est renseigné avec la valeur 0xDD, affectée le **_FREE_BLOCK** type, de bloc et conservés dans la liste du tas lié de blocs de mémoire.

Si une erreur se produit pendant la libération de la mémoire, **errno** est défini avec les informations sur la nature de la défaillance du système d’exploitation. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les types de bloc d’allocation et sur leur utilisation, consultez [Types de bloc sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les différences entre l’appel à une fonction de tas standard et sa version de débogage dans la build de débogage d’une application, consultez [Versions Debug des fonctions d’allocation du tas](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_aligned_free_dbg**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
