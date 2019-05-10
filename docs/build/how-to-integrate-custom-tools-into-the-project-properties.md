---
title: 'Procédure : Intégrer des outils personnalisés dans les propriétés du projet'
ms.date: 04/27/2016
helpviewer_keywords:
- 'msbuild (c++), howto: integrate custom tools'
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
ms.openlocfilehash: e9f0758bbb2ab796bd60516ca5d57c605e36fb56
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220687"
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>Procédure : Intégrer des outils personnalisés dans les propriétés du projet

Vous pouvez ajouter des options de l’outil personnalisé à Visual Studio **Pages de propriétés** fenêtre en créant un fichier de schéma XML sous-jacent.

Le **propriétés de Configuration** section de la **Pages de propriétés** fenêtre affiche les groupes de paramètres qui sont appelées *règles*. Chaque règle contient les paramètres d’un outil ou un groupe de fonctionnalités. Par exemple, le **l’éditeur de liens** règle contient les paramètres de l’outil Éditeur de liens. Les paramètres dans une règle peuvent être subdivisés en *catégories*.

Ce document explique comment créer un fichier dans un répertoire de jeu qui contient les propriétés de votre outil personnalisé afin que les propriétés sont chargées au démarrage de Visual Studio. Pour plus d’informations sur la façon de modifier le fichier, consultez [plateforme extensibilité partie 2](https://blogs.msdn.microsoft.com/vsproject/2009/06/18/platform-extensibility-part-2/) sur le blog de l’équipe de projet Visual Studio.

### <a name="to-add-or-change-project-properties"></a>Pour ajouter ou modifier les propriétés du projet

1. Dans l’éditeur XML, créez un fichier XML.

1. Enregistrez le fichier dans Visual Studio 2017 `VCTargets\1033` dossier. Vous aurez un chemin d’accès différents pour chaque édition de Visual Studio 2017 est installé et chaque langue. Par exemple, le chemin d’accès de dossier pour Visual Studio Enterprise edition en anglais est `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`. Ajustez le chemin d’accès pour votre langue et l’édition de Visual Studio. Chaque règle dans le **Pages de propriétés** fenêtre est représentée par un fichier XML dans ce dossier. Assurez-vous que le fichier est nommé identifie de façon unique dans le dossier.

1. Copiez le contenu de `%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml`, fermez-la sans enregistrer les modifications, puis collez le contenu dans votre nouveau fichier XML. Vous pouvez utiliser n’importe quel fichier de schéma XML, il s’agit d’un seul qui peut être utilisé afin de commencer avec un modèle.

1. Dans le nouveau fichier XML, modifiez le contenu selon vos besoins. Veillez à modifier le **nom de la règle** et **Rule.DisplayName** en haut du fichier.

1. Enregistrer les modifications et fermez le fichier.

1. Le code XML des fichiers dans `%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>` sont chargés au démarrage de Visual Studio. Par conséquent, pour tester le nouveau fichier, redémarrez Visual Studio.

1. Dans **l’Explorateur de solutions**, cliquez sur un projet, puis sur **propriétés**. Dans le **Pages de propriétés** fenêtre, dans le volet gauche, vérifiez qu’il existe un nouveau nœud avec le nom de votre règle.

## <a name="see-also"></a>Voir aussi

[MSBuild sur la ligne de commande - C++](msbuild-visual-cpp.md)
