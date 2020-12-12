---
description: En savoir plus sur :. Fichiers exp en tant qu’entrée dans l’éditeur de liens
title: Fichiers .exp en tant qu'entrée de l'Éditeur de liens
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions
- import libraries, linker files
- linking [C++], exports
- exporting functions, information about exported functions
- exporting data, export (.exp) files
- functions [C++], exporting
- .exp files [C++]
- EXP files
ms.assetid: 399f5636-0a4d-462e-b500-5f5b9ae5ad22
ms.openlocfilehash: 03104d6b4265484e54373484b6c9bbdabf0e1afc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192809"
---
# <a name="exp-files-as-linker-input"></a>Fichiers .exp en tant qu'entrée de l'Éditeur de liens

Les fichiers d’exportation (. exp) contiennent des informations sur les fonctions exportées et les éléments de données. Lorsque LIB crée une bibliothèque d’importation, il crée également un fichier. exp. Vous utilisez le fichier. exp lorsque vous liez un programme que exporte et importe à partir d’un autre programme, directement ou indirectement. Si vous créez un lien avec un fichier. exp, LINK ne produit pas de bibliothèque d’importation, car il suppose que LIB en a déjà créé un. Pour plus d’informations sur les fichiers. exp et les bibliothèques d’importation, consultez [utilisation des bibliothèques d’importation et des fichiers d’exportation](working-with-import-libraries-and-export-files.md).

## <a name="see-also"></a>Voir aussi

[Fichiers d’entrée de lien](link-input-files.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
