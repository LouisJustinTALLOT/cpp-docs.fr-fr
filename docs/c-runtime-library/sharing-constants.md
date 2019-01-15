---
title: Partage de constantes
ms.date: 11/04/2016
f1_keywords:
- _SH_DENYNO
- _SH_DENYRD
- _SH_DENYRW
- _SH_DENYWR
- _SH_COMPAT
helpviewer_keywords:
- _SH_DENYRW constant
- SH_DENYRD constant
- _SH_COMPAT constant
- _SH_DENYRD constant
- SH_DENYRW constant
- sharing constants
- SH_DENYNO constant
- _SH_DENYWR constant
- SH_DENYWR constant
- _SH_DENYNO constant
- SH_COMPAT constant
ms.assetid: 95fadc3a-55dc-473d-98b5-e8211900465d
ms.openlocfilehash: 5bcebc4f9321ebf3f85bdd757118f779a759fc62
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220515"
---
# <a name="sharing-constants"></a>Partage de constantes

Constantes pour les modes de partage de fichiers.

## <a name="syntax"></a>Syntaxe

```
#include <share.h>
```

## <a name="remarks"></a>Notes

L’argument *shflag* détermine le mode de partage, qui se compose d’une ou plusieurs des constantes manifestes. Elles peuvent être combinées avec les arguments *oflag* (voir [Constantes de fichier](../c-runtime-library/file-constants.md)).

Le tableau suivant répertorie les constantes et leur signification :

|Constante|Signification|
|--------------|-------------|
|`_SH_DENYRW`|Refuse l'accès en lecture et en écriture à un fichier|
|`_SH_DENYWR`|Refuse l'accès en écriture à un fichier|
|`_SH_DENYRD`|Refuse l'accès en lecture à un fichier|
|`_SH_DENYNO`|Autorise l'accès en lecture et en écriture|
|`_SH_SECURE`|Définit le mode sécurisé (lecture partagée, accès en écriture exclusif).|

## <a name="see-also"></a>Voir aussi

[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
