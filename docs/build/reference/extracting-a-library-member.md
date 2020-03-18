---
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
ms.openlocfilehash: 874866627099eb5aeb318273db26a976e99bac7f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439878"
---
# <a name="extracting-a-library-member"></a>Extraction d'un membre de bibliothèque

Vous pouvez utiliser LIB pour créer un fichier objet (. obj) qui contient une copie d’un membre d’une bibliothèque existante. Pour extraire une copie d’un membre, utilisez la syntaxe suivante :

```
LIB library /EXTRACT:member /OUT:objectfile
```

Cette commande crée un fichier. obj appelé *objectfile* qui contient une copie d’un `member` d’une *bibliothèque*. Le nom de l' `member` est sensible à la casse. Vous ne pouvez extraire qu’un seul membre dans une même commande. L’option/OUT est obligatoire. Il n’y a pas de nom de sortie par défaut. Si un fichier appelé *objectfile* existe déjà dans le répertoire spécifié (ou le répertoire actif, si aucun répertoire n’est spécifié avec *objectfile*), le *objectfile* extrait remplace le fichier existant.

## <a name="see-also"></a>Voir aussi

[Référence LIB](lib-reference.md)
