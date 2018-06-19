---
title: Création d’une Application MFC basée sur des formulaires | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfcforms.project
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], forms-based
- forms-based applications [MFC]
ms.assetid: 048d2f7d-b60d-4386-ad8e-71d49af9c05e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a5ee588d7fe90e5bfc39aa8e4ab7a7499b62ad98
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372445"
---
# <a name="creating-a-forms-based-mfc-application"></a>Création d'une application MFC basée sur les formulaires
Un formulaire est une boîte de dialogue avec des contrôles qui permettent à un utilisateur accéder et modifier des données. Vous souhaiterez développer une application dans laquelle l’utilisateur effectue une sélection de formulaires. En règle générale, une application basée sur des formulaires vous permet des formulaires d’accès utilisateur à un clic sur **nouveau** à partir de la **fichier** menu. Une application basée sur une boîte de dialogue, qui ne permet pas aux utilisateurs l’accès à un **nouveau** option dans le **fichier** menu, est considérée également comme une application basée sur des formulaires.  
  
 Une interface monodocument (SDI), une application basée sur les formulaires ne permet qu’une seule instance d’un formulaire spécifique à exécuter à la fois. Il est possible d’exécuter différents formulaires en même temps à partir d’une application SDI formulaires en sélectionnant un nouveau formulaire à partir de la **nouveau** option dans le **fichier** menu.  
  
 Si vous créez une interface multidocument (MDI), une application basée sur des formulaires, l’application sera en mesure de prendre en charge plusieurs instances du même formulaire.  
  
 Si vous créez une application avec prise en charge de plusieurs documents de niveau supérieur, le bureau est le parent implicit du document et le frame du document n’est pas limité à la zone cliente de l’application. Vous pouvez ouvrir plusieurs instances du document, chacun avec ses propres frame, menu et icône de barre des tâches. Vous pouvez également fermer individuellement, les instances suivantes des documents, mais si vous sélectionnez le `Exit` option à partir de la **fichier** menu de l’instance initiale, l’application ferme toutes les instances.  
  
 SDI et MDI avec plusieurs applications de documents de niveau supérieur sont tous les formulaires et utilisent l’architecture document/vue.  
  
 Par définition, toute application basée sur une boîte de dialogue est basée sur les formulaires. Une application basée sur une boîte de dialogue n’utilise pas l’architecture document/vue, donc vous devez gérer les méthodes de création et l’accès pour vos propres formulaires supplémentaires.  
  
 La classe de base pour les applications basées sur le formulaire est [CFormView](../../mfc/reference/cformview-class.md). Si votre application prend en charge de base de données, vous pouvez également sélectionner n’importe quelle classe qui dérive de `CFormView`. Un formulaire est n’importe quelle fenêtre dérivée de `CFormView` ou à partir de n’importe quelle classe qui hérite de `CFormView`.  
  
 Même si vous utilisez une classe de base, telles que [CView](../../mfc/reference/cview-class.md), vous pouvez transformer ultérieurement vos applications basée sur des formulaires par [Ajout d’une classe MFC](../../mfc/reference/adding-an-mfc-class.md) dérivé `CFormView` et en vérifiant la **DocTemplate de générer ressources** case à cocher dans la [Assistant classe MFC](../../mfc/reference/document-template-strings-mfc-add-class-wizard.md).  
  
 Une fois l’Assistant terminé, votre projet s’ouvre, et si vous avez sélectionné `CFormView` (ou une classe qui hérite de `CFormView`) en tant que classe de base ou si vous avez créé une application basée sur une boîte de dialogue, Visual C++ ouvre l’éditeur de boîte de dialogue. À ce stade, vous êtes prêt à concevoir votre premier formulaire.  
  
### <a name="to-begin-creating-a-forms-based-mfc-executable"></a>Pour commencer à créer un exécutable MFC basée sur des formulaires  
  
1.  Suivez les instructions de [création d’une Application MFC](../../mfc/reference/creating-an-mfc-application.md).  
  
2.  Dans l’Assistant Application MFC [Type d’Application](../../mfc/reference/application-type-mfc-application-wizard.md) page, sélectionnez le **prise en charge d’architecture Document/vue** case à cocher.  
  
3.  Sélectionnez **document unique**, **plusieurs documents**, ou **plusieurs documents de niveau supérieur**.  
  
    > [!NOTE]
    >  Si vous avez choisi un SDI, MDI ou application d’interface plusieurs documents de niveau supérieur, par défaut, `CView` est défini comme classe de base pour la vue de votre application dans le [Classes générées](../../mfc/reference/generated-classes-mfc-application-wizard.md) page de l’Assistant. Pour créer une application basée sur les formulaires, vous devez sélectionner `CFormView` en tant que classe de base pour la vue de l’application. Notez que l’Assistant ne fournit aucune prise en charge l’impression pour une application basée sur des formulaires.  
  
4.  Définir d’autres options de projet que vous souhaitez dans les autres pages de l’Assistant.  
  
5.  Cliquez sur **Terminer** pour générer l’application squelette.  
  
 Pour plus d'informations, voir :  
  
-   [Classes d’affichage dérivées](../../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [Alternatives à l’Architecture Document/Vue](../../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [Choix en matière de conception d’applications](../../mfc/application-design-choices.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)   
 [Mode formulaire](../../mfc/form-views-mfc.md)   
 [Création d’une Application MFC de Style Explorateur de fichiers](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)   
 [Création d’une application MFC de style navigateur web](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

