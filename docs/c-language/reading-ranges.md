---
description: 'En savoir plus sur : lecture des plages'
title: Lecture des plages
ms.date: 11/04/2016
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
ms.openlocfilehash: afb1ff0f25360de7c47663279bf6f54dd7ca6a48
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309119"
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
