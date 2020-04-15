---
title: _open_osfhandle
ms.date: 4/2/2020
api_name:
- _open_osfhandle
- _o__open_osfhandle
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _open_osfhandle
- open_osfhandle
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
ms.openlocfilehash: 16966bedd80dc90eaa89ee46e6b633a9cf7af74f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338545"
---
# <a name="_open_osfhandle"></a>_open_osfhandle

Associe un descripteur de fichiers C run-time à une poignée de fichier système d’exploitation existante.

## <a name="syntax"></a>Syntaxe

```cpp
int _open_osfhandle (
   intptr_t osfhandle,
   int flags
);
```

### <a name="parameters"></a>Paramètres

*osfhandle*<br/>
Poignée de fichier système d’exploitation.

*Drapeaux*<br/>
Types d’opération autorisés.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, **_open_osfhandle** retourne un descripteur de fichier Runtime C. Sinon, retourne -1.

## <a name="remarks"></a>Notes

La fonction **_open_osfhandle** attribue un descripteur de fichier C run-time. Il associe ce descripteur de fichier avec la poignée de fichier du système d’exploitation spécifiée par *osfhandle*. Pour éviter un avertissement du compilateur, castez l’argument *osfhandle* de **HANDLE** en **intptr_t**. L’argument *flags* est une expression d’entier formée à partir d’une ou plusieurs des constantes de manifeste définies dans \<fcntl.h>. Vous pouvez utiliser l’opérateur bitwise-OR ( **&#124;** ) pour combiner deux constantes manifestes ou plus pour former l’argument *des drapeaux.*

Les constantes de manifeste sont définies dans \<fcntl.h> :

|||
|-|-|
| **\_O\_APPEND** | Positionne un pointeur de fichier à la fin du fichier avant chaque opération d’écriture. |
| **\_O\_RDONLY** | Ouvre le fichier pour un accès en lecture uniquement. |
| **\_O\_TEXTE** | Ouvre le fichier en mode texte (traduit). |
| **\_O\_WTEXT** | Ouvre le fichier en mode Unicode (UTF-16 traduit). |

L’appel de **_open_osfhandle** transfère la propriété du handle de fichier Win32 au descripteur de fichier. Pour fermer un fichier ouvert avec **_open_osfhandle**, appelez [\_close](close.md). Le handle de fichier du système d’exploitation sous-jacent est également fermé par un appel à **_close**. N’appelez pas la fonction Win32 **CloseHandle** sur le handle d’origine. Si le descripteur de fichier est la propriété d’un **flux de &#42;FILE,** alors un appel à [fclose](fclose-fcloseall.md) ferme à la fois le descripteur de fichier et la poignée sous-jacente. Dans ce cas, n’appelez pas **_close** sur le descripteur de fichier ou **CloseHandle** sur le handle d’origine.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[\_get_osfhandle](get-osfhandle.md)
