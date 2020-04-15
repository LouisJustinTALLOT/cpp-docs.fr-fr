---
title: Alternatives à l’architecture Document-View
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], applications without
- CDocument class [MFC], space requirements
- views [MFC], applications without
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
ms.openlocfilehash: 41af30d25d7ddb9e2bdbb7a0f7b86cb741ae1048
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370803"
---
# <a name="alternatives-to-the-documentview-architecture"></a>Solutions de remplacement de l'architecture document/vue

Les applications MFC utilisent généralement l'architecture Document/Vue pour gérer les informations, les formats de fichier et la représentation visuelle des données aux utilisateurs. Pour la majorité des applications bureautiques, l'architecture Document/Vue est une architecture d'application appropriée et efficace. Cette architecture sépare les données de visualisation et, dans la plupart des cas, simplifie votre application et réduit le code redondant.

Toutefois, l'architecture Document/Vue n'est pas appropriée dans certains cas. Prenons les exemples suivants :

- Si vous déplacez une application écrite en C pour Windows, vous pouvez avoir envie de compléter votre port avant d'ajouter la prise en charge du document/de la vue à votre application.

- Si vous entrez un utilitaire léger, vous pouvez constater que vous pouvez l'effectuer sans l'architecture Document/Vue.

- Si votre code d'origine combine déjà la gestion des données et l'affichage de données, déplacer du code vers le modèle document/vue n'en vaut pas la peine car vous devez distinguer les deux. Vous pouvez préférer de laisser le code tel quel.

Pour créer une application qui n’utilise pas l’architecture du document/vue, effacez la case de **contrôle de support d’architecture Document/View** à l’étape 1 de l’assistant d’application MFC. Voir [MFC Application Wizard](../mfc/reference/mfc-application-wizard.md) pour plus de détails.

> [!NOTE]
> Les applications basées sur le dialogue produites par le MFC Application Wizard n’utilisent pas l’architecture de document/vue, de sorte que la case à cocher **de support d’architecture Document/View** est désactivée si vous sélectionnez le type d’application de dialogue.

Les assistants Visual C++, ainsi que les éditeurs de boîtes de dialogue, travaillent avec l'application générée comme ils le feraient avec n'importe quelle autre application générée par l'Assistant. L’application peut prendre en charge les barres d’outils, les barres de défilement et une barre d’état, et dispose d’une boîte **About.** Votre application n'enregistre aucun modèle de document et ne contient pas de classe de document.

Notez que votre application générée `CChildView`a `CWnd`une classe de vue, , dérivé de . MFC crée et place une instance de la classe d'affichage dans les fenêtres de frame créées par votre application. MFC s'impose toujours à l'aide d'une fenêtre vue, car elle simplifie la position et la gestion du contenu de l'application. Vous pouvez ajouter un code de peinture au membre `OnPaint` de cette classe. Votre code doit ajouter des barres de défilement à la vue plutôt qu'au frame.

Étant donné que l’architecture Document/Vue fournie par MFC est chargée d’implémenter plusieurs fonctionnalités de base d’une application, l’absence de votre projet signifie que vous êtes chargé d’implémenter plusieurs fonctionnalités importantes de votre application :

- Tel que fourni par l’assistant d’application MFC, le menu de votre application ne contient que des commandes **neuves** et **de sortie** sur le menu **Du fichier.** (La **nouvelle** commande n’est prise en charge que pour les applications MDI, et non pour les applications SDI sans support Document/View.) La ressource générée du menu ne prendra pas en charge une liste MRU (la plus récentement utilisée).

- Vous devez ajouter des fonctions de gestionnaire et des implémentations pour toutes les commandes que votre application prendra en charge, y compris **Open** et **Enregistrer** sur le menu **Fichier.** MFC fournit normalement du code pour prendre en charge ces fonctionnalités, mais cette prise en charge est étroitement liée à l'architecture Document/Vue.

- La barre d'outils de votre application, si vous en avez demandé une, est minimale.

Il est fortement recommandé d'utiliser l'Assistant Application MFC pour créer des applications sans architecture Document/Vue, car il garantit une architecture MFC correcte. Toutefois, si vous devez éviter d'utiliser l'Assistant, voici plusieurs approches pour ignorer l'architecture Document/Vue dans votre code :

- Traitez le document comme une annexe inutilisée et implémentez le code de gestion des données de la classe d'affichage, comme suggéré précédemment. La surcharge du document est relativement basse. Un seul objet [CDocument](../mfc/reference/cdocument-class.md) engage une petite quantité de frais `CDocument`généraux par lui-même, plus les petites surcharges des classes de base de [', CCmdTarget](../mfc/reference/ccmdtarget-class.md) et [CObject](../mfc/reference/cobject-class.md). Les deux dernières classes sont petites.

   Déclaré `CDocument`dans :

  - Deux objets `CString`.

  - Trois **BOOL**s.

  - Un pointeur `CDocTemplate`.

  - Un objet `CPtrList`, qui contient une liste des vues du document.

  En outre, le document requiert la durée nécessaire pour créer l'objet de document, ses objets de vue, une fenêtre frame et un objet modèle de document.

- Traitez à la fois le document et la vue comme des annexes inutilisées. Placez votre code de gestion des données et de dessin dans la fenêtre frame plutôt que dans la vue. Cette approche est plus proche du modèle de programmation en langage C.

- Remplacez les parties de le framework MFC qui créent le document et la vue pour éliminer les créer du tout. Le processus de création de documents commence par un appel à `CWinApp::AddDocTemplate`. Éliminez l'appel de la fonction membre `InitInstance` de la classe d'application et, à la place, créez une fenêtre frame `InitInstance` vous-même. Mettez votre code de gestion des données dans votre classe de fenêtre frame. Le processus de création de documents/vue est illustré dans [Document/View Creation](../mfc/document-view-creation.md). Cette procédure requiert davantage de travail et une connaissance plus approfondie du framework, mais vous libère entièrement de la surcharge de document/vue.

L’article [MFC: Using Database Classes Without Documents and Views](../data/mfc-using-database-classes-without-documents-and-views.md) donne des exemples plus concrets d’alternatives de documents/vues dans le contexte des applications de base de données.

## <a name="see-also"></a>Voir aussi

[Document/Afficher l’architecture](../mfc/document-view-architecture.md)
