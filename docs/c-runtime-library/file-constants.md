---
title: Constantes de fichier
ms.date: 11/04/2016
f1_keywords:
- _O_EXCL
- _O_RDWR
- _O_APPEND
- _O_RDONLY
- _O_TRUNC
- _O_CREAT
- _O_WRONLY
helpviewer_keywords:
- _O_RDWR constant
- O_EXCL constant
- O_RDWR constant
- O_WRONLY constant
- O_APPEND constant
- O_CREAT constant
- _O_CREAT constant
- _O_APPEND constant
- _O_EXCL constant
- O_TRUNC constant
- _O_RDONLY constant
- _O_TRUNC constant
- O_RDONLY constant
- _O_WRONLY constant
ms.assetid: c8fa5548-9ac2-4217-801d-eb45e86f2fa4
ms.openlocfilehash: 2dc473db50b1835d4e1495ce255c0a826563b70a
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220437"
---
# <a name="file-constants"></a>Constantes de fichier

## <a name="syntax"></a>Syntaxe

```
#include <fcntl.h>
```

## <a name="remarks"></a>Notes

L’expression d’entier formée à partir d’une ou plusieurs de ces constantes détermine le type des opérations de lecture ou écriture autorisées. Elle est formée en combinant une ou plusieurs constantes avec une constante de mode de traduction.

Les constantes de fichier sont les suivantes :

|Constante|Description|
|-|-|
| `_O_APPEND`  | Repositionne le pointeur de fichier à la fin du fichier avant chaque opération d'écriture.  |
| `_O_CREAT`  | Crée et ouvre un nouveau fichier pour l’écriture ; cela n’a aucun effet si le fichier spécifié par *filename* existe.  |
| `_O_EXCL`  | Retourne une valeur d'erreur si le fichier spécifié par *filename* existe. S’applique uniquement lors de l’utilisation avec `_O_CREAT`.  |
| `_O_RDONLY`  | Ouvre un fichier en lecture seule ; si cet indicateur est spécifié, ni `_O_RDWR` ni `_O_WRONLY` ne peut être donné.  |
| `_O_RDWR`  | Ouvre le fichier pour la lecture et l’écriture ; si cet indicateur est spécifié, ni `_O_RDONLY` ni `_O_WRONLY` ne peut être donné.  |
| `_O_TRUNC`  | Ouvre un fichier existant et le tronque à une longueur nulle. Le fichier doit disposer d'une autorisation en écriture. Le contenu du fichier est détruit. Si cet indicateur est spécifié, vous ne pouvez pas spécifier `_O_RDONLY`.  |
| `_O_WRONLY`  | Ouvre un fichier en écriture seule ; si cet indicateur est spécifié, ni `_O_RDONLY` ni `_O_RDWR` ne peut être donné.  |

## <a name="see-also"></a>Voir aussi

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
