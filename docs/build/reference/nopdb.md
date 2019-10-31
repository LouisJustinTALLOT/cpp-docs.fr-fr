---
title: /NOPDB
description: L’option/NOPDB empêche l’utilitaire DUMPBIN de charger et de rechercher des informations de symboles dans les fichiers PDB.
ms.date: 10/29/2019
f1_keywords:
- /NOPDB
helpviewer_keywords:
- /NOPDB dumpbin option
- /NOPDB
ms.openlocfilehash: 3b745049517888d13de245d4e29be3985c122ada
ms.sourcegitcommit: 6ed1bc5b26dc60a780c1fc5f2f19d57ba1dc47d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73145734"
---
# <a name="nopdb"></a>/NOPDB

Indique à DUMPBIN de ne pas charger et rechercher les fichiers de base de données du programme (PDB) pour les informations de symbole.

## <a name="syntax"></a>Syntaxe

> **/NOPDB**

## <a name="remarks"></a>Notes

Par défaut, DUMPBIN tente de charger des fichiers PDB pour ses fichiers objets, bibliothèques ou exécutables cibles. DUMPBIN utilise ces informations pour faire correspondre les adresses aux noms de symboles. Le processus peut prendre du temps si les fichiers PDB sont volumineux ou s’ils doivent être chargés à partir d’un serveur distant. L’option **/NOPDB** indique à DUMPBIN d’ignorer cette étape. Il affiche uniquement les adresses et les informations de symboles disponibles dans le fichier objet, la bibliothèque ou l’exécutable.

### <a name="to-set-the-nopdb-linker-option-in-visual-studio"></a>Pour définir l’option de l’éditeur de liens/NOPDB dans Visual Studio

1. Ouvrez la boîte de dialogue **pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez **Propriétés de Configuration** > **éditeur de liens** > page de propriétés ligne de **commande** .

1. Dans la zone **options supplémentaires** , ajoutez l’option **/NOPDB** . Cliquez sur **OK** ou sur **appliquer** pour enregistrer vos modifications.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Cette option n’a pas d’équivalent programmatique.

## <a name="see-also"></a>Voir aussi

\ de [ligne de commande DUMPBIN](dumpbin-command-line.md)
[Options DUMPBIN](dumpbin-options.md)\
[Référence DUMPBIN](dumpbin-reference.md)
