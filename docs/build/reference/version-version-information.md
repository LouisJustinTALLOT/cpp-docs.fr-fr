---
title: /VERSION (Informations de version)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Version
- /version
helpviewer_keywords:
- -VERSION linker option
- Version Information linker option
- version numbers, specifying in .exe
- /VERSION linker option
- VERSION linker option
ms.assetid: b86d0e86-dca6-4316-aee2-d863ccb9f223
ms.openlocfilehash: 709ba836fb537fbcb594f7eb6aa2f2d43df5b4d1
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414705"
---
# <a name="version-version-information"></a>/VERSION (Informations de version)

```
/VERSION:major[.minor]
```

## <a name="arguments"></a>Arguments

*principales* et *mineure*<br/>
Le numéro de version dans l’en-tête du fichier .exe ou .dll.

## <a name="remarks"></a>Notes

L’option /VERSION indique à l’éditeur de liens de placer un numéro de version dans l’en-tête du fichier .exe ou .dll. Utilisez DUMPBIN [/HEADERS](../../build/reference/headers.md) pour afficher le champ de version d’image de OPTIONAL HEADER VALUES pour voir le résultat de.

Le *majeure* et *mineure* arguments sont des nombres décimaux compris entre 0 et 65 535. La valeur par défaut est la version 0.0.

Les informations spécifiées avec l’option /VERSION n’affectent pas les informations de version qui s’affiche pour une application lorsque vous affichez ses propriétés dans l’Explorateur de fichiers. Ces informations proviennent d’un fichier de ressources est utilisé pour générer l’application. Consultez [Éditeur d’informations sur Version](../../windows/version-information-editor.md) pour plus d’informations.

Une autre consiste à insérer un numéro de version avec le [VERSION](../../build/reference/version-c-cpp.md) instruction de définition de module.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **général** page de propriétés.

1. Modifier le **Version** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Version%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)
