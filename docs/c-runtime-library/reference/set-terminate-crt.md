---
title: set_terminate (CRT)
ms.date: 11/04/2016
api_name:
- set_terminate
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_terminate
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
ms.openlocfilehash: 860789a3f2fda5ef13cadffa2a00dba4fbd2090a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948353"
---
# <a name="set_terminate-crt"></a>set_terminate (CRT)

Installe votre propre routine d’arrêt à appeler par **Terminate**.

## <a name="syntax"></a>Syntaxe

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>Paramètres

*termFunction*<br/>
Pointeur désignant une fonction d’arrêt que vous écrivez.

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la fonction précédente inscrite par **set_terminate** afin que la fonction précédente puisse être restaurée ultérieurement. Si aucune fonction précédente n’a été définie, la valeur de retour peut être utilisée pour restaurer le comportement par défaut ; Cette valeur peut être **null**.

## <a name="remarks"></a>Notes

La fonction **set_terminate** installe *termFunction* en tant que fonction appelée par **Terminate**. **set_terminate** est utilisé avec C++ la gestion des exceptions et peut être appelé à tout moment dans votre programme avant que l’exception ne soit levée. **arrêter** les appels [abandonnés](abort.md) par défaut. Vous pouvez modifier cette valeur par défaut en écrivant votre propre fonction d’arrêt et en appelant **set_terminate** avec le nom de votre fonction comme argument. **Terminate** appelle la dernière fonction donnée comme argument de **set_terminate**. Après avoir effectué les tâches de nettoyage souhaitées, *termFunction* doit quitter le programme. Si elle ne se ferme pas (si elle retourne à son appelant), [Abort](abort.md) est appelé.

Dans un environnement multithread, les fonctions d’arrêt sont gérées séparément pour chaque thread. Chaque nouveau thread doit installer sa propre fonction d’arrêt. Par conséquent, chaque thread est responsable de sa propre gestion des arrêts.

Le type **terminate_function** est défini en Eh. H en tant que pointeur vers une fonction d’arrêt définie par l’utilisateur, *termFunction* qui retourne **void**. Votre fonction personnalisée *termFunction* ne peut pas prendre d’arguments et ne doit pas retourner à son appelant. Si c’est le cas, [Abort](abort.md) est appelé. Une exception ne peut pas être levée à partir de *termFunction*.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> La fonction **set_terminate** ne fonctionne qu’en dehors du débogueur.

Il existe un seul gestionnaire **set_terminate** pour tous les fichiers dll ou exe liés de manière dynamique ; même si vous appelez **set_terminate** , votre gestionnaire peut être remplacé par un autre, ou vous pouvez remplacer un gestionnaire défini par une autre dll ou un autre exe.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**set_terminate**|\<eh.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [terminate](terminate-crt.md).

## <a name="see-also"></a>Voir aussi

[Routines de gestion des exceptions](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_terminate](get-terminate.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
