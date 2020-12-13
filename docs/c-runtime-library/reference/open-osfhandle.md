---
description: 'En savoir plus sur : _open_osfhandle'
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 3b5fe486416ec49f01078a4d90cab998e4bbe6c5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151656"
---
# <a name="_open_osfhandle"></a>_open_osfhandle

Associe un descripteur de fichier Runtime C à un descripteur de fichier de système d’exploitation existant.

## <a name="syntax"></a>Syntaxe

```cpp
int _open_osfhandle (
   intptr_t osfhandle,
   int flags
);
```

### <a name="parameters"></a>Paramètres

*osfhandle*<br/>
Descripteur de fichier du système d’exploitation.

*flags*<br/>
Types d’opération autorisés.

## <a name="return-value"></a>Valeur renvoyée

En cas de réussite, **_open_osfhandle** retourne un descripteur de fichier Runtime C. Sinon, retourne -1.

## <a name="remarks"></a>Notes

La fonction **_open_osfhandle** alloue un descripteur de fichier Runtime C. Il associe ce descripteur de fichier au descripteur de fichier du système d’exploitation spécifié par *osfhandle*. Pour éviter un avertissement du compilateur, castez l’argument *osfhandle* de **HANDLE** en **intptr_t**. L’argument *Flags* est une expression d’entier formée à partir d’une ou plusieurs des constantes manifestes définies dans \<fcntl.h> . Vous pouvez utiliser l’opérateur or au niveau du bit ( **&#124;** ) pour combiner deux ou plusieurs constantes manifestes pour former l’argument *Flags* .

Ces constantes manifestes sont définies dans \<fcntl.h> :

| Constante | Description |
|--|--|
| **\_O \_ Append** | Positionne un pointeur de fichier à la fin du fichier avant chaque opération d’écriture. |
| **\_O \_ RDONLY** | Ouvre le fichier pour un accès en lecture uniquement. |
| **\_O \_ Text** | Ouvre le fichier en mode texte (traduit). |
| **\_O \_ WTEXT** | Ouvre le fichier en mode Unicode (UTF-16 traduit). |

L’appel de **_open_osfhandle** transfère la propriété du handle de fichier Win32 au descripteur de fichier. Pour fermer un fichier ouvert avec **_open_osfhandle**, appelez [\_close](close.md). Le handle de fichier du système d’exploitation sous-jacent est également fermé par un appel à **_close**. N’appelez pas la fonction Win32 **CloseHandle** sur le handle d’origine. Si le descripteur de fichier appartient à un **fichier &#42;** flux, un appel à [fclose](fclose-fcloseall.md) ferme le descripteur de fichier et le handle sous-jacent. Dans ce cas, n’appelez pas **_close** sur le descripteur de fichier ou **CloseHandle** sur le handle d’origine.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[\_get_osfhandle](get-osfhandle.md)
