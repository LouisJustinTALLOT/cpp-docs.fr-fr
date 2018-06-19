---
title: Erreur irrécupérable C1052 | Documents Microsoft
ms.custom: ''
ms.date: 05/08/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1052
dev_langs:
- C++
helpviewer_keywords:
- C1052
ms.assetid: f2c09a2f-d3c1-4420-9501-ffcb65caf87b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8d272b71a527763245ccf7c8d69bd11a915eab7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225851"
---
# <a name="fatal-error-c1052"></a>Erreur irrécupérable C1052

> fichier de base de données de programme, «*nom de fichier*', a été généré par l’éditeur de liens avec/Debug : Fastlink ; compilateur ne peut pas mettre à jour ces fichiers PDB ; supprimez-le ou utilisez /Fd pour spécifier un autre nom de fichier PDB

Le compilateur ne peut pas mettre à jour les fichiers du même programme (PDB) de la base de données qui sont générés par l’éditeur de liens lors de la [/Debug : Fastlink](../../build/reference/debug-generate-debug-info.md) option est spécifiée. Normalement les fichiers PDB généré par le compilateur et les fichiers PDB généré par l’éditeur de liens ont des noms différents. Toutefois, s’ils sont définis pour utiliser les mêmes noms, cette erreur peut résulter.

Pour résoudre ce problème, vous pouvez supprimer les fichiers PDB explicitement avant que vous compilez à nouveau, ou vous pouvez créer des noms différents pour les fichiers PDB généré par le compilateur et générées par l’éditeur de liens.

Pour spécifier le nom de fichier PDB généré par le compilateur sur la ligne de commande, utilisez le [/Fd](../../build/reference/fd-program-database-file-name.md) option du compilateur. Pour spécifier le nom de fichier PDB généré par le compilateur dans l’IDE, ouvrez le **Pages de propriétés** boîte de dialogue pour votre projet et dans le **propriétés de Configuration**, **C/C++**,  **Fichiers de sortie** , définissez le **nom de fichier de base de données de programme** propriété. Par défaut, cette propriété est `$(IntDir)vc$(PlatformToolsetVersion).pdb`.

Vous pouvez également définir le nom de fichier PDB généré par l’éditeur de liens. Pour spécifier le nom de fichier PDB généré par l’éditeur de liens sur la ligne de commande, utilisez le [/PDB](../../build/reference/pdb-use-program-database.md) option de l’éditeur de liens. Pour spécifier le nom de fichier PDB généré par l’éditeur de liens dans l’IDE, ouvrez le **Pages de propriétés** boîte de dialogue pour votre projet et dans le **propriétés de Configuration**, **l’éditeur de liens**,  **Débogage** , définissez le **générer un fichier de base de données de programme** propriété. Par défaut, cette propriété est définie `$(OutDir)$(TargetName).pdb`.
