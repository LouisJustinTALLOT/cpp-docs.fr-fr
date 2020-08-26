---
title: 'Comment : intégrer les outils personnalisés dans les propriétés du projet'
ms.date: 05/16/2019
helpviewer_keywords:
- 'msbuild (c++), howto: integrate custom tools'
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
ms.openlocfilehash: 821fb1637306c70d850f12fc1b954860557f47f7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840438"
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>Comment : intégrer les outils personnalisés dans les propriétés du projet

Vous pouvez ajouter des options d’outils personnalisés à la fenêtre **Pages de propriétés** de Visual Studio en créant un fichier de schéma XML sous-jacent.

La section **Propriétés de configuration** de la fenêtre **Pages de propriétés** affiche des groupes de paramètres appelés *règles*. Chaque règle contient les paramètres d’un outil ou d’un groupe de fonctionnalités. Par exemple, la règle **Éditeur de liens** contient les paramètres de l’outil Éditeur de liens. Les paramètres d’une règle peuvent être subdivisés en *catégories*.

Ce document explique comment créer un fichier dans un répertoire défini qui contient les propriétés de votre outil personnalisé de telle sorte que ces propriétés soient chargées au démarrage de Visual Studio. Pour savoir comment modifier le fichier, consultez [Platform Extensibilty Part 2](/archive/blogs/vsproject/platform-extensibility-part-2) sur le blog Visual Studio Project Team.

### <a name="to-add-or-change-project-properties"></a>Pour ajouter ou modifier des propriétés de projet

1. Dans l’éditeur XML, créez un fichier XML.

1. Enregistrez le fichier dans le dossier `VCTargets\1033` de Visual Studio. Le chemin varie selon l’édition de Visual Studio qui est installée et la langue. Par exemple, le chemin du dossier par défaut pour l’édition Community de Visual Studio 2019 en version anglaise est `C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\VC\VCTargets`. Rectifiez le chemin en fonction de vos langue et édition de Visual Studio. Chaque règle figurant dans la fenêtre **Pages de propriétés** est représentée par un fichier XML de ce dossier. Veillez à ce que le fichier ait un nom unique dans le dossier.

1. Copiez le contenu du fichier `%ProgramFiles%\Microsoft Visual Studio\2019\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml` (votre chemin peut être différent), fermez-le sans enregistrer les modifications, puis collez le contenu dans votre nouveau fichier XML. Vous pouvez utiliser n’importe quel fichier de schéma XML. Il doit simplement vous permettre de démarrer avec un modèle.

1. Dans le nouveau fichier XML, modifiez le contenu selon vos besoins. Veillez à modifier **Rule Name** et **Rule.DisplayName** en haut du fichier.

1. Enregistrez les modifications et fermez le fichier.

1. Les fichiers XML contenus dans `%ProgramFiles%\Microsoft Visual Studio\2019\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>` (ou là où vous les avez enregistrés) sont chargés au démarrage de Visual Studio. Par conséquent, pour tester le nouveau fichier, redémarrez Visual Studio.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur un projet, puis cliquez sur **Propriétés**. Dans la fenêtre **Pages de propriétés**, dans le volet gauche, vérifiez qu’il existe un nouveau nœud avec le nom de votre règle.

## <a name="see-also"></a>Voir aussi

[MSBuild sur la ligne de commande-C++](msbuild-visual-cpp.md)
