---
title: _CrtSetDumpClient
ms.date: 11/04/2016
api_name:
- _CrtSetDumpClient
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CrtSetDumpClient
- CrtSetDumpClient
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
ms.openlocfilehash: fd2b037ce10f708ab133f31a20636438b0d04b93
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234261"
---
# <a name="_crtsetdumpclient"></a>_CrtSetDumpClient

Installe une fonction définie par l’application pour faire un dump **_CLIENT_BLOCK** blocs de mémoire de type (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
_CRT_DUMP_CLIENT _CrtSetDumpClient( _CRT_DUMP_CLIENT dumpClient );
```

### <a name="parameters"></a>Paramètres

*dumpClient*<br/>
Nouvelle fonction de vidage de mémoire définie par le client à raccorder au processus de vidage de mémoire de débogage du runtime C

## <a name="return-value"></a>Valeur de retour

Retourne la fonction de vidage de bloc définie par le client.

## <a name="remarks"></a>Notes

La fonction **_CrtSetDumpClient** permet à l’application de raccorder sa propre fonction pour faire un dump des objets stockés dans **_CLIENT_BLOCK** des blocs de mémoire dans le processus de vidage de mémoire de débogage du runtime C. Par conséquent, chaque fois qu’une fonction de vidage du débogage telle que [_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md) ou [_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md) vide un bloc de mémoire **_CLIENT_BLOCK** , la fonction dump de l’application est également appelée. **_CrtSetDumpClient** fournit à une application une méthode simple pour détecter les fuites de mémoire et valider ou signaler le contenu des données stockées dans des blocs **_CLIENT_BLOCK** . Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtSetDumpClient** sont supprimés lors du prétraitement.

La fonction **_CrtSetDumpClient** installe la nouvelle fonction de vidage définie par l’application spécifiée dans *dumpClient* et retourne la fonction de vidage précédemment définie. Voici un exemple de fonction de vidage de bloc client :

```C
void DumpClientFunction( void *userPortion, size_t blockSize );
```

L’argument *userPortion* est un pointeur vers le début de la partie des données utilisateur du bloc de mémoire et *BlockSize* spécifie la taille du bloc de mémoire allouée en octets. La fonction de vidage de bloc du client doit retourner **`void`** . Le pointeur vers la fonction de vidage client passé à **_CrtSetDumpClient** est de type **_CRT_DUMP_CLIENT**, comme défini dans CRTDBG. h :

```C
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );
```

Pour plus d’informations sur les fonctions qui opèrent sur des blocs de mémoire de type **_CLIENT_BLOCK** , consultez [fonctions de raccordement de bloc client](/visualstudio/debugger/client-block-hook-functions). La fonction [_CrtReportBlockType](crtreportblocktype.md) peut être utilisée pour retourner des informations sur les types et sous-types de blocs.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtSetDumpClient**|\<crtdbg.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
[_CrtGetDumpClient](crtgetdumpclient.md)<br/>
