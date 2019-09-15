---
title: _CrtIsMemoryBlock
ms.date: 11/04/2016
api_name:
- _CrtIsMemoryBlock
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
- CrtlsMemoryBlock
- _CrtIsMemoryBlock
helpviewer_keywords:
- _CrtIsMemoryBlock function
- CrtIsMemoryBlock function
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
ms.openlocfilehash: f29745acd06f6f5b3fa96367444e800bdc3e8e3a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938736"
---
# <a name="_crtismemoryblock"></a>_CrtIsMemoryBlock

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
Pointeur vers le numéro d’allocation du bloc ou **null**.

*filename*<br/>
Pointeur vers le nom du fichier source qui a demandé le bloc ou **null**.

*linenumber*<br/>
Pointeur vers le numéro de ligne dans le fichier source ou **null**.

## <a name="return-value"></a>Valeur de retour

**_CrtIsMemoryBlock** retourne la **valeur true** si le bloc de mémoire spécifié se trouve dans le tas local et possède un identificateur de type de bloc de tas de débogage valide. dans le cas contraire, la fonction retourne **false**.

## <a name="remarks"></a>Notes

La fonction **_CrtIsMemoryBlock** vérifie qu’un bloc de mémoire spécifié se trouve dans le tas local de l’application et qu’il a un identificateur de type de bloc valide. Cette fonction peut également être utilisée pour obtenir le numéro d’ordre d’allocation d’objet et le numéro de ligne/nom du fichier source où l’allocation de bloc de mémoire a été initialement demandée. Si vous transmettez des valeurs non**null** pour les paramètres *requestNumber*, *filename*ou *LineNumber* , **_CrtIsMemoryBlock** définit ces paramètres sur les valeurs de l’en-tête debug du bloc de mémoire, s’il trouve le bloc dans segment de mémoire local. Lorsque [_ DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtIsMemoryBlock** sont supprimés lors du prétraitement.

Si **_CrtIsMemoryBlock** échoue, elle retourne **false** et les paramètres de sortie sont initialisés aux valeurs par défaut : *requestNumber* et **LineNumber** ont la valeur 0 et le *nom de fichier* a la valeur **null**.

Comme cette fonction retourne **TRUE** ou **FALSE**, elle peut être passée à l’une des macros [_ASSERT](assert-asserte-assert-expr-macros.md) pour créer un mécanisme de gestion des erreurs de débogage simple. L'exemple suivant provoque un échec d'assertion si l'adresse spécifiée n'est pas située dans le tas local :

```C
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,
          &filename, &linenumber ) );
```

Pour plus d’informations sur la façon dont **_CrtIsMemoryBlock** peut être utilisé avec d’autres fonctions et macros de débogage, consultez [macros pour la création de rapports](/visualstudio/debugger/macros-for-reporting). Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

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
