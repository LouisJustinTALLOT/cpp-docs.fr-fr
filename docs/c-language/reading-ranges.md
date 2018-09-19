---
title: Lecture des plages | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76530dfdac917dfbde50bc3fb1b17a3c31178729
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030238"
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