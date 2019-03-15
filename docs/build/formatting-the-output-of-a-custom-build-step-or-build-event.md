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
ms.openlocfilehash: b0e9a7514704742524f97e55c06ef47c7b36631b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825644"
---
# <a name="formatting-the-output-of-a-custom-build-step-or-build-event"></a>Mise en forme de la sortie d'une étape de génération personnalisée ou d'un événement de build

Si la sortie d’un événement de build ou d’une étape de build personnalisée est correctement mise en forme, les utilisateurs bénéficient des avantages suivants :

- Les avertissements et les erreurs sont comptabilisés dans la fenêtre **Sortie**.

- La sortie apparaît dans la fenêtre **Liste des tâches**.

- Un clic sur la sortie dans la fenêtre **Sortie** permet d’afficher la rubrique appropriée.

- Les opérations F1 sont activées dans la fenêtre **Liste des tâches** ou dans la fenêtre **Sortie**.

La sortie doit avoir le format suivant :

> {<em>nomfichier</em>**(**<em>numéroligne</em> \[**,** <em>numérocolonne</em>]**)** &#124; *nomoutil*} **:** \[ <em>texte</em> ] {**error** &#124; **warning**} <em>code+numéro</em>**:**<em>chaîne localisable</em> \[ <em>texte</em> ]

Où :

- {*a* &#124; *b*} correspond à un choix de *a* ou *b*.

- \[<em>élément</em>] correspond à une chaîne ou un paramètre facultatif.

- L’élément **en gras** est un littéral.

Exemple :

> C:\\*sourcefile.cpp*(134) : erreur C2143 : erreur de syntaxe : ';' manquant avant '}'
>
> LINK : erreur irrécupérable LNK1104 : impossible d’ouvrir le fichier '*somelib.lib*'

## <a name="see-also"></a>Voir aussi

[Présentation des étapes de génération personnalisée et des événements de build](understanding-custom-build-steps-and-build-events.md)