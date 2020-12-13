---
description: 'En savoir plus sur : ajout de plusieurs vues à un seul document'
title: Ajout de plusieurs vues à un seul document
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: 84f50ad96e4c5939c7ee2e97f8babfaa5221b6f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343729"
---
# <a name="adding-multiple-views-to-a-single-document"></a>Ajout de plusieurs vues à un seul document

Dans une application SDI (single-document interface) créée à l’aide de la bibliothèque MFC (Microsoft Foundation Class), chaque type de document est associé à un type d’affichage unique. Dans certains cas, il est souhaitable d’avoir la possibilité de basculer l’affichage actuel d’un document avec une nouvelle vue.

> [!TIP]
> Pour obtenir des procédures supplémentaires sur l’implémentation de plusieurs vues pour un seul document, consultez [CDocument :: AddView](reference/cdocument-class.md#addview) et l’exemple [Collect](../overview/visual-cpp-samples.md) MFC.

Vous pouvez implémenter cette fonctionnalité en ajoutant une nouvelle `CView` classe dérivée de et du code supplémentaire pour basculer dynamiquement les affichages vers une application MFC existante.

La procédure comporte trois étapes :

- [Modifier la classe d’application existante](#vcconmodifyexistingapplicationa1)

- [Créer et modifier la nouvelle classe d’affichage](#vcconnewviewclassa2)

- [Créer et attacher la nouvelle vue](#vcconattachnewviewa3)

- [Implémenter la fonction de basculement](#vcconswitchingfunctiona4)

- [Ajouter la prise en charge du basculement de la vue](#vcconswitchingtheviewa5)

Le reste de cette rubrique suppose ce qui suit :

- Le nom de l' `CWinApp` objet dérivé de est `CMyWinApp` , et `CMyWinApp` est déclaré et défini dans *MYWINAPP. H* et *MYWINAPP. CPP*.

- `CNewView` est le nom du nouvel `CView` objet dérivé de et `CNewView` est déclaré et défini dans *NewView. H* et *NewView. CPP*.

## <a name="modify-the-existing-application-class"></a><a name="vcconmodifyexistingapplicationa1"></a> Modifier la classe d’application existante

Pour que l’application bascule entre les vues, vous devez modifier la classe d’application en ajoutant des variables membres pour stocker les vues et une méthode pour les basculer.

Ajoutez le code suivant à la déclaration de `CMyWinApp` dans *MYWINAPP. H*:

[!code-cpp[NVC_MFCDocViewSDI#1](codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

Les nouvelles variables membres, `m_pOldView` et `m_pNewView` , pointent vers la vue actuelle et celle qui vient d’être créée. La nouvelle méthode ( `SwitchView` ) bascule les vues lorsque l’utilisateur les demande. Le corps de la méthode est abordé plus loin dans cette rubrique dans [implémentation de la fonction de basculement](#vcconswitchingfunctiona4).

La dernière modification apportée à la classe application nécessite l’ajout d’un nouveau fichier d’en-tête qui définit un message Windows (**WM_INITIALUPDATE**) utilisé dans la fonction de basculement.

Insérez la ligne suivante dans la section include de *MYWINAPP. CPP*:

[!code-cpp[NVC_MFCDocViewSDI#2](codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

Enregistrez vos modifications et passez à l’étape suivante.

## <a name="create-and-modify-the-new-view-class"></a><a name="vcconnewviewclassa2"></a> Créer et modifier la nouvelle classe d’affichage

La création de la nouvelle classe d’affichage est simplifiée à l’aide de la commande **nouvelle classe** disponible à partir de affichage de classes. La seule exigence pour cette classe est qu’elle dérive de `CView` . Ajoutez cette nouvelle classe à l’application. Pour obtenir des informations spécifiques sur l’ajout d’une nouvelle classe au projet, consultez [Ajout d’une classe](../ide/adding-a-class-visual-cpp.md).

Une fois que vous avez ajouté la classe au projet, vous devez modifier l’accessibilité de certains membres de classe de vue.

Modifiez *NewView. H* en remplaçant le spécificateur d’accès par **`protected`** **`public`** pour le constructeur et le destructeur. Cela permet à la classe d’être créée et détruite dynamiquement, et de modifier l’apparence de la vue avant qu’elle ne soit visible.

Enregistrez vos modifications et passez à l’étape suivante.

## <a name="create-and-attach-the-new-view"></a><a name="vcconattachnewviewa3"></a> Créer et attacher la nouvelle vue

Pour créer et attacher la nouvelle vue, vous devez modifier la `InitInstance` fonction de votre classe d’application. La modification ajoute un nouveau code qui crée un nouvel objet de vue, puis initialise `m_pOldView` `m_pNewView` à la fois et avec les deux objets de vue existants.

Étant donné que la nouvelle vue est créée dans la `InitInstance` fonction, les vues nouvelles et existantes persistent pendant la durée de vie de l’application. Toutefois, l’application peut tout aussi facilement créer la nouvelle vue de manière dynamique.

Insérez ce code après l’appel à `ProcessShellCommand` :

[!code-cpp[NVC_MFCDocViewSDI#3](codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

Enregistrez vos modifications et passez à l’étape suivante.

## <a name="implement-the-switching-function"></a><a name="vcconswitchingfunctiona4"></a> Implémenter la fonction de basculement

À l’étape précédente, vous avez ajouté du code qui a créé et initialisé un nouvel objet de vue. La dernière partie majeure consiste à implémenter la méthode de basculement, `SwitchView` .

À la fin du fichier d’implémentation pour votre classe d’application (*MYWINAPP. CPP*), ajoutez la définition de méthode suivante :

[!code-cpp[NVC_MFCDocViewSDI#4](codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

Enregistrez vos modifications et passez à l’étape suivante.

## <a name="add-support-for-switching-the-view"></a><a name="vcconswitchingtheviewa5"></a> Ajouter la prise en charge du basculement de la vue

La dernière étape consiste à ajouter du code qui appelle la `SwitchView` méthode lorsque l’application doit basculer entre les vues. Pour ce faire, vous pouvez procéder de plusieurs façons : en ajoutant un nouvel élément de menu pour que l’utilisateur puisse choisir ou basculer les affichages en interne lorsque certaines conditions sont remplies.

Pour plus d’informations sur l’ajout de nouveaux éléments de menu et de fonctions de gestionnaire de commandes, consultez [gestionnaires pour les commandes et les notifications de contrôle](handlers-for-commands-and-control-notifications.md).

## <a name="see-also"></a>Voir aussi

[Architecture document/vue](document-view-architecture.md)
