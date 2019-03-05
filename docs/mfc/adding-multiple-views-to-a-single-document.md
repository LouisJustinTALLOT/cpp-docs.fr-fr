---
title: Ajout de plusieurs vues à un seul document
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: b665f090fc680221be70f170452d756dd5f68dc5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284279"
---
# <a name="adding-multiple-views-to-a-single-document"></a>Ajout de plusieurs vues à un seul document

Dans une application d’interface monodocument (SDI) créée avec la bibliothèque Microsoft Foundation classes (MFC), chaque type de document est associé à un seul type de vue. Dans certains cas, il est souhaitable d’avoir la possibilité de basculer l’affichage actuel d’un document avec une nouvelle vue.

> [!TIP]
>  Pour obtenir des procédures supplémentaires sur l’implémentation de plusieurs vues pour un seul document, consultez [CDocument::AddView](../mfc/reference/cdocument-class.md#addview) et [collecter](../visual-cpp-samples.md) exemple MFC.

Vous pouvez implémenter cette fonctionnalité en ajoutant une nouvelle `CView`-dérivée de classe et du code supplémentaire pour les vues de commutation dynamiquement à une application MFC existante.

Les étapes sont les suivantes :

- [Modifiez la classe d’Application existante](#vcconmodifyexistingapplicationa1)

- [Créer et modifier la nouvelle classe d’affichage](#vcconnewviewclassa2)

- [Créer et attacher la nouvelle vue](#vcconattachnewviewa3)

- [Implémenter la fonction de commutation](#vcconswitchingfunctiona4)

- [Ajouter la prise en charge pour le basculement de la vue](#vcconswitchingtheviewa5)

Le reste de cette rubrique suppose que les éléments suivants :

- Le nom de la `CWinApp`-objet dérivé est `CMyWinApp`, et `CMyWinApp` est déclaré et défini dans *MYWINAPP. H* et *MYWINAPP. CPP*.

- `CNewView` est le nom du nouveau `CView`-objet, dérivé et `CNewView` est déclaré et défini dans *NEWVIEW. H* et *NEWVIEW. CPP*.

##  <a name="vcconmodifyexistingapplicationa1"></a> Modifiez la classe d’Application existante

Pour basculer entre les vues de l’application, vous devez modifier la classe de l’application en ajoutant des variables membres pour stocker les vues et une méthode pour passer.

Ajoutez le code suivant à la déclaration de `CMyWinApp` dans *MYWINAPP. H*:

[!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

Les nouvelles variables de membre, `m_pOldView` et `m_pNewView`, pointez sur l’affichage actuel et celui nouvellement créé. La nouvelle méthode (`SwitchView`) bascule les vues lorsque demandé par l’utilisateur. Le corps de la méthode est décrite plus loin dans cette rubrique dans [implémenter la fonction de commutation](#vcconswitchingfunctiona4).

La dernière modification à la classe de l’application requiert, y compris un nouveau fichier d’en-tête qui définit un message Windows (**WM_INITIALUPDATE**) qui est utilisé dans la fonction d’échange.

Insérez la ligne suivante dans la section include de *MYWINAPP. CPP*:

[!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

Enregistrez vos modifications et continuer à l’étape suivante.

##  <a name="vcconnewviewclassa2"></a> Créer et modifier la nouvelle classe d’affichage

Création de la nouvelle classe d’affichage est facilitée par l’utilisation du **nouvelle classe** commande disponible à partir de l’affichage de classes. La seule exigence pour cette classe est qu’il dérive `CView`. Ajouter cette nouvelle classe à l’application. Pour obtenir des informations spécifiques sur l’ajout d’une nouvelle classe au projet, consultez [Ajout d’une classe](../ide/adding-a-class-visual-cpp.md).

Une fois que vous avez ajouté la classe au projet, vous devez modifier l’accessibilité de certains membres de classe de vue.

Modifier *NEWVIEW. H* en modifiant le spécificateur d’accès à partir de **protégé** à **public** pour le constructeur et le destructeur. Cela permet à la classe à être créés et détruits de manière dynamique et de modifier l’apparence de la vue avant qu’il soit visible.

Enregistrez vos modifications et continuer à l’étape suivante.

##  <a name="vcconattachnewviewa3"></a> Créer et attacher la nouvelle vue

Pour créer et attacher la nouvelle vue, vous devez modifier le `InitInstance` fonction de votre classe d’application. La modification ajoute le nouveau code qui crée un nouvel objet de vue puis initialise les deux `m_pOldView` et `m_pNewView` avec les deux objets de vue existant.

Étant donné que la nouvelle vue est créée dans le `InitInstance` (fonction), les vues de nouveaux et existants persistent pendant la durée de vie de l’application. Toutefois, l’application pourrait tout aussi facilement créer la nouvelle vue dynamiquement.

Insérez ce code après l’appel à `ProcessShellCommand`:

[!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

Enregistrez vos modifications et continuer à l’étape suivante.

##  <a name="vcconswitchingfunctiona4"></a> Implémenter la fonction de commutation

L’étape précédente, vous avez ajouté le code qui a créé et initialisé un nouvel objet de vue. La dernière étape importante consiste à implémenter la méthode de commutation, `SwitchView`.

À la fin du fichier d’implémentation pour votre classe d’application (*MYWINAPP. CPP*), ajoutez la définition de méthode suivante :

[!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

Enregistrez vos modifications et continuer à l’étape suivante.

##  <a name="vcconswitchingtheviewa5"></a> Ajouter la prise en charge pour le basculement de la vue

La dernière étape consiste à ajouter du code qui appelle le `SwitchView` méthode lors de l’application a besoin basculer entre les vues. Cela est possible de plusieurs façons : en ajoutant un nouvel élément de menu pour l’utilisateur de choisir ou échange interne des vues lorsque certaines conditions sont remplies.

Pour plus d’informations sur l’ajout de nouveaux éléments de menu et les fonctions gestionnaires de commandes, consultez [gestionnaires pour les commandes et les Notifications de contrôle](../mfc/handlers-for-commands-and-control-notifications.md).

## <a name="see-also"></a>Voir aussi

[Architecture document/vue](../mfc/document-view-architecture.md)
