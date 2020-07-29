---
title: set_unexpected (CRT)
ms.date: 11/04/2016
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
ms.openlocfilehash: f05eab14a53c8abc119a8014d5ac99dc076a9c25
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226162"
---
# <a name="set_unexpected-crt"></a>set_unexpected (CRT)

Installe votre propre fonction d’arrêt qui doit être appelée par **unexpected**.

## <a name="syntax"></a>Syntaxe

```cpp
unexpected_function set_unexpected( unexpected_function unexpFunction );
```

### <a name="parameters"></a>Paramètres

*unexpFunction*<br/>
Pointeur vers une fonction que vous écrivez pour remplacer la fonction **inattendue** .

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la fonction d’arrêt précédente inscrite par **_set_unexpected** afin que la fonction précédente puisse être restaurée ultérieurement. Si aucune fonction précédente n’a été définie, la valeur de retour peut être utilisée pour restaurer le comportement par défaut ; Cette valeur peut être **null**.

## <a name="remarks"></a>Notes

La fonction **set_unexpected** installe *unexpFunction* en tant que fonction appelée par **inattendue**. **inattendu** n’est pas utilisé dans l’implémentation actuelle de gestion des exceptions C++. Le type de **unexpected_function** est défini en Eh. H en tant que pointeur vers une fonction inattendue définie par l’utilisateur, *unexpFunction* qui retourne **`void`** . Votre fonction *unexpFunction* personnalisée ne doit pas retourner à son appelant.

```cpp
typedef void ( *unexpected_function )( );
```

Par défaut, les appels **inattendus** **se terminent**. Vous pouvez modifier ce comportement par défaut en écrivant votre propre fonction d’arrêt et en appelant **set_unexpected** avec le nom de votre fonction comme argument. appel **inattendu** de la dernière fonction donnée comme argument pour **set_unexpected**.

Contrairement à la fonction d’arrêt personnalisée installée par un appel à **set_terminate**, une exception peut être levée à partir de *unexpFunction*.

Dans un environnement multithread, les fonctions inattendues sont gérées séparément pour chaque thread. Chaque nouveau thread doit installer sa propre fonction inattendue. Par conséquent, chaque thread est responsable de sa propre gestion inattendue.

Dans l’implémentation Microsoft actuelle de la gestion des exceptions C++, les appels **inattendus** **se terminent** par défaut et ne sont jamais appelés par la bibliothèque Runtime de gestion des exceptions. Il n’existe aucun avantage particulier à appeler **inattendu** plutôt que d' **arrêter**.

Il existe un seul gestionnaire de **set_unexpected** pour tous les fichiers dll ou exe liés de manière dynamique ; même si vous appelez **set_unexpected** votre gestionnaire peut être remplacé par un autre ou que vous remplacez un gestionnaire défini par une autre dll ou un autre exe.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**set_unexpected**|\<eh.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Routines de gestion des exceptions](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_unexpected](get-unexpected.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[pire](terminate-crt.md)<br/>
[erreur](unexpected-crt.md)<br/>
