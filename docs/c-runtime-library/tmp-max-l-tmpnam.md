---
title: TMP_MAX, L_tmpnam | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- TMP_MAX
- L_tmpnam
dev_langs:
- C++
helpviewer_keywords:
- temporary files, length
- L_tmpnam constant
- TMP_MAX constant
ms.assetid: ab19fd0c-b5b7-49f7-b23d-da9dfbcf0c1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cee175eb7f12952dfe7e30ef79842ee03a96fbb1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019677"
---
# <a name="tmpmax-ltmpnam"></a>TMP_MAX, L_tmpnam

## <a name="syntax"></a>Syntaxe

```
#include <stdio.h>
```

## <a name="remarks"></a>Notes

`TMP_MAX` est le nombre maximal de noms de fichiers uniques que la fonction `tmpnam` peut générer. `L_tmpnam` est la longueur des noms de fichiers temporaires générés par `tmpnam`.

## <a name="see-also"></a>Voir aussi

[Constantes globales](../c-runtime-library/global-constants.md)