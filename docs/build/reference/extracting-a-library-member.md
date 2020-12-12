---
description: 'En savoir plus sur : extraction d’un membre de bibliothèque'
title: Extraction d'un membre de bibliothèque
ms.date: 11/04/2016
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
ms.openlocfilehash: 8797db6baa08fc36cf288f5b23d73ff730edd973
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192315"
---
# <a name="extracting-a-library-member"></a>Extraction d'un membre de bibliothèque

Vous pouvez utiliser LIB pour créer un fichier objet (. obj) qui contient une copie d’un membre d’une bibliothèque existante. Pour extraire une copie d’un membre, utilisez la syntaxe suivante :

```
LIB library /EXTRACT:member /OUT:objectfile
```

Cette commande crée un fichier. obj appelé *objectfile* qui contient une copie d’une `member` *bibliothèque*. Le `member` nom respecte la casse. Vous ne pouvez extraire qu’un seul membre dans une même commande. L’option/OUT est obligatoire. Il n’y a pas de nom de sortie par défaut. Si un fichier appelé *objectfile* existe déjà dans le répertoire spécifié (ou le répertoire actif, si aucun répertoire n’est spécifié avec *objectfile*), le *objectfile* extrait remplace le fichier existant.

## <a name="see-also"></a>Voir aussi

[Référence LIB](lib-reference.md)
