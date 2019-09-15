---
title: _free_dbg
ms.date: 11/04/2016
api_name:
- _free_dbg
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
- _free_dbg
- free_dbg
helpviewer_keywords:
- memory blocks, deallocating
- freeing memory
- _free_dbg function
- free_dbg function
ms.assetid: fc5e8299-616d-48a0-b979-e037117278c6
ms.openlocfilehash: 43591ce8710dd25ad33832a5f084ca6e84bba979
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956807"
---
# <a name="_free_dbg"></a>_free_dbg

Libère un bloc de mémoire dans le tas (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
void _free_dbg(
   void *userData,
   int blockType
);
```

### <a name="parameters"></a>Paramètres

*userData*<br/>
Pointeur désignant le bloc de mémoire alloué à libérer.

*blockType*<br/>
Type de bloc de mémoire alloué à libérer : _ **client_block**, **_NORMAL_BLOCK**ou **_IGNORE_BLOCK**.

## <a name="remarks"></a>Notes

La fonction **_free_dbg** est une version de débogage de la fonction [Free](free.md) . Lorsque [_ DEBUG](../../c-runtime-library/debug.md) n’est pas défini, chaque appel à **_free_dbg** est réduit à un appel à **Free**. **Free** et **_free_dbg** libèrent tous deux un bloc de mémoire dans le tas de base, mais **_free_dbg** prend en charge deux fonctionnalités de débogage : la capacité à conserver les blocs libérés dans la liste liée du tas pour simuler des conditions de mémoire insuffisante et un paramètre de type de bloc pour types d’allocation spécifiques gratuits.

**_free_dbg** effectue une vérification de validité sur tous les fichiers et emplacements de blocs spécifiés avant d’effectuer l’opération libre. Il n'est pas prévu que l'application fournisse ces informations. Quand un bloc de mémoire est libéré, le gestionnaire de tas de débogage vérifie automatiquement l'intégrité des mémoires tampons de chaque côté de la partie utilisateur et émet un rapport d'erreurs si un remplacement a eu lieu. Si le champ de bits **_CRTDBG_DELAY_FREE_MEM_DF** de l’indicateur _ [crtdbgflag](../../c-runtime-library/crtdbgflag.md) est défini, le bloc libéré est rempli avec la valeur 0xDD, le type de bloc **_FREE_BLOCK** est affecté et il est conservé dans la liste liée du tas des blocs de mémoire.

Si une erreur se produit lors de la libération de la mémoire, **errno** est défini avec les informations du système d’exploitation sur la nature de la défaillance. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les types de bloc d’allocation et sur leur utilisation, consultez [Types de bloc sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les différences entre l’appel à une fonction de tas standard et sa version de débogage dans la build de débogage d’une application, consultez [Versions Debug des fonctions d’allocation du tas](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_free_dbg**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de **_free_dbg**, consultez [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
