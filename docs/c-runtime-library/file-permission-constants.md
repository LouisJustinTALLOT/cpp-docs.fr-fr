---
description: En savoir plus sur les constantes d’autorisation de fichier
title: Constantes d'autorisations de fichier
ms.date: 11/04/2016
helpviewer_keywords:
- S_IWRITE constant
- constants [C++], file attributes
- S_IREAD constant
- file permissions [C++]
- _S_IWRITE constant
- _S_IREAD constant
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
ms.openlocfilehash: a220ec404202b1f962a4c0bf51d20b7eea2720ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331077"
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
