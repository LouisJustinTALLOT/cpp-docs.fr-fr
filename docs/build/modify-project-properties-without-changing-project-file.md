---
title: 'Comment : modifier les propriétés et les cibles de projet C++ sans modifier le fichier projet'
ms.date: 11/28/2018
helpviewer_keywords:
- project properties [C++], modifying outside project file
ms.openlocfilehash: a1ba5647542f69cfc7748986e512e74401bfc404
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833359"
---
# <a name="how-to-modify-c-project-properties-and-targets-without-changing-the-project-file"></a>Comment : modifier les propriétés et les cibles de projet C++ sans modifier le fichier projet

Vous pouvez remplacer les propriétés et les cibles de projet à partir de l’invite de commandes MSBuild sans changer le fichier projet. Cela est utile quand vous voulez appliquer certaines propriétés temporairement ou occasionnellement. Vous devez être familiarisé avec MSBuild. Pour plus d’informations, consultez [MSBuild](/visualstudio/msbuild/msbuild).

> [!IMPORTANT]
> Vous pouvez utiliser l’éditeur XML dans Visual Studio, ou n’importe quel éditeur de texte, pour créer le fichier .props ou .targets. N’utilisez pas le **Gestionnaire de propriétés** dans ce scénario, car il ajoute les propriétés au fichier projet.

*Pour remplacer les propriétés de projet :*

1. Créez un fichier .props qui spécifie les propriétés à remplacer.

1. À partir de l’invite de commandes : définissez ForceImportBeforeCppTargets="C:\sources\my_props.props"

*Pour remplacer les cibles de projet :*

1. Créer un fichier .targets avec leur implémentation ou une cible particulière

2. À partir de l’invite de commandes : définissez ForceImportAfterCppTargets ="C:\sources\my_target.targets"

Vous pouvez aussi définir l’option sur la ligne de commande msbuild à l’aide de l’option /p: :

```cmd
> msbuild myproject.sln /p:ForceImportBeforeCppTargets="C:\sources\my_props.props"
> msbuild myproject.sln /p:ForceImportAfterCppTargets="C:\sources\my_target.targets"
```

Quand vous remplacez les propriétés et les cibles de cette façon, c’est comme si vous ajoutiez les importations suivantes à tous les fichiers .vcxproj dans la solution :

```cmd
<Import Project=="C:\sources\my_props.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
<Import Project==" C:\sources\my_target.targets"" />
```
