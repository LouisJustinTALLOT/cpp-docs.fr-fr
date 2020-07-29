---
title: offsetof, macro
ms.date: 11/04/2016
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
- offsetof
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
ms.openlocfilehash: ee6d5e56bb9f41a842e53984f754c7c07d58a125
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213500"
---
# <a name="offsetof-macro"></a>offsetof, macro

Récupère le décalage d'un membre au début de sa structure parent.

## <a name="syntax"></a>Syntaxe

```C
size_t offsetof(
   structName,
   memberName
);
```

### <a name="parameters"></a>Paramètres

*structName*<br/>
Nom de la structure de données parent.

*memberName*<br/>
Nom du membre dans la structure de données parent pour lequel le décalage doit être déterminé.

## <a name="return-value"></a>Valeur de retour

**OffsetOf** retourne le décalage en octets du membre spécifié à partir du début de sa structure de données parente. Il n'est pas défini pour les champs de bits.

## <a name="remarks"></a>Notes

La macro **OffsetOf** retourne le décalage en octets de *MemberName* à partir du début de la structure spécifiée par *structName* en tant que valeur de type **size_t**. Vous pouvez spécifier des types avec le **`struct`** mot clé.

> [!NOTE]
> **OffsetOf** n’est pas une fonction et ne peut pas être décrit à l’aide d’un prototype C.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**offsetof**|\<stddef.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)<br/>
