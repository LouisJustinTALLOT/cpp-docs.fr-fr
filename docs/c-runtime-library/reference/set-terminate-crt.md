---
title: set_terminate (CRT) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e62dc1e4f99a1d2707c6e7b86c79e0ffc8aa027
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450974"
---
# <a name="setterminate-crt"></a>set_terminate (CRT)

Installe votre propre routine de terminaison à être appelé par **Terminer**.

## <a name="syntax"></a>Syntaxe

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>Paramètres

*termFunction*<br/>
Pointeur désignant une fonction d’arrêt que vous écrivez.

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la fonction précédente enregistrée par **set_terminate** afin que la fonction précédente permettre être restaurée ultérieurement. Si aucune fonction précédente n’a été définie, la valeur de retour peut être utilisée pour restaurer le comportement par défaut ; Cette valeur peut être **NULL**.

## <a name="remarks"></a>Notes

Le **set_terminate** fonction installe *termFunction* que la fonction appelée par **Terminer**. **set_terminate** est utilisé avec la gestion des exceptions C++ et peut être appelée à tout moment dans votre programme avant que l’exception est levée. **Terminer** appelle [abandonner](abort.md) par défaut. Vous pouvez modifier cette valeur par défaut en écrivant votre propre fonction d’arrêt et en appelant **set_terminate** avec le nom de votre fonction comme argument. **Terminer** appelle la dernière fonction donnée comme argument à **set_terminate**. Une fois exécutant une tâches de nettoyage, vous le souhaitez *termFunction* doit quitter le programme. Si elle ne quitte pas (si elle retourne à son appelant), [abandonner](abort.md) est appelée.

Dans un environnement multithread, les fonctions d’arrêt sont gérées séparément pour chaque thread. Chaque nouveau thread doit installer sa propre fonction d’arrêt. Par conséquent, chaque thread est responsable de sa propre gestion des arrêts.

Le **terminate_function** type est défini dans le Gestionnaire d’événements. H comme un pointeur vers une fonction définie par l’utilisateur un arrêt, *termFunction* qui retourne **void**. Votre fonction personnalisée *termFunction* ne peut prendre aucun argument et ne doit pas retourner à son appelant. Dans ce cas, [abandonner](abort.md) est appelée. Une exception ne peut pas être levée à partir de *termFunction*.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> Le **set_terminate** fonctionne uniquement en dehors du débogueur.

Il existe un seul **set_terminate** gestionnaire pour tous les liée de manière dynamique DLL ou exe ; même si vous appelez **set_terminate** votre gestionnaire peut être remplacé par un autre, ou vous pouvez remplacer un gestionnaire défini par un autre Fichier DLL ou EXE.

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
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
