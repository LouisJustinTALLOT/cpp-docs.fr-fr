---
title: _CrtIsValidPointer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtIsValidPointer
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
- CrtlsValidPointer
- _CrtIsValidPointer
dev_langs:
- C++
helpviewer_keywords:
- CrtIsValidPointer function
- _CrtIsValidPointer function
ms.assetid: 91c35590-ea5e-450f-a15d-ad8d62ade1fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb78f8dee494fd213df6db16e2800cb9090bdf3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397265"
---
# <a name="crtisvalidpointer"></a>_CrtIsValidPointer

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

**_CrtIsValidPointer** retourne la valeur TRUE si le pointeur spécifié n’est pas null. Dans les versions de bibliothèque CRT antérieures à Visual Studio 2010, retourne TRUE si la plage mémoire spécifiée est valide pour la ou les opérations spécifiées. Dans le cas contraire, la fonction retourne FALSE.

## <a name="remarks"></a>Notes

En commençant par la bibliothèque CRT dans Visual Studio 2010, le *taille* et *accès* paramètres sont ignorés, et **_CrtIsValidPointer** vérifie uniquement que le spécifié*adresse* n’est pas null. Ce test étant facile à effectuer par soi-même, nous vous déconseillons d'utiliser cette fonction. Dans les versions antérieures de Visual Studio 2010, la fonction vérifie que la plage mémoire débutant à *adresse* et l’extension pour *taille* octets est valide pour l’ou les opérations d’accessibilité spécifiées. Lorsque *accès* est définie sur TRUE, la plage de mémoire est vérifiée pour la lecture et l’écriture. Lorsque *accès* est FALSE, la plage de mémoire n’est validée pour la lecture. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtIsValidPointer** sont supprimés lors du prétraitement.

Comme cette fonction retourne TRUE ou FALSE, elle peut être passée à l’une des macros [_ASSERT](assert-asserte-assert-expr-macros.md) pour créer un mécanisme de gestion des erreurs de débogage simple. L'exemple suivant provoque un échec d'assertion si la plage mémoire n'est pas valide pour les opérations à la fois de lecture et d'écriture :

```C
_ASSERTE( _CrtIsValidPointer( address, size, TRUE ) );
```

Pour plus d’informations sur la façon **_CrtIsValidPointer** peut être utilisé avec d’autres fonctions de débogage et les macros, consultez [Macros pour la création de rapports](/visualstudio/debugger/macros-for-reporting). Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Spécifications

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
