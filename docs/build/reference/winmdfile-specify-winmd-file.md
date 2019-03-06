---
title: /WINMDFILE (spécifier un fichier winmd)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
ms.openlocfilehash: 5532046f4284100c60bb82c12b4d47c721fc275e
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413080"
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE (spécifier un fichier winmd)

Spécifie le nom de fichier pour le fichier de sortie de métadonnées du Runtime Windows (.winmd) qui est généré par le [/WINMD](../../build/reference/winmd-generate-windows-metadata.md) option de l’éditeur de liens.

```
/WINMDFILE:filename
```

## <a name="remarks"></a>Notes

Utilisez la valeur spécifiée dans `filename` pour remplacer le nom de fichier .winmd par défaut (`binaryname`.winmd). Notez que vous n’ajoutez pas de « .winmd » au `filename`.  Si plusieurs valeurs sont répertoriés sur le **/WINMDFILE** ligne de commande, le dernier est prioritaire.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **l’éditeur de liens** dossier.

1. Sélectionnez le **Windows métadonnées** page de propriétés.

1. Dans le **fichier de métadonnées Windows** , entrez l’emplacement du fichier.

## <a name="see-also"></a>Voir aussi

[/WINMD (Générer des métadonnées Windows)](../../build/reference/winmd-generate-windows-metadata.md)<br/>
[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)
