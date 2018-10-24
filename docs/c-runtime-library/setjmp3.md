---
title: _setjmp3 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _setjmp3
apilocation:
- msvcrt.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- setjmp3
- _setjmp3
dev_langs:
- C++
helpviewer_keywords:
- _setjmp3 function
- setjmp3 function
ms.assetid: 6129c2f3-8bac-4fdb-a827-44e1eebba500
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22416f4036d79f9e9b7c95f1cf9098e450533f39
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054270"
---
# <a name="setjmp3"></a>_setjmp3

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

*env*<br/>
[out] Adresse de la mémoire tampon chargée de stocker les informations d’état.

*count*<br/>
[in] Nombre de `DWORD` d’informations supplémentaires stockés dans le paramètre `optional parameters`.

*optional parameters*<br/>
[in] Données supplémentaires transmises par l’intrinsèque `setjmp`. Le premier `DWORD` est un pointeur de fonction utilisé pour dérouler des données supplémentaires et rétablir un état de registre non volatile. Le deuxième `DWORD` est le niveau d'essai à restaurer. Les données supplémentaires éventuelles sont enregistrées dans le tableau de données générique dans `jmp_buf`.

## <a name="return-value"></a>Valeur de retour

Retourne toujours 0.

## <a name="remarks"></a>Notes

N'utilisez pas cette fonction dans un programme C++. Il s'agit d'une fonction intrinsèque qui ne prend pas en charge C++. Pour plus d'informations sur l'utilisation de `setjmp`, consultez [Utilisation de setjmp/longjmp](../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Configuration requise

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[setjmp](../c-runtime-library/reference/setjmp.md)