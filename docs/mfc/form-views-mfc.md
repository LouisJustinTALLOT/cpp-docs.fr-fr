---
title: Écran de vues (MFC) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user interfaces [MFC], forms
- forms [MFC]
- applications [MFC], forms-based
- forms-based applications [MFC]
- forms [MFC], adding to applications
ms.assetid: efbe73c1-4ca4-4613-aac2-30d916e92c0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 87775c8afa1fa6eec8fbbdbbaa11bc9b5e6f1faa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349044"
---
# <a name="form-views-mfc"></a>Mode Formulaire (MFC)
Vous pouvez ajouter des formulaires à n’importe quelle application Visual C++ qui prend en charge les bibliothèques MFC, y compris un [application basée sur des formulaires](../mfc/reference/creating-a-forms-based-mfc-application.md) (une classe d’affichage est dérivée de `CFormView`). Si vous n’avez pas initialement votre application pour prendre en charge les formulaires, Visual C++ ajoute cette prise en charge pour vous lorsque vous insérez un nouveau formulaire. Dans une application SDI ou MDI, qui implémente la valeur par défaut [architecture document/vue](../mfc/document-view-architecture.md), lorsque l’utilisateur choisit le `New` commande (par défaut, sur le **fichier** menu), Visual C++ invite l’utilisateur à Choisissez parmi les formulaires disponibles.  
  
 Dans une application SDI, quand l’utilisateur choisit le `New` de commande, l’instance actuelle du formulaire continue de s’exécuter, mais une nouvelle instance de l’application avec le formulaire sélectionné est créée si aucune n’est trouvée. Dans une application MDI, l’instance actuelle du formulaire continue à s’exécuter quand l’utilisateur choisit le `New` commande.  
  
> [!NOTE]
>  Vous pouvez insérer un formulaire dans une application basée sur une boîte de dialogue (celui dont la classe de boîte de dialogue est basée sur `CDialog` et l’autre dans la vue aucune classe est implémentée). Toutefois, sans l’architecture document/vue, Visual C++ n’implémente pas automatiquement le **fichier**&#124;**nouveau** fonctionnalité. Vous devez créer un moyen de l’utilisateur d’afficher des formulaires supplémentaires, comme en implémentant une boîte de dialogue à onglets avec différentes pages de propriétés.  
  
 Lorsque vous insérez un nouveau formulaire dans votre application, Visual C++ effectue les opérations suivantes :  
  
-   Crée une classe basée sur une des classes de style de formulaire que vous choisissez (`CFormView`, `CRecordView`, `CDaoRecordView`, ou `CDialog`).  
  
-   Crée une ressource de boîte de dialogue avec les styles appropriés (ou vous pouvez utiliser une ressource de boîte de dialogue existant qui n’a pas encore été associée à une classe).  
  
     Si vous choisissez une ressource existante de la boîte de dialogue, vous devrez peut-être définir ces styles à l’aide de la page de propriétés pour la boîte de dialogue. Styles d’une boîte de dialogue doivent inclure :  
  
     **WS_CHILD**= On  
  
     `WS_BORDER`= Off  
  
     **WS_VISIBLE**= désactivé  
  
     **WS_CAPTION =** désactivé  
  
 Pour les applications basées sur l’architecture document/vue, le **nouveau formulaire** commande (avec le bouton droit dans l’affichage de classes) également :  
  
-   Crée un **CDocument**-classe de base  
  
     Au lieu de créer une nouvelle classe, vous pouvez utiliser n’importe quel existant **CDocument**-basé sur la classe dans votre projet.  
  
-   Génère un modèle de document (dérivée de **CDocument**) avec des ressources chaîne, menu et icône.  
  
     Vous pouvez également créer une nouvelle classe sur laquelle baser le modèle.  
  
-   Ajoute un appel à **AddDocumentTemplate** dans votre application `InitInstance` code.  
  
     Visual C++ ajoute ce code pour chaque nouveau formulaire que vous créez, ce qui ajoute le formulaire à la liste des formulaires disponibles quand l’utilisateur choisit le `New` commande. Ce code inclut l’ID de ressource associé du formulaire et les noms des classes de frame qui constituent le nouvel objet de formulaire, vue et document associé.  
  
     Modèles de document servent de la connexion entre les documents, fenêtres frame et vues. Pour un seul document, vous pouvez créer plusieurs modèles.  
  
 Pour plus d'informations, voir :  
  
-   [Créer une Application basée sur des formulaires](../mfc/reference/creating-a-forms-based-mfc-application.md)  
  
-   [Insertion d’un formulaire dans un projet](../mfc/inserting-a-form-into-a-project.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments d’Interface utilisateur](../mfc/user-interface-elements-mfc.md)
