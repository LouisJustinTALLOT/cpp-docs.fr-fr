---
title: _set_new_mode
ms.date: 4/2/2020
api_name:
- _set_new_mode
- _o__set_new_mode
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_new_mode
- _set_new_mode
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
ms.openlocfilehash: 3a27717d65714de54f477e4e2b3f243c4631fd8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332320"
---
# <a name="_set_new_mode"></a>_set_new_mode

Définit un nouveau mode de manutention pour **malloc**.

## <a name="syntax"></a>Syntaxe

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>Paramètres

*newhandlermode*<br/>
Nouveau mode de manutention pour **malloc**; la valeur valide est de 0 ou 1.

## <a name="return-value"></a>Valeur de retour

Retourne le mode de manutention précédent réglé pour **malloc**. Une valeur de retour de 1 indique que, en cas d’omission d’allouer la mémoire, **malloc** précédemment appelé la nouvelle routine de gestionnaire; une valeur de rendement de 0 indique qu’elle ne l’a pas fait. Si l’argument *du newhandlermode* n’est pas égal à 0 ou 1, renvoie -1.

## <a name="remarks"></a>Notes

La fonction C++ **_set_new_mode** définit le mode de nouveau gestionnaire pour [malloc](malloc.md). Le nouveau mode de manutention indique si, en cas de défaillance, **malloc** est d’appeler la nouvelle routine de gestionnaire tel que défini par [_set_new_handler](set-new-handler.md). Par défaut, **malloc** n’appelle pas la nouvelle routine de gestionnaire sur l’omission d’allouer la mémoire. Vous pouvez passer outre à ce comportement par défaut de sorte que, lorsque **malloc** ne parvient pas à allouer la mémoire, **malloc** appelle la nouvelle routine de gestionnaire de la même manière que le **nouvel** opérateur fait quand il échoue pour la même raison. Pour plus d’informations, voir les opérateurs [new](../../cpp/new-operator-cpp.md) et [delete](../../cpp/delete-operator-cpp.md) dans la *Référence du langage C++*. Pour substituer la valeur par défaut, appelez :

```cpp
_set_new_mode(1);
```

au début de votre programme ou lien avec Newmode.obj (voir [Options Link](../../c-runtime-library/link-options.md)).

Cette fonction valide son paramètre. Si *newhandlermode* est autre chose que 0 ou 1, la fonction invoque le gestionnaire de paramètres invalides, tel que décrit dans [La validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, <strong>_set_new_mode</strong> renvoie -1 et définit **errno** à `EINVAL`.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_set_new_mode**|\<new.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[Gratuit](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
[_query_new_mode](query-new-mode.md)<br/>
