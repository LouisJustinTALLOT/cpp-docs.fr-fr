---
title: _open_osfhandle
ms.date: 05/21/2019
apiname:
- _open_osfhandle
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _open_osfhandle
- open_osfhandle
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
ms.openlocfilehash: 9e940844eb5e37755c10999feb294981afc8683a
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821601"
---
# <a name="openosfhandle"></a>_open_osfhandle

Associe un descripteur de fichier Runtime C à un descripteur de fichier du système d’exploitation existant.

## <a name="syntax"></a>Syntaxe

```cpp
int _open_osfhandle (
   intptr_t osfhandle,
   int flags
);
```

### <a name="parameters"></a>Paramètres

*osfhandle*<br/>
Handle de fichier du système d’exploitation.

*flags*<br/>
Types d’opération autorisés.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, **_open_osfhandle** retourne un descripteur de fichier Runtime C. Sinon, elle retourne -1.

## <a name="remarks"></a>Notes

Le **_open_osfhandle** fonction alloue un descripteur de fichier Runtime C. Il associe ce descripteur de fichier avec le handle de fichier de système d’exploitation spécifié par *osfhandle*. Pour éviter un avertissement du compilateur, castez l’argument *osfhandle* de **HANDLE** en **intptr_t**. L’argument *flags* est une expression d’entier formée à partir d’une ou plusieurs des constantes de manifeste définies dans \<fcntl.h>. Vous pouvez utiliser l’opérateur OR au niveau du bit ( **&#124;** ) pour combiner deux ou plusieurs constantes manifestes pour former le *indicateurs* argument.

Les constantes de manifeste sont définies dans \<fcntl.h> :

|||
|-|-|
| **\_O\_APPEND** | Positionne un pointeur de fichier à la fin du fichier avant chaque opération d’écriture. |
| **\_O\_RDONLY** | Ouvre le fichier pour un accès en lecture uniquement. |
| **\_O\_TEXT** | Ouvre le fichier en mode texte (traduit). |
| **\_O\_WTEXT** | Ouvre le fichier en mode Unicode (UTF-16 traduit). |

L’appel de **_open_osfhandle** transfère la propriété du handle de fichier Win32 au descripteur de fichier. Pour fermer un fichier ouvert avec **_open_osfhandle**, appelez [\_close](close.md). Le handle de fichier du système d’exploitation sous-jacent est également fermé par un appel à **_close**. N’appelez pas la fonction Win32 **CloseHandle** sur le handle d’origine. Si le descripteur de fichier est détenu par un **fichier &#42;**  flux, puis un appel à [fclose](fclose-fcloseall.md) ferme le descripteur de fichier et le handle sous-jacent. Dans ce cas, n’appelez pas **_close** sur le descripteur de fichier ou **CloseHandle** sur le handle d’origine.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[\_get_osfhandle](get-osfhandle.md)
