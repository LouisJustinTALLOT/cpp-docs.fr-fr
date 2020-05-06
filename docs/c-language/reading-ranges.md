---
title: Lecture des plages
ms.date: 11/04/2016
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
ms.openlocfilehash: 86bb24647084d8bdc452960bab631587c2413276
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64343150"
---
# <a name="reading-ranges"></a>Lecture des plages

**ANSI 4.9.6.2** L’interprétation d’un tiret (-) qui n’est ni le premier ni le dernier caractère de la scanlist pour la conversion % [ dans la fonction `fscanf`

La ligne suivante

```
fscanf( fileptr, "%[A-Z]", strptr);
```

lit tout nombre de caractères dans la plage A-Z dans la chaîne vers laquelle pointe `strptr`.

## <a name="see-also"></a>Voir aussi

[Fonctions de la bibliothèque](../c-language/library-functions.md)
