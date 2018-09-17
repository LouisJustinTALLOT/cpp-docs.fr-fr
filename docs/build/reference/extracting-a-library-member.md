---
title: Extraction d’un membre de bibliothèque | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9207a77868b3257d09f0d9efe38e4765cb8f4906
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726516"
---
# <a name="extracting-a-library-member"></a>Extraction d'un membre de bibliothèque

Vous pouvez utiliser LIB pour créer un fichier objet (.obj) qui contient une copie d’un membre d’une bibliothèque existante. Pour extraire une copie d’un membre, utilisez la syntaxe suivante :

```
LIB library /EXTRACT:member /OUT:objectfile
```

Cette commande crée un fichier .obj appelé *objectfile* qui contient une copie d’un `member` d’un *bibliothèque*. Le `member` nom respecte la casse. Vous pouvez extraire qu’un seul membre dans une seule commande. L’option /OUT est nécessaire ; Il n’existe aucun nom de sortie par défaut. Si un fichier appelé *objectfile* existe déjà dans le répertoire spécifié (ou le répertoire actuel, si aucun répertoire n’est spécifié avec *objectfile*), l’extrait *objectfile*remplace le fichier existant.

## <a name="see-also"></a>Voir aussi

[Référence LIB](../../build/reference/lib-reference.md)