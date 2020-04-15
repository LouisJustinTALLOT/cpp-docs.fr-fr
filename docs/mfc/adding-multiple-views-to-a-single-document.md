---
title: Ajout de plusieurs vues à un seul document
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: 4fa39a4d9369c84d2cffdaeff28dc9cb2f966b31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370867"
---
# <a name="adding-multiple-views-to-a-single-document"></a>Ajout de plusieurs vues à un seul document

Dans une application d’interface à un seul document (SDI) créée avec la bibliothèque Microsoft Foundation Class (MFC), chaque type de document est associé à un type de vue unique. Dans certains cas, il est souhaitable d’avoir la capacité de changer la vue actuelle d’un document avec une nouvelle vue.

> [!TIP]
> Pour des procédures supplémentaires sur la mise en œuvre de plusieurs vues pour un seul document, voir [CDocument:AddView](../mfc/reference/cdocument-class.md#addview) et [l’échantillon COLLECT](../overview/visual-cpp-samples.md) MFC.

Vous pouvez implémenter cette `CView`fonctionnalité en ajoutant une nouvelle classe dérivée et un code supplémentaire pour passer les vues dynamiquement à une application MFC existante.

La procédure comporte trois étapes :

- [Modifier la catégorie d’application existante](#vcconmodifyexistingapplicationa1)

- [Créer et modifier la nouvelle classe de vue](#vcconnewviewclassa2)

- [Créer et joindre la nouvelle vue](#vcconattachnewviewa3)

- [Mettre en œuvre la fonction de commutation](#vcconswitchingfunctiona4)

- [Ajouter un support pour changer la vue](#vcconswitchingtheviewa5)

Le reste de ce sujet suppose ce qui suit:

- Le nom `CWinApp`de l’objet dérivé est, `CMyWinApp`et `CMyWinApp` est déclaré et défini dans *MYWINAPP. H* et *MYWINAPP. RPC*.

- `CNewView`est le nom `CView`du nouvel objet `CNewView` dérivé, et est déclaré et défini dans *NEWVIEW. H* et *NEWVIEW. RPC*.

## <a name="modify-the-existing-application-class"></a><a name="vcconmodifyexistingapplicationa1"></a>Modifier la catégorie d’application existante

Pour que l’application passe d’une vue à l’autre, vous devez modifier la classe d’application en ajoutant des variables de membres pour stocker les vues et une méthode pour les changer.

Ajoutez le code suivant `CMyWinApp` à la déclaration de *MYWINAPP. H*:

[!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

Les nouvelles variables `m_pOldView` `m_pNewView`membres, et , pointent vers la vue actuelle et la nouvelle création. La nouvelle`SwitchView`méthode ( ) change les vues sur demande de l’utilisateur. Le corps de la méthode est discuté plus tard dans ce sujet dans [Mettre en œuvre la fonction de commutation](#vcconswitchingfunctiona4).

La dernière modification de la classe d’application nécessite d’inclure un nouveau fichier d’en-tête qui définit un message Windows (**WM_INITIALUPDATE**) qui est utilisé dans la fonction de commutation.

Insérez la ligne suivante dans la section inclure de *MYWINAPP. RPC*:

[!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

Enregistrez vos modifications et continuez à passer à l’étape suivante.

## <a name="create-and-modify-the-new-view-class"></a><a name="vcconnewviewclassa2"></a>Créer et modifier la nouvelle classe de vue

La création de la nouvelle classe de vue est facilitée en utilisant la commande **New Class** disponible à partir de Class View. La seule exigence pour cette classe `CView`est qu’elle dérive de . Ajoutez cette nouvelle classe à l’application. Pour obtenir des informations précises sur l’ajout d’une nouvelle classe au projet, voir [Ajouter une classe](../ide/adding-a-class-visual-cpp.md).

Une fois que vous avez ajouté la classe au projet, vous devez changer l’accessibilité de certains membres de la classe de vue.

Modifier *NEWVIEW. H* en changeant le spécificateur d’accès de **protégé** au **public** pour le constructeur et le destructeur. Cela permet à la classe d’être créée et détruite dynamiquement et de modifier l’apparence de vue avant qu’elle ne soit visible.

Enregistrez vos modifications et continuez à passer à l’étape suivante.

## <a name="create-and-attach-the-new-view"></a><a name="vcconattachnewviewa3"></a>Créer et joindre la nouvelle vue

Pour créer et joindre la nouvelle vue, vous devez modifier la `InitInstance` fonction de votre classe d’application. La modification ajoute un nouveau code qui crée un `m_pOldView` `m_pNewView` nouvel objet de vue, puis initialise à la fois et avec les deux objets de vue existants.

Étant donné que la `InitInstance` nouvelle vue est créée dans la fonction, les vues nouvelles et existantes persistent pendant toute la durée de l’application. Cependant, l’application pourrait tout aussi bien créer la nouvelle vue dynamiquement.

Insérez ce `ProcessShellCommand`code après l’appel à :

[!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

Enregistrez vos modifications et continuez à passer à l’étape suivante.

## <a name="implement-the-switching-function"></a><a name="vcconswitchingfunctiona4"></a>Mettre en œuvre la fonction de commutation

Dans l’étape précédente, vous avez ajouté du code qui a créé et para initialisé un nouvel objet de vue. La dernière pièce importante est de `SwitchView`mettre en œuvre la méthode de commutation, .

À la fin du fichier d’implémentation de votre classe de demande *(MYWINAPP. RPC*), ajouter la définition de méthode suivante :

[!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

Enregistrez vos modifications et continuez à passer à l’étape suivante.

## <a name="add-support-for-switching-the-view"></a><a name="vcconswitchingtheviewa5"></a>Ajouter un support pour changer la vue

La dernière étape consiste à `SwitchView` ajouter du code qui appelle la méthode lorsque l’application doit basculer entre les vues. Cela peut être fait de plusieurs façons: soit en ajoutant un nouvel élément de menu pour l’utilisateur de choisir ou en changeant les vues en interne lorsque certaines conditions sont remplies.

Pour plus d’informations sur l’ajout de nouveaux éléments de menu et les fonctions de gestionnaire de commande, voir [Handlers for Commands and Control Notifications](../mfc/handlers-for-commands-and-control-notifications.md).

## <a name="see-also"></a>Voir aussi

[Document/Afficher l’architecture](../mfc/document-view-architecture.md)
