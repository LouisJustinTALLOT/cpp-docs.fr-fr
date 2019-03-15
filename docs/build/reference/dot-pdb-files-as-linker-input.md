---
title: Fichiers .pdb en tant qu'entrée dans l'éditeur de liens
ms.date: 11/04/2016
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
ms.openlocfilehash: 365f2955f5bc9e8082221a070af454c820c665f1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822508"
---
# <a name="pdb-files-as-linker-input"></a>Fichiers .pdb en tant qu'entrée dans l'éditeur de liens

Objet (.obj) les fichiers compilés à l’aide de l’option/Zi contiennent le nom d’une base de données du programme (PDB). Vous ne spécifiez pas de nom de fichier PDB de l’objet à l’éditeur de liens ; LIEN utilise le nom incorporé pour trouver le fichier PDB s’il est nécessaire. Cela s’applique également aux objets débogables contenus dans une bibliothèque ; le fichier PDB pour une bibliothèque pouvant être débogué doit être disponible pour l’éditeur de liens, ainsi que la bibliothèque.

LIEN utilise également un fichier PDB pour contenir les informations de débogage pour le fichier .exe ou .dll. Le PDB du programme est un fichier de sortie et un fichier d’entrée, car le lien mises à jour le fichier PDB lorsqu’il régénère le programme.

## <a name="see-also"></a>Voir aussi

[Fichiers d’entrée LINK](link-input-files.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
