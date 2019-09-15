---
title: _set_new_mode
ms.date: 11/04/2016
api_name:
- _set_new_mode
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
ms.openlocfilehash: b248f1c97b1ec334b7441f33862b90473e08993f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948440"
---
# <a name="_set_new_mode"></a>_set_new_mode

Définit un nouveau mode de gestionnaire pour **malloc**.

## <a name="syntax"></a>Syntaxe

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>Paramètres

*newhandlermode*<br/>
Nouveau mode de gestionnaire pour **malloc**; la valeur valide est 0 ou 1.

## <a name="return-value"></a>Valeur de retour

Retourne le mode de gestionnaire précédent défini pour **malloc**. Une valeur de retour de 1 indique que, en cas d’échec d’allocation de mémoire, **malloc** a précédemment appelé la nouvelle routine de gestionnaire ; une valeur de retour de 0 indique qu’elle ne l’a pas fait. Si l’argument *newhandlermode* n’est pas égal à 0 ou 1, retourne-1.

## <a name="remarks"></a>Notes

La fonction C++ **_set_new_mode** définit le mode de nouveau gestionnaire pour [malloc](malloc.md). Le nouveau mode de gestionnaire indique si, en cas d’échec, **malloc** est appelé la routine de nouveau gestionnaire telle qu’elle est définie par [_set_new_handler](set-new-handler.md). Par défaut, **malloc** n’appelle pas la routine de nouveau gestionnaire en cas d’échec d’allocation de mémoire. Vous pouvez remplacer ce comportement par défaut de sorte que, lorsque **malloc** ne parvient pas à allouer de la mémoire, **malloc** appelle la routine de nouveau gestionnaire de la même façon que l’opérateur **New** lorsqu’il échoue pour la même raison. Pour plus d’informations, voir les opérateurs [new](../../cpp/new-operator-cpp.md) et [delete](../../cpp/delete-operator-cpp.md) dans la *Référence du langage C++* . Pour substituer la valeur par défaut, appelez :

```cpp
_set_new_mode(1);
```

au début de votre programme, ou créez un lien avec Newmode.obj (consultez [Options de lien](../../c-runtime-library/link-options.md)).

Cette fonction valide son paramètre. Si *newhandlermode* a une valeur autre que 0 ou 1, la fonction appelle le gestionnaire de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, <strong>_set_new_mode</strong> retourne-1 et définit `EINVAL` **errno** sur.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_set_new_mode**|\<new.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
[_query_new_mode](query-new-mode.md)<br/>
