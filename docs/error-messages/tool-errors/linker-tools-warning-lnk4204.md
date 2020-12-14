---
description: 'En savoir plus sur les éléments suivants : avertissement des outils Éditeur de liens LNK4204'
title: Avertissement des outils Éditeur de liens LNK4204
ms.date: 11/04/2016
f1_keywords:
- LNK4204
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
ms.openlocfilehash: e0e61967a7b3bf42eb2c084d73c7c0aa9485c47e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294195"
---
# <a name="linker-tools-warning-lnk4204"></a>Avertissement des outils Éditeur de liens LNK4204

'NomFichier’ne contient pas d’informations de débogage pour le module de référencement ; liaison de l’objet comme si aucune information de débogage

Le fichier. pdb comporte une signature erronée. L’éditeur de liens continue à lier l’objet sans informations de débogage. Vous souhaiterez peut-être recompiler le fichier objet à l’aide de l’option [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) .

LNK4204 peut se produire si certains des objets de la bibliothèque font référence à un fichier qui n’existe plus. Cela peut se produire lors de la reconstruction de la solution, par exemple ; un fichier objet peut être supprimé et ne peut pas être reconstruit en raison d’une erreur de compilation. Dans ce cas, compilez avec **/Z7**, ou **/FD**, pour mettre à jour les objets afin qu’ils fassent référence à un seul fichier par bibliothèque (qui n’est pas le nom de fichier. pdb par défaut).  Pour plus d’informations, consultez l’article [/Fd (Nom de fichier PDB)](../../build/reference/fd-program-database-file-name.md).  Assurez-vous que le fichier. pdb est enregistré avec la bibliothèque chaque fois qu’il est mis à jour dans le système de contrôle de code source.
