---
title: Erreur irrécupérable C1052
ms.date: 05/08/2017
f1_keywords:
- C1052
helpviewer_keywords:
- C1052
ms.assetid: f2c09a2f-d3c1-4420-9501-ffcb65caf87b
ms.openlocfilehash: b381cc3cfe27d4c4a9d744a6b854a0e43727fe71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243667"
---
# <a name="fatal-error-c1052"></a>Erreur irrécupérable C1052

> fichier de base de données de programme, «*filename*», a été généré par l’éditeur de liens avec/Debug : Fastlink ; compilateur ne peut pas mettre à jour ces fichiers PDB ; Veuillez le supprimer ou utilisez /Fd pour spécifier un autre nom de fichier PDB

Le compilateur ne peut pas mettre à jour les fichiers du même programme (PDB) de la base de données qui sont générés par l’éditeur de liens lorsque le [/Debug : Fastlink](../../build/reference/debug-generate-debug-info.md) option est spécifiée. Normalement les fichiers PDB généré par le compilateur et les fichiers PDB généré par l’éditeur de liens ont des noms différents. Toutefois, si elles sont définies pour utiliser les mêmes noms, cette erreur peut résulter.

Pour résoudre ce problème, vous pouvez supprimer explicitement les fichiers PDB avant que vous compilez de nouveau, ou vous pouvez créer des noms différents pour les fichiers PDB généré par le compilateur et généré par l’éditeur de liens.

Pour spécifier le nom de fichier PDB généré par le compilateur sur la ligne de commande, utilisez le [/Fd](../../build/reference/fd-program-database-file-name.md) option du compilateur. Pour spécifier le nom de fichier PDB généré par le compilateur dans l’IDE, ouvrez le **Pages de propriétés** boîte de dialogue pour votre projet et dans le **propriétés de Configuration**, **C/C++**,  **Fichiers de sortie** , définissez le **nom de fichier de base de données de programme** propriété. Par défaut, cette propriété est `$(IntDir)vc$(PlatformToolsetVersion).pdb`.

Vous pouvez également définir le nom de fichier PDB généré par l’éditeur de liens. Pour spécifier le nom de fichier PDB généré par l’éditeur de liens sur la ligne de commande, utilisez le [/PDB](../../build/reference/pdb-use-program-database.md) option de l’éditeur de liens. Pour spécifier le nom de fichier PDB généré par l’éditeur de liens dans l’IDE, ouvrez le **Pages de propriétés** boîte de dialogue pour votre projet et dans le **propriétés de Configuration**, **l’éditeur de liens**,  **Débogage** , définissez le **générer un fichier de base de données de programme** propriété. Par défaut, cette propriété est définie sur `$(OutDir)$(TargetName).pdb`.
