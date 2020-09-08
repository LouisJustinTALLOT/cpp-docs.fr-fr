---
title: INP, _inp, inpw, _inpw, _inpd
description: Décrit les fonctions INP, _inp, inpw, _inpw et _inpd des fonctions obsolètes et supprimées de la bibliothèque Microsoft C Runtime (CRT).
ms.date: 12/09/2019
api_name:
- inp
- inpw
- _inp
- _inpw
- _inpd
api_location:
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- inp
- inpw
- _inp
- _inpw
- _inpd
helpviewer_keywords:
- inp function
- inpw function
- ports, I/O routines
- inpd function
- _inp function
- _inpd function
- I/O [CRT], port
- _inpw function
ms.assetid: 5d9c2e38-fc85-4294-86d5-7282cc02d1b3
ms.openlocfilehash: aafcd633b2ee04c9ced1520d4ecd1520475d0fea
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556474"
---
# <a name="inp-_inp-inpw-_inpw-_inpd"></a>INP, _inp, inpw, _inpw, _inpd

Entrées, à partir d’un port, d’un octet ( `inp` , `_inp` ), d’un mot ( `inpw` , `_inpw` ) ou d’un mot double ( `_inpd` ).

> [!IMPORTANT]
> Ces fonctions sont obsolètes. À compter de Visual Studio 2015, ils ne sont pas disponibles dans le CRT. \
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```cpp
int _inp(
   unsigned short port
);
unsigned short _inpw(
   unsigned short port
);
unsigned long _inpd(
   unsigned short port
);
```

### <a name="parameters"></a>Paramètres

*importer*\
Numéro du port d’E/S.

## <a name="return-value"></a>Valeur renvoyée

Les fonctions retournent l’octet, le mot ou le mot double lu à partir du `port`. Il n’y a pas d’erreur de retour.

## <a name="remarks"></a>Notes

Les fonctions `_inp`, `_inpw`et `_inpd` lisent respectivement un octet, un mot et un mot double sur le port d’entrée spécifié. La valeur d’entrée peut être tout entier court non signé dans la plage 0 - 65 535.

Étant donné que ces fonctions lisent directement à partir d’un port d’E/S, elles ne peuvent pas être utilisées dans le code utilisateur.

Les `inp` `inpw` noms et sont des noms plus anciens et déconseillés pour les `_inp` `_inpw` fonctions et. Pour plus d’informations, consultez [noms de fonctions POSIX](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|`_inp`|\<conio.h>|
|`_inpw`|\<conio.h>|
|`_inpd`|\<conio.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[E/s de console et de port](../c-runtime-library/console-and-port-i-o.md)\
[outp, outpw, _outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)
