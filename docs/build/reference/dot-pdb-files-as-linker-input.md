---
title: . Fichiers PDB en tant qu’entrée de l’éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6b728903d2a270efc6b3eb736e45540651dae8c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706184"
---
# <a name="pdb-files-as-linker-input"></a>Fichiers .pdb en tant qu'entrée dans l'éditeur de liens

Objet (.obj) les fichiers compilés à l’aide de l’option/Zi contiennent le nom d’une base de données du programme (PDB). Vous ne spécifiez pas de nom de fichier PDB de l’objet à l’éditeur de liens ; LIEN utilise le nom incorporé pour trouver le fichier PDB s’il est nécessaire. Cela s’applique également aux objets débogables contenus dans une bibliothèque ; le fichier PDB pour une bibliothèque pouvant être débogué doit être disponible pour l’éditeur de liens, ainsi que la bibliothèque.

LIEN utilise également un fichier PDB pour contenir les informations de débogage pour le fichier .exe ou .dll. Le PDB du programme est un fichier de sortie et un fichier d’entrée, car le lien mises à jour le fichier PDB lorsqu’il régénère le programme.

## <a name="see-also"></a>Voir aussi

[Fichiers d’entrée LINK](../../build/reference/link-input-files.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)