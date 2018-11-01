---
title: _CrtIsMemoryBlock
ms.date: 11/04/2016
apiname:
- _CrtIsMemoryBlock
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
- CrtlsMemoryBlock
- _CrtIsMemoryBlock
helpviewer_keywords:
- _CrtIsMemoryBlock function
- CrtIsMemoryBlock function
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
ms.openlocfilehash: c4a85ebeb45552c6f5355853de2a45766d6bc984
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555741"
---
# <a name="crtismemoryblock"></a>_CrtIsMemoryBlock

Vérifie qu’un bloc de mémoire spécifié est dans le tas local et qu’il a un identificateur de type de bloc de tas de débogage valide (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
int _CrtIsMemoryBlock(
   const void *userData,
   unsigned int size,
   long *requestNumber,
   char **filename,
   int *linenumber
);
```

### <a name="parameters"></a>Paramètres

*userData*<br/>
Pointeur indiquant le début d’un bloc de mémoire à vérifier.

*size*<br/>
Taille du bloc spécifié (en octets).

*requestNumber*<br/>
Pointeur vers le numéro d’allocation du bloc ou **NULL**.

*filename*<br/>
Pointeur vers le nom du fichier source qui a demandé le bloc ou **NULL**.

*linenumber*<br/>
Pointeur vers le numéro de ligne dans le fichier source ou **NULL**.

## <a name="return-value"></a>Valeur de retour

**_CrtIsMemoryBlock** retourne **TRUE** si le bloc de mémoire spécifié se trouve dans le tas local et a un identificateur de type bloc du tas de débogage valide ; sinon, la fonction retourne **FALSE**.

## <a name="remarks"></a>Notes

Le **_CrtIsMemoryBlock** fonction vérifie qu’un bloc de mémoire spécifié se trouve dans le tas local de l’application et qu’il a un identificateur de type de bloc valide. Cette fonction peut également être utilisée pour obtenir le numéro d’ordre d’allocation d’objet et le numéro de ligne/nom du fichier source où l’allocation de bloc de mémoire a été initialement demandée. Transmission non -**NULL** valeurs pour le *requestNumber*, *filename*, ou *linenumber* causes de paramètres **_ CrtIsMemoryBlock** pour définir ces paramètres pour les valeurs dans l’en-tête de débogage du bloc de mémoire, s’il trouve le bloc dans le tas local. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtIsMemoryBlock** sont supprimés lors du prétraitement.

Si **_CrtIsMemoryBlock** échoue, elle retourne **FALSE** et les paramètres de sortie sont initialisés aux valeurs par défaut : *requestNumber* et **lineNumber**  sont définies sur 0 et *filename* a la valeur **NULL**.

Comme cette fonction retourne **TRUE** ou **FALSE**, elle peut être passée à l’une des macros [_ASSERT](assert-asserte-assert-expr-macros.md) pour créer un mécanisme de gestion des erreurs de débogage simple. L'exemple suivant provoque un échec d'assertion si l'adresse spécifiée n'est pas située dans le tas local :

```C
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,
          &filename, &linenumber ) );
```

Pour plus d’informations sur la façon **_CrtIsMemoryBlock** peut être utilisé avec d’autres fonctions de débogage et les macros, consultez [Macros pour la création de rapports](/visualstudio/debugger/macros-for-reporting). Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtIsMemoryBlock**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

Voir l’exemple pour la rubrique [_CrtIsValidHeapPointer](crtisvalidheappointer.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
