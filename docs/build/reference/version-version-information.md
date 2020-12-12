---
description: En savoir plus sur:/VERSION (informations de version)
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
ms.openlocfilehash: 7c6a27e4829c4acf66db2887e01a147aceb1c5d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176364"
---
# <a name="version-version-information"></a>/VERSION (Informations de version)

```
/VERSION:major[.minor]
```

## <a name="arguments"></a>Arguments

*major* et *Minor*<br/>
Le numéro de version que vous souhaitez dans l’en-tête du fichier. exe ou. dll.

## <a name="remarks"></a>Notes

L’option/VERSION indique à l’éditeur de liens de placer un numéro de version dans l’en-tête du fichier. exe ou. dll. Utilisez DUMPBIN [/headers](headers.md) pour voir le champ version de l’image des valeurs d’en-tête facultatives pour voir l’effet de/version.

Les arguments *major* et *Minor* sont des nombres décimaux compris entre 0 et 65 535. La valeur par défaut est la version 0,0.

Les informations spécifiées avec/VERSION n’affectent pas les informations de version qui s’affichent pour une application lorsque vous affichez ses propriétés dans l’Explorateur de fichiers. Ces informations de version proviennent d’un fichier de ressources qui est utilisé pour générer l’application. Pour plus d’informations, consultez [éditeur d’informations sur la version](../../windows/version-information-editor.md) .

Une autre façon d’insérer un numéro de version consiste à utiliser l’instruction de définition de module [version](version-c-cpp.md) .

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **général** .

1. Modifiez la propriété **version** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Version%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
