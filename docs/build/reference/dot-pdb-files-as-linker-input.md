---
description: En savoir plus sur :. Fichiers PDB en tant qu’entrée dans l’éditeur de liens
title: Fichiers .pdb en tant qu'entrée dans l'éditeur de liens
ms.date: 11/04/2016
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
ms.openlocfilehash: 713d42e7e95b5d1e7e3b1f9be21203b75569cdbe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201155"
---
# <a name="pdb-files-as-linker-input"></a>Fichiers .pdb en tant qu'entrée dans l'éditeur de liens

Les fichiers objets (. obj) compilés à l’aide de l’option/Zi contiennent le nom d’une base de données de programme (PDB). Vous ne spécifiez pas le nom de fichier PDB de l’objet à l’éditeur de liens ; LINK utilise le nom incorporé pour rechercher le fichier PDB, si nécessaire. Cela s’applique également aux objets déboguables contenus dans une bibliothèque. le fichier PDB d’une bibliothèque pouvant être déboguée doit être disponible pour l’éditeur de liens, ainsi que pour la bibliothèque.

LINK utilise également un fichier PDB pour stocker les informations de débogage pour le fichier. exe ou. dll. Le PDB du programme est à la fois un fichier de sortie et un fichier d’entrée, car LINK met à jour le fichier PDB lorsqu’il reconstruit le programme.

## <a name="see-also"></a>Voir aussi

[Fichiers d’entrée de lien](link-input-files.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
