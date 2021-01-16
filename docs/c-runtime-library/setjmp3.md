---
description: 'En savoir plus sur : _setjmp3'
title: _setjmp3
ms.date: 1/14/2021
api_name:
- _setjmp3
api_location:
- msvcrt.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr120.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- setjmp3
- _setjmp3
helpviewer_keywords:
- _setjmp3 function
- setjmp3 function
ms.assetid: 6129c2f3-8bac-4fdb-a827-44e1eebba500
ms.openlocfilehash: 9d65f807c34d926485777d49156061196dfc0948
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98243097"
---
# `_setjmp3`

Fonction CRT interne. Nouvelle implémentation de la fonction `setjmp`.

## <a name="syntax"></a>Syntaxe

```
int _setjmp3(
   OUT jmp_buf env,
   int count,
   (optional parameters)
);
```

#### <a name="parameters"></a>Paramètres

*`env`*\
[out] Adresse de la mémoire tampon chargée de stocker les informations d’état.

*`count`*\
[in] Nombre de `DWORD` d’informations supplémentaires stockés dans le paramètre `optional parameters`.

*`optional parameters`*\
[in] Données supplémentaires transmises par l’intrinsèque `setjmp`. Le premier `DWORD` est un pointeur de fonction utilisé pour dérouler des données supplémentaires et rétablir un état de registre non volatile. Le deuxième `DWORD` est le niveau d'essai à restaurer. Les données supplémentaires éventuelles sont enregistrées dans le tableau de données générique dans `jmp_buf`.

## <a name="return-value"></a>Valeur renvoyée

Retourne toujours 0.

## <a name="remarks"></a>Remarques

N’utilisez pas cette fonction dans un programme C++. Il s’agit d’une fonction intrinsèque qui ne prend pas en charge C++. Pour plus d'informations sur l'utilisation de `setjmp`, consultez [Utilisation de setjmp/longjmp](../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Configuration requise

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](../c-runtime-library/reference/crt-alphabetical-function-reference.md)\
[`setjmp`](../c-runtime-library/reference/setjmp.md)
