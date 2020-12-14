---
description: En savoir plus sur:/WINMDFILE (spécifier le fichier winmd)
title: /WINMDFILE (spécifier un fichier winmd)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
ms.openlocfilehash: fd10768c494bbedfbe650e0f0e3e72e8a062cdc1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259017"
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE (spécifier un fichier winmd)

Spécifie le nom de fichier pour le fichier de sortie de métadonnées de Windows Runtime (. winmd) qui est généré par l’option de l’éditeur de liens [/WINMD](winmd-generate-windows-metadata.md) .

```
/WINMDFILE:filename
```

## <a name="remarks"></a>Notes

Utilisez la valeur spécifiée dans `filename` pour remplacer le nom de fichier. winmd par défaut ( `binaryname` . winmd). Notez que vous n’ajoutez pas « . winmd » à `filename` .  Si plusieurs valeurs sont répertoriées sur la ligne de commande **/WINMDFILE** , le dernier est prioritaire.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier de l' **éditeur de liens** .

1. Sélectionnez la page de propriétés **métadonnées Windows** .

1. Dans la zone **fichier de métadonnées Windows** , entrez l’emplacement du fichier.

## <a name="see-also"></a>Voir aussi

[/WINMD (générer les métadonnées Windows)](winmd-generate-windows-metadata.md)<br/>
[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
