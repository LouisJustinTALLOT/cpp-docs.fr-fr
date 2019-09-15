---
title: _CrtIsValidPointer
ms.date: 11/04/2016
api_name:
- _CrtIsValidPointer
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
- CrtlsValidPointer
- _CrtIsValidPointer
helpviewer_keywords:
- CrtIsValidPointer function
- _CrtIsValidPointer function
ms.assetid: 91c35590-ea5e-450f-a15d-ad8d62ade1fa
ms.openlocfilehash: 490d2dea097935dee2cd2a003aa28e32f1ced69d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938768"
---
# <a name="_crtisvalidpointer"></a>_CrtIsValidPointer

Vérifie qu'un pointeur n'a pas la valeur null. Dans les versions de la bibliothèque Runtime C antérieures à Visual Studio 2010, vérifie qu'une plage mémoire spécifiée est valide pour la lecture et l'écriture (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
int _CrtIsValidPointer(
   const void *address,
   unsigned int size,
   int access
);
```

### <a name="parameters"></a>Paramètres

*address*<br/>
Pointe vers le début de la plage mémoire dont la validité doit être testée.

*size*<br/>
Taille de la plage mémoire spécifiée (en octets).

*access*<br/>
Accessibilité en lecture/écriture à déterminer pour la plage mémoire.

## <a name="return-value"></a>Valeur de retour

**_CrtIsValidPointer** retourne la valeur true si le pointeur spécifié n’a pas la valeur null. Dans les versions de bibliothèque CRT antérieures à Visual Studio 2010, retourne TRUE si la plage mémoire spécifiée est valide pour la ou les opérations spécifiées. Dans le cas contraire, la fonction retourne FALSE.

## <a name="remarks"></a>Notes

À partir de la bibliothèque CRT dans Visual Studio 2010, la *taille* et les paramètres d' *accès* sont ignorés, et **_CrtIsValidPointer** vérifie uniquement que l' *adresse* spécifiée n’est pas null. Ce test étant facile à effectuer par soi-même, nous vous déconseillons d'utiliser cette fonction. Dans les versions antérieures à Visual Studio 2010, la fonction vérifie que la plage mémoire qui commence à l' *adresse* et s’étend sur la *taille* en octets est valide pour les opérations d’accessibilité spécifiées. Lorsque l' *accès* a la valeur true, la plage mémoire est vérifiée pour la lecture et l’écriture. Lorsque l' *accès* a la valeur false, la plage mémoire n’est validée que pour la lecture. Lorsque [_ DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtIsValidPointer** sont supprimés lors du prétraitement.

Comme cette fonction retourne TRUE ou FALSE, elle peut être passée à l’une des macros [_ASSERT](assert-asserte-assert-expr-macros.md) pour créer un mécanisme de gestion des erreurs de débogage simple. L'exemple suivant provoque un échec d'assertion si la plage mémoire n'est pas valide pour les opérations à la fois de lecture et d'écriture :

```C
_ASSERTE( _CrtIsValidPointer( address, size, TRUE ) );
```

Pour plus d’informations sur la façon dont **_CrtIsValidPointer** peut être utilisé avec d’autres fonctions et macros de débogage, consultez [macros pour la création de rapports](/visualstudio/debugger/macros-for-reporting). Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtIsValidPointer**|\<crtdbg.h>|

**_CrtIsValidPointer** est une extension Microsoft. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

Voir l’exemple pour la rubrique [_CrtIsValidHeapPointer](crtisvalidheappointer.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
