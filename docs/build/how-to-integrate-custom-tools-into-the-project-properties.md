---
title: 'Comment : intégrer les outils personnalisés dans les propriétés du projet | Documents Microsoft'
ms.custom: ''
ms.date: 04/27/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.howto.integratecustomtools
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: integrate custom tools'
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 00482aa2b4b700d15e46d0741e76dd17afc28419
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368900"
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>Comment : intégrer les outils personnalisés dans les propriétés du projet
Vous pouvez ajouter des options de l’outil personnalisé pour Visual Studio **Pages de propriétés** fenêtre en créant un fichier de schéma XML sous-jacent.  
  
 Le **propriétés de Configuration** section de la **Pages de propriétés** fenêtre affiche les groupes de paramètres qui sont appelées *règles*. Chaque règle contient les paramètres d’un outil ou d’un groupe de fonctionnalités. Par exemple, le **l’éditeur de liens** règle contient les paramètres de l’outil de l’éditeur de liens. Les paramètres dans une règle peuvent être subdivisées en *catégories*.  
  
 Ce document explique comment créer un fichier dans un répertoire de jeu qui contient les propriétés de votre outil personnalisé afin que les propriétés sont chargées au démarrage de Visual Studio. Pour plus d’informations sur la façon de modifier le fichier, consultez [plateforme extensibilité partie 2](http://go.microsoft.com/fwlink/p/?linkid=191489) sur le blog de l’équipe de projet Visual Studio.  
  
### <a name="to-add-or-change-project-properties"></a>Pour ajouter ou modifier les propriétés du projet  
  
1.  Dans l’éditeur XML, créez un fichier XML.  
  
2.  Enregistrez le fichier dans le 2017 Visual Studio `VCTargets\1033` dossier. Vous aurez un autre chemin d’accès pour chaque édition de Visual 2017 Studio qui est installé et pour chaque langue. Par exemple, le chemin d’accès de dossier pour Visual Studio Enterprise edition en anglais est `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`. Ajustez le chemin d’accès pour votre langue et l’édition de Visual Studio. Chaque règle de la **Pages de propriétés** fenêtre est représentée par un fichier XML dans ce dossier. Assurez-vous que le fichier est nommé de manière unique dans le dossier.  
  
3.  Copiez le contenu de `%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml`, fermez-la sans enregistrer les modifications, puis collez le contenu dans votre nouveau fichier XML. Vous pouvez utiliser n’importe quel fichier de schéma XML - il s’agit d’un seul qui peut être utilisé afin de commencer avec un modèle.  
  
4.  Dans le nouveau fichier XML, modifiez le contenu en fonction de vos besoins. Veillez à modifier le **nom de la règle** et **Rule.DisplayName** en haut du fichier.  
  
5.  Enregistrer les modifications et fermez le fichier.  
  
6.  Le code XML dans les fichiers `%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>` sont chargés au démarrage de Visual Studio. Par conséquent, pour tester le nouveau fichier, redémarrez Visual Studio.  
  
7.  Dans **l’Explorateur de solutions**, avec le bouton droit à un projet, puis sur **propriétés**. Dans le **Pages de propriétés** fenêtre, dans le volet gauche, vérifiez qu’il existe un nouveau nœud avec le nom de votre règle.  
  
## <a name="see-also"></a>Voir aussi  
 [MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
