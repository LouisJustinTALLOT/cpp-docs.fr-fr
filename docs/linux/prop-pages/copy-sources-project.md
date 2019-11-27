---
title: Copier les sources, propriétés de projet (Linux C++)
ms.date: 10/16/2019
ms.assetid: 1a44230d-5dd8-4d33-93b4-e77e03e00150
ms.openlocfilehash: bc99814e825cda091b6a0b00256ca2d8269ecdd3
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305397"
---
# <a name="copy-sources-project-properties-linux-c"></a>Copier les sources, propriétés de projet (Linux C++)

::: moniker range="vs-2015"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range=">=vs-2017"

Les propriétés définies dans cette page de propriétés s’appliquent à tous les fichiers contenus dans le projet, à l’exception de ceux pour lesquels des propriétés de niveau fichier sont définies.

Propriété | Description
--- | ---
Sources à copier | Spécifie les sources devant être copiées sur le système distant. Tout changement apporté à cette liste peut entraîner un décalage ou des répercussions dans la structure des répertoires où sont copiés les fichiers sur le système distant.
Copier les sources | Spécifie si les sources doivent être copiées sur le système distant.
Sources supplémentaires à copier | Spécifie les sources supplémentaires à copier sur le système distant. Vous pouvez éventuellement fournir la liste sous forme de paires de mappage entre l’emplacement local et l’emplacement distant en utilisant la syntaxe suivante : fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, où un fichier local peut être copié vers l’emplacement distant spécifié sur le système distant.

@SourcesToCopyRemotely et @DataFilesToCopyRemotely font référence à des groupes d’éléments dans le fichier projet. Pour modifier les sources ou les fichiers de données qui sont copiés à distance, modifiez le fichier *vcxproj* de la façon suivante :

```xml
<ItemGroup>
   <MyItems Include="foo.txt" />
   <MyItems Include="bar.txt" />
   <DataFilesToCopyRemotely Include="@(MyItems)" />
</ItemGroup>
```

::: moniker-end
