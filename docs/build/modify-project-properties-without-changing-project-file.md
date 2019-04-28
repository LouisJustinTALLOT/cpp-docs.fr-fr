---
title: 'Procédure : Modifier les propriétés du projet C++ et les cibles sans modifier le fichier de projet'
ms.date: 11/28/2018
helpviewer_keywords:
- project properties [C++], modifying outside project file
ms.openlocfilehash: ad527d8ee69a1786be7d325571f9c9ac4f9a8574
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273337"
---
# <a name="how-to-modify-c-project-properties-and-targets-without-changing-the-project-file"></a>Procédure : Modifier les propriétés du projet C++ et les cibles sans modifier le fichier de projet

Vous pouvez remplacer les propriétés et les cibles de projet à partir de l’invite de commandes MSBuild sans changer le fichier projet. Cela est utile quand vous voulez appliquer certaines propriétés temporairement ou occasionnellement. Vous devez être familiarisé avec MSBuild. Pour plus d’informations, consultez [MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild).

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
