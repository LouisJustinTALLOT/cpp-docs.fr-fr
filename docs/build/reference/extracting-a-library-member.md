---
title: Extraction d'un membre de bibliothèque
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
ms.openlocfilehash: 4d7629707d99130551401fdda39a972ab2447480
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412885"
---
# <a name="extracting-a-library-member"></a>Extraction d'un membre de bibliothèque

Vous pouvez utiliser LIB pour créer un fichier objet (.obj) qui contient une copie d’un membre d’une bibliothèque existante. Pour extraire une copie d’un membre, utilisez la syntaxe suivante :

```
LIB library /EXTRACT:member /OUT:objectfile
```

Cette commande crée un fichier .obj appelé *objectfile* qui contient une copie d’un `member` d’un *bibliothèque*. Le `member` nom respecte la casse. Vous pouvez extraire qu’un seul membre dans une seule commande. L’option /OUT est nécessaire ; Il n’existe aucun nom de sortie par défaut. Si un fichier appelé *objectfile* existe déjà dans le répertoire spécifié (ou le répertoire actuel, si aucun répertoire n’est spécifié avec *objectfile*), l’extrait *objectfile*remplace le fichier existant.

## <a name="see-also"></a>Voir aussi

[Référence LIB](../../build/reference/lib-reference.md)
