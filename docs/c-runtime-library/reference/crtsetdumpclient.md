---
title: _CrtSetDumpClient
ms.date: 11/04/2016
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
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
ms.openlocfilehash: 09f319f6298dbec6b229b2923bd86fc9b50314de
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342997"
---
# <a name="crtsetdumpclient"></a>_CrtSetDumpClient

Installe une fonction définie par l’application pour faire un dump **_CLIENT_BLOCK** type des blocs de mémoire (version debug uniquement).

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

Le **_CrtSetDumpClient** (fonction) permet à l’application de raccorder sa propre fonction pour vider des objets stockés dans **_CLIENT_BLOCK** processus de vidage de mémoire de débogage de blocs de mémoire dans le temps d’exécution C. Par conséquent, chaque fois qu’un débogage fonction de vidage comme [_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md) ou [_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md) exporte un **_CLIENT_BLOCK** bloc de mémoire, l’application fonction de vidage est également appelée. **_CrtSetDumpClient** fournit une application avec une méthode simple pour la détection des fuites de mémoire et de validation ou de création de rapports le contenu des données stockées dans **_CLIENT_BLOCK** blocs. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtSetDumpClient** sont supprimés lors du prétraitement.

Le **_CrtSetDumpClient** fonction installe la nouvelle fonction de vidage définie par l’application spécifiée dans *dumpClient* et retourne la fonction de vidage définie. Voici un exemple de fonction de vidage de bloc client :

```C
void DumpClientFunction( void *userPortion, size_t blockSize );
```

Le *userPortion* argument est un pointeur vers le début de la partie de données utilisateur du bloc de mémoire et *blockSize* spécifie la taille de la mémoire allouée bloc en octets. La fonction de vidage de bloc client doit retourner **void**. Le pointeur vers la fonction de vidage client passé à **_CrtSetDumpClient** est de type **_CRT_DUMP_CLIENT**, tel que défini dans Crtdbg.h :

```C
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );
```

Pour plus d’informations sur les fonctions qui opèrent sur **_CLIENT_BLOCK** type des blocs de mémoire, consultez [fonctions de raccordement de bloc Client](/visualstudio/debugger/client-block-hook-functions). La fonction [_CrtReportBlockType](crtreportblocktype.md) peut être utilisée pour retourner des informations sur les types et sous-types de blocs.

## <a name="requirements"></a>Configuration requise

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
