---
title: Création d'une application MFC basée sur les formulaires
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfcforms.project
helpviewer_keywords:
- applications [MFC], forms-based
- forms-based applications [MFC]
ms.assetid: 048d2f7d-b60d-4386-ad8e-71d49af9c05e
ms.openlocfilehash: 6810a6c7fce91865a92d048129da29305e22abc1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372325"
---
# <a name="creating-a-forms-based-mfc-application"></a>Création d'une application MFC basée sur les formulaires

Un formulaire est une boîte de dialogue avec les contrôles qui permettent à un utilisateur accéder et modifier des données. Voulez-vous développer une application dans laquelle l’utilisateur sélectionne parmi une sélection de formulaires. En général, une application basée sur les formulaires permet les formulaires d’accès utilisateur par clic **New** à partir de la **fichier** menu. Une application basée sur la boîte de dialogue, qui ne permet pas aux utilisateurs l’accès à un **New** option dans le **fichier** menu, est considérée également comme une application basée sur les formulaires.

Une interface monodocument (SDI), une application basée sur les formulaires ne permet qu’une seule instance d’un formulaire spécifique à exécuter à la fois. Il est possible d’exécuter différents formulaires en même temps à partir d’une application basée sur les formulaires de SDI en sélectionnant un nouveau formulaire à partir de la **New** option dans le **fichier** menu.

Si vous créez une interface multidocument (MDI), une application basée sur les formulaires, l’application sera en mesure de prendre en charge plusieurs instances du même formulaire.

Si vous créez une application avec prise en charge de plusieurs documents de niveau supérieur, le bureau est le parent implicit pour le document et le frame du document n’est pas limité à la zone cliente de l’application. Vous pouvez ouvrir plusieurs instances du document, chacun avec sa propre image, un menu et une icône de barre des tâches. Vous pouvez également fermer individuellement, les instances suivantes des documents, mais si vous sélectionnez le **Exit** option à partir de la **fichier** menu de l’instance initiale, l’application ferme toutes les instances.

SDI et MDI avec plusieurs applications de document de niveau supérieur sont tous les formulaires et utilisent l’architecture document/vue.

N’importe quelle application basée sur la boîte de dialogue, par définition, est basée sur les formulaires. Une application basée sur la boîte de dialogue n’utilise pas l’architecture document/vue, donc vous devez gérer les méthodes de création et l’accès pour vos propres formulaires supplémentaires.

La classe de base pour les applications basées sur le formulaire est [CFormView](../../mfc/reference/cformview-class.md). Si votre application a prise en charge de la base de données, vous pouvez également sélectionner n’importe quelle classe qui dérive de `CFormView`. Un formulaire est n’importe quelle fenêtre dérivé `CFormView` ou à partir de n’importe quelle classe qui hérite de `CFormView`.

Même si vous utilisez une classe de base telles que [CView](../../mfc/reference/cview-class.md), vous pouvez transformer ultérieurement vos applications basée sur les formulaires par [Ajout d’une classe MFC](../../mfc/reference/adding-an-mfc-class.md) dérivé `CFormView` et en vérifiant la **DocTemplate générer ressources** case à cocher dans la [Assistant classe MFC](../../mfc/reference/document-template-strings-mfc-add-class-wizard.md).

Une fois l’Assistant terminé, votre projet s’ouvre, et si vous avez sélectionné `CFormView` (ou une classe qui hérite de `CFormView`) en tant que votre classe de base ou si vous avez créé une application basée sur la boîte de dialogue, Visual C++ ouvre l’éditeur de boîtes de dialogue. À ce stade, vous êtes prêt à concevoir votre premier formulaire.

### <a name="to-begin-creating-a-forms-based-mfc-executable"></a>Pour commencer à créer un exécutable MFC basée sur des formulaires

1. Suivez les instructions de [création d’une Application MFC](../../mfc/reference/creating-an-mfc-application.md).

1. Dans l’Assistant Application MFC [Type d’Application](../../mfc/reference/application-type-mfc-application-wizard.md) page, sélectionnez le **support de l’architecture Document/vue** case à cocher.

1. Sélectionnez **monodocument**, **plusieurs documents**, ou **plusieurs documents de niveau supérieur**.

    > [!NOTE]
    >  Si vous avez choisi un SDI, MDI ou application d’interface multidocument de niveau supérieur, par défaut, `CView` est défini en tant que classe de base pour la vue de votre application dans le [Classes générées](../../mfc/reference/generated-classes-mfc-application-wizard.md) page de l’Assistant. Pour créer une application basée sur les formulaires, vous devez sélectionner `CFormView` en tant que classe de base pour la vue de l’application. Notez que l’Assistant ne fournit aucune prise en charge l’impression pour une application basée sur les formulaires.

1. Définissez d’autres options de projet que vous souhaitez que sur les autres pages de l’Assistant.

1. Cliquez sur **Terminer** pour générer l’application squelette.

Pour plus d'informations, voir :

- [Classes d’affichage dérivées](../../mfc/derived-view-classes-available-in-mfc.md)

- [Alternatives à l’Architecture Document/Vue](../../mfc/alternatives-to-the-document-view-architecture.md)

- [Choix en matière de conception d’applications](../../mfc/application-design-choices.md)

## <a name="see-also"></a>Voir aussi

[Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)<br/>
[Mode formulaire](../../mfc/form-views-mfc.md)<br/>
[Création d’une application MFC de style Explorateur de fichiers](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)<br/>
[Création d’une application MFC de style navigateur web](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)
