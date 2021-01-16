---
description: 'En savoir plus sur : set_unexpected (CRT)'
title: set_unexpected (CRT)
ms.date: 1/14/2021
api_name:
- set_unexpected
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_unexpected
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
ms.openlocfilehash: b9918e152a5d27c853aef7769b932ee4efedeef8
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98242629"
---
# <a name="set_unexpected-crt"></a>`set_unexpected` Ecran

Installe votre propre fonction d’arrêt qui doit être appelée par **`unexpected`** .

## <a name="syntax"></a>Syntaxe

```cpp
unexpected_function set_unexpected( unexpected_function unexpFunction );
```

### <a name="parameters"></a>Paramètres

*`unexpFunction`*\
Pointeur vers une fonction que vous écrivez pour remplacer la **`unexpected`** fonction.

## <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers la fonction d’arrêt précédente inscrite par **`_set_unexpected`** afin que la fonction précédente puisse être restaurée ultérieurement. Si aucune fonction précédente n’a été définie, la valeur de retour peut être utilisée pour restaurer le comportement par défaut ; Cette valeur peut être **`NULL`** .

## <a name="remarks"></a>Remarques

La **`set_unexpected`** fonction installe *unexpFunction* en tant que fonction appelée par **`unexpected`** . **`unexpected`** n’est pas utilisé dans l’implémentation actuelle de gestion des exceptions C++. Le **`unexpected_function`** type est défini en Eh. H en tant que pointeur vers une fonction inattendue définie par l’utilisateur, *unexpFunction* qui retourne **`void`** . Votre fonction *unexpFunction* personnalisée ne doit pas retourner à son appelant.

```cpp
typedef void ( *unexpected_function )( );
```

Par défaut, **`unexpected`** appelle **`terminate`** . Vous pouvez modifier ce comportement par défaut en écrivant votre propre fonction d’arrêt et en appelant **`set_unexpected`** avec le nom de votre fonction comme argument. **`unexpected`** appelle la dernière fonction donnée comme argument à **`set_unexpected`** .

Contrairement à la fonction d’arrêt personnalisée installée par un appel à **`set_terminate`** , une exception peut être levée à partir de **`unexpFunction`** .

Dans un environnement multithread, les fonctions inattendues sont gérées séparément pour chaque thread. Chaque nouveau thread doit installer sa propre fonction inattendue. Par conséquent, chaque thread est responsable de sa propre gestion inattendue.

Dans l’implémentation Microsoft actuelle de la gestion des exceptions C++, **`unexpected`** appelle **`terminate`** par défaut et n’est jamais appelé par la bibliothèque Runtime de gestion des exceptions. L’appel de **`unexpected`** plutôt que **term’inate** ne présente aucun avantage particulier.

Il existe un seul **`set_unexpected`** Gestionnaire pour tous les fichiers dll ou exe liés de manière dynamique ; même si vous appelez **`set_unexpected`** votre gestionnaire peut être remplacé par un autre ou que vous remplacez un gestionnaire défini par une autre dll ou un autre exe.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**`set_unexpected`**|`<eh.h>`|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Routines de gestion des exceptions](../../c-runtime-library/exception-handling-routines.md)\
[`abort`](abort.md)\
[`_get_unexpected`](get-unexpected.md)\
[`set_terminate`](set-terminate-crt.md)\
[`terminate`](terminate-crt.md)\
[`unexpected`](unexpected-crt.md)\
