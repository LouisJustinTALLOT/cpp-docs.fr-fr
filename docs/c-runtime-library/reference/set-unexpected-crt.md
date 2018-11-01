---
title: set_unexpected (CRT)
ms.date: 11/04/2016
apiname:
- set_unexpected
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
- set_unexpected
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
ms.openlocfilehash: 6c38421e447ca7b3f263148f51f0ade5c59e2804
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484225"
---
# <a name="setunexpected-crt"></a>set_unexpected (CRT)

Installe votre propre fonction d’arrêt qui doit être appelée par **unexpected**.

## <a name="syntax"></a>Syntaxe

```cpp
unexpected_function set_unexpected( unexpected_function unexpFunction );
```

### <a name="parameters"></a>Paramètres

*unexpFunction*<br/>
Pointeur vers une fonction que vous écrivez pour remplacer le **inattendue** (fonction).

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la fonction d’arrêt inscrite par **_set_unexpected** afin que la fonction précédente peut être restaurée ultérieurement. Si aucune fonction précédente n’a été définie, la valeur de retournée peut être utilisée pour restaurer le comportement par défaut ; Cette valeur peut être **NULL**.

## <a name="remarks"></a>Notes

Le **set_unexpected** fonction installe *unexpFunction* que la fonction appelée par **inattendue**. **inattendue** n’est pas utilisé dans l’implémentation de la gestion des exceptions C++ actuelle. Le **unexpected_function** type est défini dans le Gestionnaire d’événements. H comme un pointeur vers une fonction inattendue défini par l’utilisateur, *unexpFunction* qui retourne **void**. Votre personnalisé *unexpFunction* fonction ne doit pas retourner à son appelant.

```cpp
typedef void ( *unexpected_function )( );
```

Par défaut, **inattendue** appels **Terminer**. Vous pouvez modifier ce comportement par défaut en écrivant votre propre fonction d’arrêt et en appelant **set_unexpected** avec le nom de votre fonction comme argument. **inattendue** appelle la dernière fonction donnée comme argument à **set_unexpected**.

Contrairement à la fonction d’arrêt personnalisée installée par un appel à **set_terminate**, une exception peut être levée depuis *unexpFunction*.

Dans un environnement multithread, les fonctions inattendues sont gérées séparément pour chaque thread. Chaque nouveau thread doit installer sa propre fonction inattendue. Par conséquent, chaque thread est responsable de sa propre gestion inattendue.

Dans l’implémentation actuelle de Microsoft de gestion des exceptions C++, **inattendue** appels **Terminer** par défaut et n’est jamais appelé par la bibliothèque d’exécution de la gestion des exceptions. Ne présente aucun avantage particulier à appeler **inattendue** plutôt que **Terminer**.

Il existe un seul **set_unexpected** gestionnaire pour tout dynamiquement DLL ou exe liés ; même si vous appelez **set_unexpected** votre gestionnaire peut être remplacé par un autre, ou que vous remplacez un gestionnaire défini par une autre DLL ou EXE.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**set_unexpected**|\<eh.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Routines de gestion des exceptions](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_unexpected](get-unexpected.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
