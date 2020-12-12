---
description: 'En savoir plus sur : vues de formulaire (MFC)'
title: Mode Formulaire (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces [MFC], forms
- forms [MFC]
- applications [MFC], forms-based
- forms-based applications [MFC]
- forms [MFC], adding to applications
ms.assetid: efbe73c1-4ca4-4613-aac2-30d916e92c0e
ms.openlocfilehash: be0853c46509e92d758b38e6a3b7fbd993e9b700
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180359"
---
# <a name="form-views-mfc"></a>Mode Formulaire (MFC)

Vous pouvez ajouter des formulaires à n’importe quel Visual C++ application qui prend en charge les bibliothèques MFC, y compris une [application basée sur les formulaires](reference/creating-a-forms-based-mfc-application.md) (dont la classe de vue est dérivée de `CFormView` ). Si vous n’avez pas initialement créé votre application pour prendre en charge les formulaires, Visual C++ ajouterez cette prise en charge lorsque vous insérerez un nouveau formulaire. Dans une application SDI ou MDI, qui implémente l' [architecture document/vue](document-view-architecture.md)par défaut, quand l’utilisateur choisit la **nouvelle** commande (par défaut, dans le menu **fichier** ), Visual C++ invite l’utilisateur à choisir parmi les formulaires disponibles.

Avec une application SDI, lorsque l’utilisateur choisit la **nouvelle** commande, l’instance actuelle du formulaire continue à s’exécuter, mais une nouvelle instance de l’application avec le formulaire sélectionné est créée si aucune n’est trouvée. Dans une application MDI, l’instance actuelle du formulaire continue à s’exécuter lorsque l’utilisateur choisit la **nouvelle** commande.

> [!NOTE]
> Vous pouvez insérer un formulaire dans une application basée sur une boîte de dialogue (dont la classe de boîte de dialogue est basée sur `CDialog` et dans laquelle aucune classe d’affichage n’est implémentée). Toutefois, sans l’architecture document/vue, Visual C++ n’implémente pas automatiquement le **fichier**&#124;**nouvelle** fonctionnalité. Vous devez créer une méthode permettant à l’utilisateur d’afficher des formulaires supplémentaires, par exemple en implémentant une boîte de dialogue à onglets avec diverses pages de propriétés.

Lorsque vous insérez un nouveau formulaire dans votre application, Visual C++ effectue les opérations suivantes :

- Crée une classe basée sur l’une des classes de style de formulaire que vous choisissez ( `CFormView` , `CRecordView` , `CDaoRecordView` ou `CDialog` ).

- Crée une ressource de boîte de dialogue avec les styles appropriés (ou vous pouvez utiliser une ressource de boîte de dialogue existante qui n’a pas encore été associée à une classe).

   Si vous choisissez une ressource de boîte de dialogue existante, vous devrez peut-être définir ces styles à l’aide de la page Propriétés de la boîte de dialogue. Les styles d’une boîte de dialogue doivent inclure :

     **WS_CHILD**= on

     **WS_BORDER**= désactivé

     **WS_VISIBLE**= désactivé

     **WS_CAPTION**= désactivé

Pour les applications basées sur l’architecture document/vue, la commande **nouveau formulaire** (cliquez avec le bouton droit dans affichage de classes) également :

- Crée une `CDocument` classe basée sur

   Au lieu d’avoir créé une nouvelle classe, vous pouvez utiliser n’importe quelle `CDocument` classe existante de votre projet.

- Génère un modèle de document (dérivé de `CDocument` ) avec des ressources de chaîne, de menu et d’icône.

   Vous pouvez également créer une classe sur laquelle baser le modèle.

- Ajoute un appel à `AddDocumentTemplate` dans le code de votre application `InitInstance` .

   Visual C++ ajoute ce code pour chaque nouveau formulaire que vous créez, qui ajoute le formulaire à la liste des formulaires disponibles lorsque l’utilisateur choisit la **nouvelle** commande. Ce code comprend l’ID de ressource associé au formulaire et les noms des classes de document, de vue et de frame associées qui forment le nouvel objet de formulaire.

   Les modèles de document servent de connexion entre les documents, les fenêtres Frame et les vues. Pour un document unique, vous pouvez créer de nombreux modèles.

Pour plus d'informations, consultez les pages suivantes :

- [Créer une application Forms-Based](reference/creating-a-forms-based-mfc-application.md)

- [Insertion d’un formulaire dans un projet](inserting-a-form-into-a-project.md)

## <a name="see-also"></a>Voir aussi

[Éléments de l’interface utilisateur](user-interface-elements-mfc.md)
