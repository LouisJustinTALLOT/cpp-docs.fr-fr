---
title: Constantes d’accès fichier en lecture-écriture
ms.date: 11/04/2016
f1_keywords:
- c.constants.file
helpviewer_keywords:
- read/write access constants
- write access constants
- access constants for file read/write
- constants [C++], file attributes
- file read/write access constants
ms.assetid: 56cd1d22-39a5-4fcf-bea2-7046d249e8ee
ms.openlocfilehash: 7bf16271c0d58e3d87e4c24795ec0bd1ee1ccb89
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666172"
---
# <a name="file-readwrite-access-constants"></a>Constantes d'accès fichier en lecture/écriture

## <a name="syntax"></a>Syntaxe

```
#include <stdio.h>
```

## <a name="remarks"></a>Notes

Ces constantes spécifient le type d’accès (« a », « r » ou « w ») demandé pour le fichier. Le [mode de traduction](../c-runtime-library/file-translation-constants.md) (« b » ou « t ») et le [mode commit-to-disk](../c-runtime-library/commit-to-disk-constants.md) (« c » ou « n ») peut tous deux être spécifiés avec le type d’accès.

Les types d’accès sont décrits dans le tableau suivant :

|Type d’accès|Description|
|----------|----------------|
|**"r"**|Ouvre pour l'accès en lecture. Si le fichier n’existe pas ou est introuvable, l’appel pour ouvrir le fichier échoue.|
|**"w"**|Ouvre un fichier vide pour l'accès en écriture. Si le fichier spécifié existe, son contenu est détruit.|
|**"a"**|Ouvre pour l'écriture à la fin du fichier (ajout) ; crée d'abord le fichier s'il n'existe pas. Toutes les opérations d’écriture se produisent à la fin du fichier. Même si le pointeur de fichier peut être repositionné à l’aide de `fseek` ou de `rewind`, il est toujours replacé à la fin du fichier avant toute opération d’écriture. |
|**"r+"**|Ouvre pour l'accès en lecture et en écriture. Si le fichier n’existe pas ou est introuvable, l’appel pour ouvrir le fichier échoue.|
|**"w+"**|Ouvre un fichier vide pour l'accès en lecture et en écriture. Si le fichier spécifié existe, son contenu est détruit.|
|**"a+"**|Comme **"a"**, mais permet aussi la lecture.|

Quand le type d'accès « r+ », « w+ » ou « a+ » est spécifié, la lecture et l'écriture sont autorisées (on dit que le fichier est ouvert pour mise à jour). Cependant, quand vous basculez entre lecture et écriture, une opération intermédiaire `fflush`, `fsetpos`, `fseek` ou `rewind` doit exister. La position actuelle peut être spécifiée pour l'opération `fsetpos` ou `fseek`.

## <a name="see-also"></a>Voir aussi

[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)<br/>
[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)