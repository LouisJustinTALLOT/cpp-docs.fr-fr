---
description: 'En savoir plus sur : alternatives à l’architecture document/vue'
title: Alternatives à l’architecture Document-View
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], applications without
- CDocument class [MFC], space requirements
- views [MFC], applications without
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
ms.openlocfilehash: 6462a7aabdf52e3ec881f32d68d12128595f2110
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274045"
---
# <a name="alternatives-to-the-documentview-architecture"></a>Solutions de remplacement de l'architecture document/vue

Les applications MFC utilisent généralement l'architecture Document/Vue pour gérer les informations, les formats de fichier et la représentation visuelle des données aux utilisateurs. Pour la majorité des applications bureautiques, l'architecture Document/Vue est une architecture d'application appropriée et efficace. Cette architecture sépare les données de visualisation et, dans la plupart des cas, simplifie votre application et réduit le code redondant.

Toutefois, l'architecture Document/Vue n'est pas appropriée dans certains cas. Prenons les exemples suivants :

- Si vous déplacez une application écrite en C pour Windows, vous pouvez avoir envie de compléter votre port avant d'ajouter la prise en charge du document/de la vue à votre application.

- Si vous entrez un utilitaire léger, vous pouvez constater que vous pouvez l'effectuer sans l'architecture Document/Vue.

- Si votre code d'origine combine déjà la gestion des données et l'affichage de données, déplacer du code vers le modèle document/vue n'en vaut pas la peine car vous devez distinguer les deux. Vous pouvez préférer de laisser le code tel quel.

Pour créer une application qui n’utilise pas l’architecture document/vue, désactivez la case à cocher **prise en charge de l’architecture document/vue** à l’étape 1 de l’Assistant Application MFC. Pour plus d’informations, consultez [Assistant Application MFC](reference/mfc-application-wizard.md) .

> [!NOTE]
> Les applications basées sur des boîtes de dialogue produites par l’Assistant Application MFC n’utilisent pas l’architecture document/vue. la case à cocher **prise en charge de l’architecture document/vue** est donc désactivée si vous sélectionnez le type d’application boîte de dialogue.

Les assistants Visual C++, ainsi que les éditeurs de boîtes de dialogue, travaillent avec l'application générée comme ils le feraient avec n'importe quelle autre application générée par l'Assistant. L’application peut prendre en charge les barres d’outils, les barres de défilement et une barre d’État, et a une zone **à propos** de. Votre application n'enregistre aucun modèle de document et ne contient pas de classe de document.

Notez que votre application générée a une classe d’affichage, `CChildView` , dérivée de `CWnd` . MFC crée et place une instance de la classe d'affichage dans les fenêtres de frame créées par votre application. MFC s'impose toujours à l'aide d'une fenêtre vue, car elle simplifie la position et la gestion du contenu de l'application. Vous pouvez ajouter un code de peinture au membre `OnPaint` de cette classe. Votre code doit ajouter des barres de défilement à la vue plutôt qu'au frame.

Étant donné que l’architecture Document/Vue fournie par MFC est chargée d’implémenter plusieurs fonctionnalités de base d’une application, l’absence de votre projet signifie que vous êtes chargé d’implémenter plusieurs fonctionnalités importantes de votre application :

- Comme fourni par l’Assistant Application MFC, le menu de votre application contient uniquement les commandes **nouveau** et **quitter** dans le menu **fichier** . (La **nouvelle** commande est prise en charge uniquement pour les applications MDI, pas pour les applications SDI sans prise en charge de document/vue.) La ressource de menu générée ne prend pas en charge une liste MRU (récemment utilisée).

- Vous devez ajouter des fonctions de gestionnaire et des implémentations pour toutes les commandes que votre application prendra en charge, y compris **ouvrir** et **Enregistrer** dans le menu **fichier** . MFC fournit normalement du code pour prendre en charge ces fonctionnalités, mais cette prise en charge est étroitement liée à l'architecture Document/Vue.

- La barre d'outils de votre application, si vous en avez demandé une, est minimale.

Il est fortement recommandé d'utiliser l'Assistant Application MFC pour créer des applications sans architecture Document/Vue, car il garantit une architecture MFC correcte. Toutefois, si vous devez éviter d'utiliser l'Assistant, voici plusieurs approches pour ignorer l'architecture Document/Vue dans votre code :

- Traitez le document comme une annexe inutilisée et implémentez le code de gestion des données de la classe d'affichage, comme suggéré précédemment. La surcharge du document est relativement basse. Un seul objet [CDocument](reference/cdocument-class.md) induit une petite surcharge en soi, plus la petite surcharge des classes de `CDocument` base de, [CCmdTarget](reference/ccmdtarget-class.md) et [CObject](reference/cobject-class.md). Les deux dernières classes sont petites.

   Déclaré dans `CDocument` :

  - Deux objets `CString`.

  - Trois **bool** s.

  - Un pointeur `CDocTemplate`.

  - Un objet `CPtrList`, qui contient une liste des vues du document.

  En outre, le document requiert la durée nécessaire pour créer l'objet de document, ses objets de vue, une fenêtre frame et un objet modèle de document.

- Traitez à la fois le document et la vue comme des annexes inutilisées. Placez votre code de gestion des données et de dessin dans la fenêtre frame plutôt que dans la vue. Cette approche est plus proche du modèle de programmation en langage C.

- Remplacez les parties de le framework MFC qui créent le document et la vue pour éliminer les créer du tout. Le processus de création de documents commence par un appel à `CWinApp::AddDocTemplate`. Éliminez l'appel de la fonction membre `InitInstance` de la classe d'application et, à la place, créez une fenêtre frame `InitInstance` vous-même. Mettez votre code de gestion des données dans votre classe de fenêtre frame. Le processus de création de document/vue est illustré dans la création d’un [document/](document-view-creation.md)d’une vue. Cette procédure requiert davantage de travail et une connaissance plus approfondie du framework, mais vous libère entièrement de la surcharge de document/vue.

L’article [MFC : utilisation des classes de base de données sans document ni](../data/mfc-using-database-classes-without-documents-and-views.md) vue fournit des exemples concrets d’alternatives document/vue dans le contexte des applications de base de données.

## <a name="see-also"></a>Voir aussi

[Architecture document/vue](document-view-architecture.md)
