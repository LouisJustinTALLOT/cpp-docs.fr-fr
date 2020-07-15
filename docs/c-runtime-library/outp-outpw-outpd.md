---
title: outp, outpw, _outp, _outpw, _outpd
description: Décrit les fonctions outp, outpw, _outp, _outpw et _outpd obsolètes et supprimées de la bibliothèque Microsoft C Runtime (CRT).
ms.date: 12/09/2019
api_name:
- _outpd
- _outp
- _outpw
- outp
- outpw
api_location:
- msvcrt.dll
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _outpw
- _outpd
- _outp
- outp
- outpw
- outpd
helpviewer_keywords:
- outpw function
- words
- _outpd function
- outpd function
- outp function
- ports, writing bytes at
- bytes, writing to ports
- words, writing to ports
- double words
- double words, writing to ports
- _outpw function
- _outp function
ms.assetid: c200fe22-41f6-46fd-b0be-ebb805b35181
ms.openlocfilehash: 0d28511cdf7487226635c0317b7c0ba21ab1d1be
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373474"
---
# <a name="outp-outpw-_outp-_outpw-_outpd"></a>outp, outpw, _outp, _outpw, _outpd

Génère, sur un port, un octet ( `outp` , `_outp` ), un mot ( `outpw` , `_outpw` ) ou un mot double ( `_outpd` ).

> [!IMPORTANT]
> Ces fonctions sont obsolètes. À compter de Visual Studio 2015, ils ne sont pas disponibles dans le CRT. \
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```cpp
int _outp(
   unsigned short port,
   int databyte
);
unsigned short _outpw(
   unsigned short port,
   unsigned short dataword
);
unsigned long _outpd(
   unsigned short port,
   unsigned long dataword
);
```

### <a name="parameters"></a>Paramètres

*importer*\
Numéro de port.

*databyte, dataword*\
Valeurs de sortie.

## <a name="return-value"></a>Valeur de retour

Les fonctions retournent la sortie des données. Aucun retour d'erreur.

## <a name="remarks"></a>Notes

Les fonctions `_outp`, `_outpw`et `_outpd` écrivent respectivement un octet, un mot et un mot double sur le port de sortie spécifié. L’argument *port* peut être un entier non signé compris entre 0 et 65 535 ; *databyte* peut être n’importe quel entier dans la plage 0-255 ; et *dataword* peuvent être n’importe quelle valeur dans la plage d’un entier, un entier Short non signé et un entier long non signé, respectivement.

Comme ces fonctions écrivent directement sur un port d’e/s, elles ne peuvent pas être utilisées dans le code Windows en mode utilisateur. Pour plus d’informations sur l’utilisation des ports d’e/s dans le système d’exploitation Windows, consultez [communications en série](https://docs.microsoft.com/previous-versions/ff802693(v=msdn.10)).

Les `outp` `outpw` noms et sont des noms plus anciens et déconseillés pour les `_outp` `_outpw` fonctions et. Pour plus d’informations, consultez [noms de fonctions POSIX](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|`_outp`|\<conio.h>|
|`_outpw`|\<conio.h>|
|`_outpd`|\<conio.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[E/s de console et de port](../c-runtime-library/console-and-port-i-o.md)\
[INP, inpw, _inp, _inpw, _inpd](../c-runtime-library/inp-inpw-inpd.md)
