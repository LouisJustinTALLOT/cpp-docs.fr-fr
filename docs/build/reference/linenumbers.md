---
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
ms.openlocfilehash: ea4c3ac2ad582e0fe364f2da26511a66e9dc376c
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2019
ms.locfileid: "57811951"
---
# <a name="linenumbers"></a>/LINENUMBERS

```
/LINENUMBERS
```

## <a name="remarks"></a>Notes

Cette option affiche les numéros de ligne COFF. Numéros de ligne existent dans un fichier objet, s’il a été compilé avec le programme de base de données (/ Zi), Compatible C7 (/ Z7), ou les numéros de ligne uniquement (/Zd). Un fichier exécutable ou une DLL contient des numéros de ligne COFF s’il a été lié avec générer des infos de débogage (/Debug).

Uniquement les [/HEADERS](headers.md) (option DUMPBIN) est disponible pour les fichiers générés avec le [/GL](gl-whole-program-optimization.md) option du compilateur.

## <a name="see-also"></a>Voir aussi

[DUMPBIN, options](dumpbin-options.md)
