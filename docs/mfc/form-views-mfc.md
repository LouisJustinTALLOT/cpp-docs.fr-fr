---
title: Mode Formulaire (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces [MFC], forms
- forms [MFC]
- applications [MFC], forms-based
- forms-based applications [MFC]
- forms [MFC], adding to applications
ms.assetid: efbe73c1-4ca4-4613-aac2-30d916e92c0e
ms.openlocfilehash: 5e8912c9013175fe254b2f4a4a968a67fd071f39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365298"
---
# <a name="form-views-mfc"></a>Mode Formulaire (MFC)

Vous pouvez ajouter des formulaires à n’importe quelle application Visual CMD qui prend en `CFormView`charge les bibliothèques MFC, y compris une application basée sur des [formulaires](../mfc/reference/creating-a-forms-based-mfc-application.md) (dont la classe de vue est dérivée ). Si vous n’avez pas initialement créé votre application pour prendre en charge les formulaires, Visual CMD vous ajoutera ce support lorsque vous insérez un nouveau formulaire. Dans une application SDI ou MDI, qui implémente l’architecture par défaut [du document/vue,](../mfc/document-view-architecture.md)lorsque l’utilisateur choisit la **nouvelle** commande (par défaut, sur le menu **Fichier),** Visual CMD invite l’utilisateur à choisir parmi les formulaires disponibles.

Avec une application SDI, lorsque l’utilisateur choisit la **nouvelle** commande, l’instance actuelle du formulaire continue de s’exécuter, mais une nouvelle instance de l’application avec le formulaire sélectionné est créée si l’on n’est pas trouvé. Dans une application MDI, l’instance actuelle du formulaire continue de s’exécuter lorsque l’utilisateur choisit la **nouvelle** commande.

> [!NOTE]
> Vous pouvez insérer un formulaire dans une application basée sur `CDialog` le dialogue (dont la classe de dialogue est basée sur et une dans laquelle aucune classe de vue n’est implémentée). Toutefois, sans l’architecture du document/vue, Visual CMMD ne met pas automatiquement en œuvre le **Fichier**&#124;**Nouvelles** fonctionnalités. Vous devez créer un moyen pour l’utilisateur d’afficher des formulaires supplémentaires, par exemple en implémentant une boîte de dialogue tabbed avec diverses pages de propriété.

Lorsque vous insérez un nouveau formulaire dans votre application, Visual CMMD fait ce qui suit :

- Crée une classe basée sur l’une des`CFormView`classes `CRecordView` `CDaoRecordView`de `CDialog`forme-style que vous choisissez ( , , , ou ).

- Crée une ressource de dialogue avec des styles appropriés (ou vous pouvez utiliser une ressource de dialogue existante qui n’a pas encore été associée à une classe).

   Si vous choisissez une ressource de dialogue existante, vous devrez peut-être définir ces styles en utilisant la page Propriétés pour la boîte de dialogue. Les styles pour une boîte de dialogue doivent inclure :

     **WS_CHILD**'On

     **WS_BORDER**'Off'

     **WS_VISIBLE**'Off'

     **WS_CAPTION**'Off'

Pour les applications basées sur l’architecture de document/vue, la commande **New Form** (clic droit dans Class View) également :

- Crée `CDocument`une classe basée sur

   Au lieu de créer une nouvelle classe, vous pouvez utiliser n’importe quelle classe existante `CDocument`dans votre projet.

- Génère un modèle de `CDocument`document (dérivé de ) avec des ressources de chaîne, de menu et d’icône.

   Vous pouvez également créer une nouvelle classe sur laquelle fonder le modèle.

- Ajoute un `AddDocumentTemplate` appel dans le `InitInstance` code de votre application.

   Visual CMD ajoute ce code pour chaque nouvelle forme que vous créez, ce qui ajoute le formulaire à la liste des formulaires disponibles lorsque l’utilisateur choisit la **nouvelle** commande. Ce code comprend l’ID de ressources associé du formulaire et les noms des classes de documents, de vue et de cadres associées qui composent ensemble le nouvel objet de formulaire.

   Les modèles de documents servent de connexion entre les documents, les fenêtres d’encadrement et les vues. Pour un seul document, vous pouvez créer de nombreux modèles.

Pour plus d'informations, consultez les pages suivantes :

- [Créer une application basée sur les formulaires](../mfc/reference/creating-a-forms-based-mfc-application.md)

- [Insertion d’un formulaire dans un projet](../mfc/inserting-a-form-into-a-project.md)

## <a name="see-also"></a>Voir aussi

[Éléments d’interface utilisateur](../mfc/user-interface-elements-mfc.md)
