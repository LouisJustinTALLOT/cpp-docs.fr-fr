---
title: _CrtSetDumpClient | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtSetDumpClient
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
apitype: DLLExport
f1_keywords:
- _CrtSetDumpClient
- CrtSetDumpClient
dev_langs:
- C++
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d5fecc90b4b7259f1440a0a0d86277c769c4e16
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397221"
---
# <a name="crtsetdumpclient"></a>_CrtSetDumpClient

Installe une fonction définie par l’application pour faire un dump **_CLIENT_BLOCK** tapez des blocs de mémoire (version debug uniquement).

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

Le **_CrtSetDumpClient** fonction permet à l’application permettant d’accéder aux objets de vidage stockés dans sa propre fonction de **_CLIENT_BLOCK** blocs de mémoire dans le runtime C déboguer le processus de vidage de mémoire. Par conséquent, chaque fois qu’un débogage dump comme fonction [_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md) ou [_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md) exporte un **_CLIENT_BLOCK** bloc de mémoire, l’application fonction Dump est appelée ainsi. **_CrtSetDumpClient** fournit une application avec une méthode simple pour la détection des fuites de mémoire et de validation ou de création de rapports le contenu des données stockées dans **_CLIENT_BLOCK** blocs. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtSetDumpClient** sont supprimés lors du prétraitement.

Le **_CrtSetDumpClient** fonction installe la nouvelle fonction définie par l’application de vidage spécifiée dans *dumpClient* et retourne la fonction de vidage précédemment défini. Voici un exemple de fonction de vidage de bloc client :

```C
void DumpClientFunction( void *userPortion, size_t blockSize );
```

Le *userPortion* argument est un pointeur vers le début de la partie de données utilisateur du bloc de mémoire et *blockSize* Spécifie le bloc de la taille de la mémoire allouée en octets. La fonction de vidage de bloc client doit retourner **void**. Le pointeur vers la fonction de vidage de client qui est passé à **_CrtSetDumpClient** est de type **_CRT_DUMP_CLIENT**, comme défini dans Crtdbg.h :

```C
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );
```

Pour plus d’informations sur les fonctions qui opèrent sur **_CLIENT_BLOCK** blocs de mémoire de type, consultez [fonctions de raccordement de bloc Client](/visualstudio/debugger/client-block-hook-functions). La fonction [_CrtReportBlockType](crtreportblocktype.md) peut être utilisée pour retourner des informations sur les types et sous-types de blocs.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtSetDumpClient**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
[_CrtGetDumpClient](crtgetdumpclient.md)<br/>
