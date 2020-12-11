---
description: 'En savoir plus sur : mise en forme de la sortie d’une étape de génération personnalisée ou d’un événement de build'
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
ms.openlocfilehash: c2631e3c6cbd8e66d88527ff75ff7bcac9869b4f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156422"
---
# <a name="formatting-the-output-of-a-custom-build-step-or-build-event"></a>Mise en forme de la sortie d'une étape de génération personnalisée ou d'un événement de build

Si la sortie d’un événement de build ou d’une étape de build personnalisée est correctement mise en forme, les utilisateurs bénéficient des avantages suivants :

- Les avertissements et les erreurs sont comptabilisés dans la fenêtre **Sortie**.

- La sortie apparaît dans la fenêtre **Liste des tâches**.

- Un clic sur la sortie dans la fenêtre **Sortie** permet d’afficher la rubrique appropriée.

- Les opérations F1 sont activées dans la fenêtre **Liste des tâches** ou dans la fenêtre **Sortie**.

La sortie doit avoir le format suivant :

> {<em>filename</em>**(**<em>line #</em> \[ **,** <em>Column #</em>]**)** &#124; *ToolName*} **:** \[ <em>n’importe quel texte</em> ] {**error** &#124; **Warning**} <em>code + nombre</em>**:**<em>chaîne localisable</em> \[ <em>n’importe quel texte</em> ]

Où :

- {*a* &#124; *b*} correspond à un choix de *a* ou *b*.

- \[<em>élément</em>] correspond à une chaîne ou un paramètre facultatif.

- L’élément **en gras** est un littéral.

Par exemple :

> C:\\*sourcefile.cpp*(134) : erreur C2143 : erreur de syntaxe : ';' manquant avant '}'
>
> LINK : erreur irrécupérable LNK1104 : impossible d’ouvrir le fichier '*somelib.lib*'

## <a name="see-also"></a>Voir aussi

[Présentation des étapes de génération personnalisée et des événements de build](understanding-custom-build-steps-and-build-events.md)
