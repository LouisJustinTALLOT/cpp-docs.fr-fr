---
title: _pclose
ms.date: 11/04/2016
api_name:
- _pclose
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _pclose
- pclose
helpviewer_keywords:
- _pclose function
- pclose function
- pipes, closing
ms.assetid: e2e31a9e-ba3a-4124-bcbb-c4040110b3d3
ms.openlocfilehash: 383dd96553463a2619537cf06fc6534770ed88d5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951081"
---
# <a name="_pclose"></a>_pclose

Attend un nouveau processeur de commandes et ferme le flux au niveau du canal associé.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _pclose(
FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*stream*<br/>
Valeur de retour de l’appel précédent à **_popen**.

## <a name="return-value"></a>Valeur de retour

Retourne l’état de sortie du processeur de commandes de fin ou-1 si une erreur se produit. Le format de la valeur de retour est le même que pour **_cwait**, sauf que les octets de poids faible et de poids fort sont permutés. Si Stream a la **valeur null**, **_pclose** définit **errno** sur **EINVAL** et retourne-1.

Pour obtenir des informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **_pclose** recherche l’ID de processus du processeur de commandes (cmd. exe) Démarré par l’appel **_popen** associé, exécute un appel [_cwait](cwait.md) sur le nouveau processeur de commandes, puis ferme le flux sur le canal associé.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_pclose**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[_pipe](pipe.md)<br/>
[_popen, _wpopen](popen-wpopen.md)<br/>
