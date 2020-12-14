---
description: En savoir plus sur:/LINENUMBERS
title: /LINENUMBERS
ms.date: 11/04/2016
f1_keywords:
- /linenumbers
helpviewer_keywords:
- LINENUMBERS dumpbin option
- line numbers
- -LINENUMBERS dumpbin option
- /LINENUMBERS dumpbin option
ms.assetid: 1681d582-2c2f-484e-9920-109959549055
ms.openlocfilehash: 9df3d88476a82466f86ec23147c9f8f35f9b3f1d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191015"
---
# <a name="linenumbers"></a>/LINENUMBERS

```
/LINENUMBERS
```

## <a name="remarks"></a>Notes

Cette option affiche les numéros de ligne COFF. Les numéros de ligne existent dans un fichier objet s’il a été compilé avec la base de données du programme (/ZI), compatible C7 (/Z7) ou les numéros de ligne uniquement (/ZD). Un fichier exécutable ou une DLL contient des numéros de ligne COFF s’il a été lié avec générer des informations de débogage (/DEBUG).

Seule l’option [/HEADERS](headers.md) DUMPBIN peut être utilisée sur les fichiers générés avec l’option du compilateur [/GL](gl-whole-program-optimization.md).

## <a name="see-also"></a>Voir aussi

[Options DUMPBIN](dumpbin-options.md)
