---
title: Mise en forme de la sortie d'une étape de génération personnalisée ou d'un événement de build
ms.date: 08/27/2018
helpviewer_keywords:
- builds [C++], build events
- custom build steps [C++], output format
- events [C++], build
- build events [C++], output format
- build steps [C++], output format
- builds [C++], custom build steps
ms.assetid: 92ad3e38-24d7-4b89-90e6-5a16f5f998da
ms.openlocfilehash: 09bf8485a352d6ec2c1297f8a1be508cb7476c31
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169823"
---
# <a name="formatting-the-output-of-a-custom-build-step-or-build-event"></a>Mise en forme de la sortie d'une étape de génération personnalisée ou d'un événement de build

Si la sortie d’un événement de build ou d’une étape de build personnalisée est correctement mise en forme, les utilisateurs bénéficient des avantages suivants :

- Les avertissements et les erreurs sont comptabilisés dans la fenêtre **Sortie**.

- La sortie apparaît dans la fenêtre **Liste des tâches**.

- Un clic sur la sortie dans la fenêtre **Sortie** permet d’afficher la rubrique appropriée.

- Les opérations F1 sont activées dans la fenêtre **Liste des tâches** ou dans la fenêtre **Sortie**.

La sortie doit avoir le format suivant :

> {<em>filename</em>**(**<em>line #</em> \[ **,** <em>Column #</em>]**)** &#124; *ToolName*} **:** \[ <em>n’importe quel texte</em> ] {**Error** &#124; **Warning**} <em>code + number</em>**:**<em>chaîne</em> \[ localisable <em>n’importe quel texte</em> ]

Où :

- {*a* &#124; *b*} correspond à un choix de *a* ou *b*.

- \[<em>élément</em>] correspond à une chaîne ou un paramètre facultatif.

- L’élément **en gras** est un littéral.

Par exemple :

> C:\\*sourcefile.cpp*(134) : erreur C2143 : erreur de syntaxe : ';' manquant avant '}'
>
> LINK : erreur irrécupérable LNK1104 : impossible d’ouvrir le fichier '*somelib.lib*'

## <a name="see-also"></a>Voir aussi

[Présentation des étapes de génération personnalisée et des événements de build](understanding-custom-build-steps-and-build-events.md)
