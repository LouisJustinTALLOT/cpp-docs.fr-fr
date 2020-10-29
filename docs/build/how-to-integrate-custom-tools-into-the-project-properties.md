---
title: 'Comment : intégrer les outils personnalisés dans les propriétés du projet'
description: Comment intégrer des outils personnalisés dans les propriétés du projet dans les projets C++ Visual Studio.
ms.date: 10/08/2020
helpviewer_keywords:
- 'MSBuild (C++), howto: integrate custom tools'
ms.openlocfilehash: 58626101d54c5b1f9749174e5f3e8938c431d025
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922151"
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>Comment : intégrer les outils personnalisés dans les propriétés du projet

Vous pouvez ajouter des options d’outils personnalisés à la fenêtre **pages de propriétés** de Visual Studio en créant un fichier XML.

La section **Propriétés de configuration** de la fenêtre pages de **Propriétés** de affiche les groupes de paramètres appelés *règles* . Chaque règle contient les paramètres d’un outil ou d’un groupe de fonctionnalités. Par exemple, la règle **Éditeur de liens** contient les paramètres de l’outil Éditeur de liens. Les paramètres d’une règle peuvent être subdivisés en *catégories* .

Vous pouvez créer un fichier de règles qui contient les propriétés de votre outil personnalisé afin que les propriétés soient chargées au démarrage de Visual Studio. Pour plus d’informations sur la modification du fichier, consultez extensibilité de la [plateforme, partie 2](/archive/blogs/vsproject/platform-extensibility-part-2) , sur le blog de l’équipe de projet Visual Studio.

::: moniker range="msvc-140"

Le dossier dans lequel placer votre fichier de règles dépend des paramètres régionaux et de la version de Visual Studio en cours d’utilisation. Dans une invite de commandes développeur Visual Studio 2015 ou version antérieure, le dossier règles est *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\<locale>`* . La `<version>` valeur est *`v140`* dans Visual Studio 2015. `<locale>`Est un LCID, par exemple, `1033` pour l’anglais. Vous utiliserez un chemin d’accès différent pour chaque édition de Visual Studio installée, et pour chaque langue. Par exemple, le chemin d’accès du dossier des règles par défaut pour Visual Studio 2015 Community Edition en anglais peut être *`C:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\v140\1033\`* .

::: moniker-end

::: moniker range="msvc-150"

Le dossier dans lequel placer votre fichier de règles dépend des paramètres régionaux et de la version de Visual Studio en cours d’utilisation. Dans une invite de commandes développeur Visual Studio 2017, le dossier règles est *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\<locale>\`* . `<locale>`Est un LCID, par exemple, `1033` pour l’anglais. Dans une invite de commandes développeur Visual Studio 2015 ou version antérieure, le dossier Rules est *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\<locale>\`* , où la `<version>` valeur se trouve *`v140`* dans Visual Studio 2015. Vous utiliserez un chemin d’accès différent pour chaque édition de Visual Studio installée, et pour chaque langue. Par exemple, le chemin d’accès du dossier des règles par défaut pour Visual Studio 2017 Community Edition en anglais peut être *`C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033\`* .

::: moniker-end

::: moniker range=">=msvc-160"

Le dossier dans lequel placer votre fichier de règles dépend des paramètres régionaux et de la version de Visual Studio en cours d’utilisation. Dans une invite de commandes développeur Visual Studio 2019 ou version ultérieure, le dossier règles est *`%VSINSTALLDIR%MSBuild\Microsoft\VC\<version>\<locale>\`* , où la `<version>` valeur se trouve *`v160`* dans Visual Studio 2019. `<locale>`Est un LCID, par exemple, `1033` pour l’anglais. Dans Visual Studio 2017, le dossier Rules est *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\<locale>\`* . Dans une invite de commandes développeur Visual Studio 2015 ou version antérieure, le dossier règles est *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\<locale>\`* . Vous utiliserez un chemin d’accès différent pour chaque édition de Visual Studio installée, et pour chaque langue. Par exemple, le chemin d’accès du dossier des règles par défaut pour Visual Studio 2019 Community Edition en anglais peut être *`C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\MSBuild\Microsoft\VC\v160\1033\`* .

::: moniker-end

### <a name="to-add-or-change-project-properties"></a>Pour ajouter ou modifier des propriétés de projet

1. Dans l’éditeur XML, créez un fichier XML.

1. Enregistrez le fichier dans le dossier des règles par défaut. Rectifiez le chemin en fonction de vos langue et édition de Visual Studio. Chaque règle figurant dans la fenêtre **Pages de propriétés** est représentée par un fichier XML de ce dossier. Veillez à ce que le fichier ait un nom unique dans le dossier.

1. Copiez le contenu d’un fichier de règles existant, tel que *`rc.xml`* , fermez-le sans enregistrer les modifications, puis collez le contenu dans votre nouveau fichier XML. Vous pouvez copier n’importe quel fichier de schéma XML à utiliser comme modèle. Choisissez une valeur similaire à celle de votre outil.

1. Dans le nouveau fichier XML, modifiez le contenu selon vos besoins. Veillez à modifier **Rule Name** et **Rule.DisplayName** en haut du fichier.

1. Enregistrer vos modifications et fermez le fichier.

1. Les fichiers XML du dossier Rules sont chargés au démarrage de Visual Studio. Pour tester le nouveau fichier, redémarrez Visual Studio.

1. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur un projet, puis choisissez **Propriétés** . Dans la fenêtre **pages de propriétés** , vérifiez qu’il existe un nouveau nœud avec le nom de votre règle.

## <a name="see-also"></a>Voir aussi

[MSBuild sur la ligne de commande-C++](msbuild-visual-cpp.md)
