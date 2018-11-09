---
title: Lecture des plages
ms.date: 11/04/2016
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
ms.openlocfilehash: b5c6a6baf43b8786fbd0301e4b89ea856d839606
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604105"
---
# <a name="reading-ranges"></a>Lecture des plages

**ANSI 4.9.6.2** L’interprétation d’un tiret (-) qui n’est ni le premier ni le dernier caractère de la scanlist pour la conversion % [ dans la fonction `fscanf`

La ligne suivante

```
fscanf( fileptr, "%[A-Z]", strptr);
```

lit tout nombre de caractères dans la plage A-Z dans la chaîne vers laquelle pointe `strptr`.

## <a name="see-also"></a>Voir aussi

[Fonctions des bibliothèques](../c-language/library-functions.md)