---
description: 'En savoir plus sur : erreur irrécupérable C1052'
title: Erreur irrécupérable C1052
ms.date: 05/08/2017
f1_keywords:
- C1052
helpviewer_keywords:
- C1052
ms.assetid: f2c09a2f-d3c1-4420-9501-ffcb65caf87b
ms.openlocfilehash: 818210cc4c3658167de30b9e666c600695389330
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251737"
---
# <a name="fatal-error-c1052"></a>Erreur irrécupérable C1052

> le fichier de base de données du programme, '*nom_fichier*', a été généré par l’éditeur de liens avec/Debug : Fastlink ; le compilateur ne peut pas mettre à jour ces fichiers PDB ; Supprimez-la ou utilisez/FD pour spécifier un autre nom de fichier PDB

Le compilateur ne peut pas mettre à jour les mêmes fichiers de base de données du programme (PDB) qui sont générés par l’éditeur de liens lorsque l’option [/Debug : Fastlink](../../build/reference/debug-generate-debug-info.md) est spécifiée. Normalement, les fichiers PDB générés par le compilateur et les fichiers PDB générés par l’éditeur de liens ont des noms différents. Toutefois, si elles sont configurées pour utiliser les mêmes noms, cette erreur peut se produire.

Pour résoudre ce problème, vous pouvez supprimer explicitement les fichiers PDB avant de compiler à nouveau, ou vous pouvez créer des noms différents pour les fichiers PDB générés par le compilateur et générés par l’éditeur de liens.

Pour spécifier le nom de fichier PDB généré par le compilateur sur la ligne de commande, utilisez l’option de compilateur [/FD](../../build/reference/fd-program-database-file-name.md) . Pour spécifier le nom de fichier PDB généré par le compilateur dans l’IDE, ouvrez la boîte de dialogue **pages de propriétés** de votre projet et, dans la page **Propriétés de configuration**, **C/C++**, **fichiers de sortie** , définissez la propriété **nom de fichier de la base de données du programme** . Par défaut, cette propriété a la valeur `$(IntDir)vc$(PlatformToolsetVersion).pdb` .

Vous pouvez également définir le nom de fichier PDB généré par l’éditeur de liens. Pour spécifier le nom de fichier PDB généré par l’éditeur de liens sur la ligne de commande, utilisez l’option de l’éditeur de liens [/PDB](../../build/reference/pdb-use-program-database.md) . Pour spécifier le nom de fichier PDB généré par l’éditeur de liens dans l’IDE, ouvrez la boîte de dialogue **pages de propriétés** de votre projet et, dans la page **Propriétés de configuration**, éditeur de **liens**, **débogage** , définissez la propriété **générer le fichier de base de données du programme** . Par défaut, cette propriété est définie sur `$(OutDir)$(TargetName).pdb`.
