---
title: Constantes d'autorisations de fichier
ms.date: 11/04/2016
f1_keywords:
- _S_IWRITE
- _S_IREAD
helpviewer_keywords:
- S_IWRITE constant
- constants [C++], file attributes
- S_IREAD constant
- file permissions [C++]
- _S_IWRITE constant
- _S_IREAD constant
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
ms.openlocfilehash: 7b9d99f8b0fc7daf8f7dc58db999c7f885a3dc8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648602"
---
# <a name="file-permission-constants"></a>Constantes d'autorisations de fichier

## <a name="syntax"></a>Syntaxe

```

#include <sys/stat.h>

```

## <a name="remarks"></a>Notes

Une de ces constantes est obligatoire quand `_O_CREAT` (`_open`, `_sopen`) est spécifié.

L’argument `pmode` spécifie les paramètres d’autorisation du fichier comme suit.

|Constante|Signification|
|--------------|-------------|
|`_S_IREAD`|Lecture autorisée|
|`_S_IWRITE`|Écriture autorisée|
|`_S_IREAD` &#124; `_S_IWRITE`|Lecture et écriture autorisées|

Lorsqu’elle est utilisée en tant qu’argument `pmode` pour `_umask`, la constante manifeste définit le paramètre d’autorisation, comme suit.

|Constante|Signification|
|--------------|-------------|
|`_S_IREAD`|Écriture non autorisée (le fichier est en lecture seule)|
|`_S_IWRITE`|Lecture non autorisée (le fichier est en écriture seule)|
|`_S_IREAD` &#124; `_S_IWRITE`|Pas d’autorisation en lecture ou écriture|

## <a name="see-also"></a>Voir aussi

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_umask](../c-runtime-library/reference/umask.md)<br/>
[Types standard](../c-runtime-library/standard-types.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)