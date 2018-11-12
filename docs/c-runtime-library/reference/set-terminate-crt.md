---
title: set_terminate (CRT)
ms.date: 11/04/2016
apiname:
- set_terminate
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_terminate
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
ms.openlocfilehash: 7be81dec7fba80a273d635cbd30b96b09928bc66
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493910"
---
# <a name="setterminate-crt"></a>set_terminate (CRT)

Installe votre propre routine d’arrêt doit être appelée par **Terminer**.

## <a name="syntax"></a>Syntaxe

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>Paramètres

*termFunction*<br/>
Pointeur désignant une fonction d’arrêt que vous écrivez.

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la précédente fonction inscrite par **set_terminate** afin que la fonction précédente peut être restaurée ultérieurement. Si aucune fonction précédente n’a été définie, la valeur de retournée peut être utilisée pour restaurer le comportement par défaut ; Cette valeur peut être **NULL**.

## <a name="remarks"></a>Notes

Le **set_terminate** fonction installe *termFunction* que la fonction appelée par **Terminer**. **set_terminate** est utilisé avec la gestion des exceptions C++ et peut être appelée à tout moment dans votre programme avant l’exception est levée. **mettre fin à** appels [abandonner](abort.md) par défaut. Vous pouvez modifier cette valeur par défaut en écrivant votre propre fonction d’arrêt et en appelant **set_terminate** avec le nom de votre fonction comme argument. **mettre fin à** appelle la dernière fonction donnée comme argument à **set_terminate**. Une fois exécutant une tâches de nettoyage, souhaitées *termFunction* doit fermer le programme. Si elle ne se ferme pas (si elle retourne à son appelant), [abandonner](abort.md) est appelée.

Dans un environnement multithread, les fonctions d’arrêt sont gérées séparément pour chaque thread. Chaque nouveau thread doit installer sa propre fonction d’arrêt. Par conséquent, chaque thread est responsable de sa propre gestion des arrêts.

Le **terminate_function** type est défini dans le Gestionnaire d’événements. H comme un pointeur vers une fonction d’arrêt défini par l’utilisateur, *termFunction* qui retourne **void**. Votre fonction personnalisée *termFunction* peut prendre aucun argument et ne doit pas retourner à son appelant. Le cas échéant, [abandonner](abort.md) est appelée. Une exception ne peut pas être levée depuis *termFunction*.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> Le **set_terminate** fonction fonctionne uniquement en dehors du débogueur.

Il existe un seul **set_terminate** gestionnaire pour tout dynamiquement DLL ou exe liés ; même si vous appelez **set_terminate** votre gestionnaire peut être remplacé par un autre, ou vous pouvez remplacer un gestionnaire défini par un autre DLL ou EXE.

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
