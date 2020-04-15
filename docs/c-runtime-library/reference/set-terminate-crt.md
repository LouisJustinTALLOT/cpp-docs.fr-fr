---
title: set_terminate (CRT)
ms.date: 4/2/2020
api_name:
- set_terminate
- _o_set_terminate
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 08ea5bb8c446fadac6a7bcf7ca172c5d14546776
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332104"
---
# <a name="set_terminate-crt"></a>set_terminate (CRT)

Installe votre propre routine de terminaison à appeler par **résiliation**.

## <a name="syntax"></a>Syntaxe

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>Paramètres

*termeFunction*<br/>
Pointeur désignant une fonction d’arrêt que vous écrivez.

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur à la fonction précédente enregistrée par **set_terminate** afin que la fonction précédente puisse être restaurée plus tard. Si aucune fonction antérieure n’a été définie, la valeur de retour peut être utilisée pour restaurer le comportement par défaut; cette valeur peut être **NULL**.

## <a name="remarks"></a>Notes

La fonction **set_terminate** installe *termeFunction* comme fonction appelée par **fin**. **set_terminate** est utilisé avec la manipulation d’exception de C et peut être appelé à n’importe quel point de votre programme avant que l’exception soit lancée. **mettre fin aux** appels [avorter](abort.md) par défaut. Vous pouvez modifier ce défaut en écrivant votre propre fonction de terminaison et en appelant **set_terminate** avec le nom de votre fonction comme argument. **mettre fin aux** appels de la dernière fonction donnée comme un argument à **set_terminate**. Après avoir effectué les tâches de nettoyage souhaitées, *termFunction* devrait quitter le programme. S’il ne sort pas (s’il retourne à son appelant), [l’avortement](abort.md) est appelé.

Dans un environnement multithread, les fonctions d’arrêt sont gérées séparément pour chaque thread. Chaque nouveau thread doit installer sa propre fonction d’arrêt. Par conséquent, chaque thread est responsable de sa propre gestion des arrêts.

Le **type terminate_function** est défini en EH. H comme pointeur d’une fonction de termFunction définie par l’utilisateur, *termeFunction* qui retourne **nul**. Votre terme de fonction *personnaliséFunction* ne peut prendre aucun argument et ne doit pas revenir à son appelant. Si c’est le cas, [l’avortement](abort.md) est appelé. Une exception ne peut pas être jetée de l’intérieur du *termeFunction*.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> La fonction **set_terminate** ne fonctionne qu’en dehors du débbugger.

Il existe un seul **gestionnaire set_terminate** pour tous les DLLs ou EXE liés dynamiquement; même si vous appelez **set_terminate** votre gestionnaire peut être remplacé par un autre, ou vous pouvez remplacer un gestionnaire défini par un autre DLL ou EXE.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

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
[Mettre fin](terminate-crt.md)<br/>
[Inattendu](unexpected-crt.md)<br/>
