---
title: _set_new_mode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_new_mode
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_new_mode
- _set_new_mode
dev_langs:
- C++
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b914e950fd94435768c355f327d3d48a653e0d5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407143"
---
# <a name="setnewmode"></a>_set_new_mode

Définit un nouveau mode de gestionnaire pour **malloc**.

## <a name="syntax"></a>Syntaxe

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>Paramètres

*newhandlermode*<br/>
Mode du nouveau gestionnaire de **malloc**; valide valeur est 0 ou 1.

## <a name="return-value"></a>Valeur de retour

Retourne le gestionnaire précédent mode défini pour **malloc**. Une valeur de 1 indique que, en cas d’échec d’allocation de mémoire, de retour **malloc** précédemment appelé la routine du nouveau gestionnaire ; une valeur de retour de 0 indique qu’il n’a pas. Si le *newhandlermode* argument est différent de 0 ou 1, retourne -1.

## <a name="remarks"></a>Notes

La fonction C++ **_set_new_mode** définit le mode de nouveau gestionnaire pour [malloc](malloc.md). Le nouveau mode de gestionnaire indique si, en cas d’échec, **malloc** consiste à appeler la routine du gestionnaire en tant que jeu par [_set_new_handler](set-new-handler.md). Par défaut, **malloc** n’appelle pas la routine du gestionnaire sur les échecs d’allocation de mémoire. Vous pouvez substituer ce comportement par défaut afin que, lorsque **malloc** ne parvient pas à allouer de la mémoire, **malloc** appelle la routine du Gestionnaire de la même façon que les **nouveau** opérateur est Lorsqu’il échoue pour la même raison. Pour plus d’informations, voir les opérateurs [new](../../cpp/new-operator-cpp.md) et [delete](../../cpp/delete-operator-cpp.md) dans la *Référence du langage C++*. Pour substituer la valeur par défaut, appelez :

```cpp
_set_new_mode(1);
```

au début de votre programme, ou créez un lien avec Newmode.obj (consultez [Options de lien](../../c-runtime-library/link-options.md)).

Cette fonction valide son paramètre. Si *newhandlermode* tout élément autre que 0 ou 1, la fonction appelle le Gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **_ *** set_new_mode** retourne -1 et définit **errno** à **EINVAL**.

## <a name="requirements"></a>Spécifications

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
