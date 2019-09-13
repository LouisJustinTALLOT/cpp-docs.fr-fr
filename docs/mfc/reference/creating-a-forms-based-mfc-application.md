---
title: Création d'une application MFC basée sur les formulaires
ms.date: 09/09/2019
f1_keywords:
- vc.appwiz.mfcforms.project
helpviewer_keywords:
- applications [MFC], forms-based
- forms-based applications [MFC]
ms.assetid: 048d2f7d-b60d-4386-ad8e-71d49af9c05e
ms.openlocfilehash: 1dbbc5c29f85ced846cb3e07a02a5d6a55c94b20
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908054"
---
# <a name="creating-a-forms-based-mfc-application"></a>Création d'une application MFC basée sur les formulaires

Un formulaire est une boîte de dialogue avec des contrôles qui permettent à un utilisateur d’accéder aux données et éventuellement de les modifier. Vous pouvez développer une application dans laquelle l’utilisateur sélectionne dans une sélection de formulaires. En règle générale, une application basée sur les formulaires permet à l’utilisateur d’accéder aux formulaires en cliquant sur **nouveau** dans le menu **fichier** . Une application basée sur des boîtes de dialogue, qui n’autorise pas les utilisateurs à accéder à une **nouvelle** option dans le menu **fichier** , est également considérée comme une application basée sur les formulaires.

Une application SDI (single document interface), basée sur des formulaires, permet à une seule instance d’un formulaire particulier de s’exécuter à la fois. Il est possible d’exécuter des formulaires différents en même temps à partir d’une application basée sur les formulaires SDI en sélectionnant un nouveau formulaire à partir de la **nouvelle** option dans le menu **fichier** .

Si vous créez une application MDI (multiple document interface), l’application est en mesure de prendre en charge plusieurs instances du même formulaire.

Si vous créez une application avec une prise en charge de documents de niveau supérieur, le bureau est le parent implicite pour le document et le frame du document n’est pas limité à la zone cliente de l’application. Vous pouvez ouvrir plusieurs instances du document, chacune avec ses propres icône de cadre, de menu et de barre des tâches. Vous pouvez fermer individuellement des instances de documents suivantes, mais si vous sélectionnez l’option **quitter** dans le menu **fichier** de l’instance initiale, l’application ferme toutes les instances.

SDI, MDI et plusieurs applications de document de niveau supérieur sont tous des formulaires basés sur l’architecture document/vue.

Une application basée sur des boîtes de dialogue, par définition, est basée sur les formulaires. Une application basée sur des boîtes de dialogue n’utilise pas l’architecture document/vue. vous devez donc gérer les méthodes de création et d’accès pour vos propres formulaires supplémentaires.

La classe de base pour les applications basées sur les formulaires est [CFormView](cformview-class.md). Si votre application prend en charge les bases de données, vous pouvez également sélectionner une classe qui `CFormView`dérive de. Un formulaire est une fenêtre dérivée `CFormView` de ou de n’importe quelle classe qui `CFormView`hérite de.

Même si vous utilisez une classe de base telle que [CView](cview-class.md), vous pouvez ultérieurement rendre vos applications basées sur les formulaires en [ajoutant une classe MFC](adding-an-mfc-class.md) dérivée de `CFormView`.

Une fois que vous avez terminé avec l’Assistant, votre projet s’ouvre et `CFormView` , si vous avez sélectionné (ou une `CFormView`classe qui hérite de) comme classe de base ou si vous avez créé une C++ application basée sur des boîtes de dialogue, le visuel ouvre l’éditeur de boîtes de dialogue. À ce stade, vous êtes prêt à concevoir votre premier formulaire.

### <a name="to-begin-creating-a-forms-based-mfc-executable"></a>Pour commencer à créer un exécutable MFC basé sur des formulaires

1. Suivez les instructions de [création d’une application MFC](creating-an-mfc-application.md) pour une application MFC basée sur les formulaires.

1. Dans la page type d' [application](application-type-mfc-application-wizard.md) de l’Assistant Application MFC, activez la case à cocher **prise en charge de l’architecture document/vue** .

1. Sélectionnez **un document unique**, **plusieurs documents**ou **plusieurs documents de niveau supérieur**.

    > [!NOTE]
    >  Si vous avez choisi une application SDI, MDI ou d’interface de document de niveau supérieur, par défaut `CView` , est définie en tant que classe de base pour l’affichage de votre application dans la page [classes générées](generated-classes-mfc-application-wizard.md) de l’Assistant. Pour créer une application basée sur les formulaires, vous devez `CFormView` sélectionner comme classe de base pour l’affichage de l’application. Notez que l’Assistant ne prend pas en charge l’impression pour une application basée sur les formulaires.

1. Définissez les autres options de projet de votre choix dans les autres pages de l’Assistant.

1. Cliquez sur **Terminer** pour générer l’application squelette.

Pour plus d'informations, voir :

- [Classes d’affichage dérivées](../derived-view-classes-available-in-mfc.md)

- [Alternatives à l’architecture document/vue](../alternatives-to-the-document-view-architecture.md)

- [Choix en matière de conception d’applications](../application-design-choices.md)

## <a name="see-also"></a>Voir aussi

[Assistant Application MFC](mfc-application-wizard.md)<br/>
[Modes formulaire](../form-views-mfc.md)<br/>
[Création d’une application MFC de style Explorateur de fichiers](creating-a-file-explorer-style-mfc-application.md)<br/>
[Création d’une application MFC de style navigateur web](creating-a-web-browser-style-mfc-application.md)
