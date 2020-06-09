---
title: "Contrôles ActiveX MFC : utilisation d'images dans un contrôle ActiveX"
ms.date: 11/04/2016
f1_keywords:
- LPPICTUREDISP
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- MFC ActiveX controls [MFC], pictures
- OnDraw method [MFC]
- OnResetState method [MFC]
- CLSID_CPicturePropPage [MFC]
ms.assetid: 2e49735c-21b9-4442-bb3d-c82ef258eec9
ms.openlocfilehash: 9eb204dd240ae17421a20b7cddeff56c9a22c19b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618077"
---
# <a name="mfc-activex-controls-using-pictures-in-an-activex-control"></a>Contrôles ActiveX MFC : utilisation d'images dans un contrôle ActiveX

Cet article décrit le type Picture courant et explique comment l’implémenter dans votre contrôle ActiveX. Les sujets abordés sont les suivants :

- [Vue d’ensemble des propriétés d’image personnalisées](#_core_overview_of_custom_picture_properties)

- [Implémentation d’une propriété Picture personnalisée dans votre contrôle ActiveX](#_core_implementing_a_custom_picture_property_in_your_activex_control)

- [Ajouts à votre projet de contrôle](#_core_additions_to_your_control_project)

## <a name="overview-of-custom-picture-properties"></a><a name="_core_overview_of_custom_picture_properties"></a> Vue d’ensemble des propriétés Picture personnalisées

Un type Picture est un groupe de types communs à certains contrôles ActiveX. Le type Picture gère des métafichiers, des bitmaps et des icônes, et permet à l’utilisateur de spécifier une image à afficher dans un contrôle ActiveX. Les propriétés Picture personnalisées sont implémentées en utilisant un objet Picture et des fonctions Get/Set qui permettent de contrôler l’accès utilisateur à la propriété Picture. Les utilisateurs du contrôle accèdent à la propriété Picture personnalisée via la page de propriétés Picture stock.

Outre le type Picture standard, les types Font et Color sont également disponibles. Pour plus d’informations sur l’utilisation du type Font standard dans votre contrôle ActiveX, consultez l’article [Contrôles ActiveX MFC : utilisation des polices](mfc-activex-controls-using-fonts.md).

Les classes de contrôles ActiveX fournissent différents composants que vous pouvez utiliser pour implémenter la propriété Picture dans le contrôle. Ces composants sont les suivants :

- La classe [CPictureHolder](reference/cpictureholder-class.md) .

   Cette classe fournit un accès facile à l’objet Picture et les fonctionnalités pour l’élément affiché par la propriété Picture personnalisée.

- Prise en charge des propriétés de type **LPPICTUREDISP**, implémentée avec les fonctions Get/Set.

   Grâce à l’Affichage de classes, vous pouvez rapidement ajouter une ou plusieurs propriétés personnalisées prenant en charge le type Picture. Pour plus d’informations sur l’ajout de propriétés de contrôle ActiveX avec l’Affichage de classes, consultez l’article [Contrôles ActiveX MFC : propriétés](mfc-activex-controls-properties.md).

- Une page de propriétés qui permet de manipuler une ou plusieurs propriétés Picture d’un contrôle.

   Cette page de propriétés fait partie d’un groupe de pages de propriétés stock disponibles pour les contrôles ActiveX. Pour plus d’informations sur les pages de propriétés des contrôles ActiveX, consultez l’article [Contrôles ActiveX MFC : utilisation des pages de propriétés stock](mfc-activex-controls-using-stock-property-pages.md).

## <a name="implementing-a-custom-picture-property-in-your-activex-control"></a><a name="_core_implementing_a_custom_picture_property_in_your_activex_control"></a>Implémentation d’une propriété Picture personnalisée dans votre contrôle ActiveX

Quand vous avez terminé les étapes décrites dans cette section, le contrôle peut afficher les images choisies par son utilisateur. L’utilisateur peut modifier l’image affichée à l’aide d’une page de propriétés qui affiche l’image actuelle et qui comporte un bouton Parcourir permettant à l’utilisateur de sélectionner d’autres images.

Une propriété Picture personnalisée est implémentée selon un processus similaire à celui utilisée pour l’implémentation d’autres propriétés, la principale différence étant que la propriété personnalisée doit prendre en charge un type Picture. Étant donné que l’élément de la propriété Picture doit être dessiné par le contrôle ActiveX, un certain nombre d’ajouts et de modifications doivent être effectués sur la propriété avant qu’elle puisse être entièrement implémentée.

Pour implémenter une propriété Picture personnalisée, vous devez procéder comme suit :

- [Ajoutez du code à votre projet de contrôle](#_core_additions_to_your_control_project).

   Un ID de page de propriétés Picture standard, un membre de données de type `CPictureHolder`et une propriété personnalisée de type **LPPICTUREDISP** avec une implémentation de Get/Set doivent être ajoutés.

- [Modifiez plusieurs fonctions dans votre classe de contrôle](#_core_modifications_to_your_control_project).

   Ces modifications sont apportées à plusieurs fonctions qui sont responsables du dessin de votre contrôle ActiveX.

## <a name="additions-to-your-control-project"></a><a name="_core_additions_to_your_control_project"></a> Ajouts à votre projet de contrôle

Pour ajouter l’ID de page de propriétés pour la page de propriétés Picture standard, insérez la ligne suivante après la macro BEGIN_PROPPAGEIDS dans le fichier d’implémentation du contrôle (. CPP) :

[!code-cpp[NVC_MFC_AxPic#1](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_1.cpp)]

Vous devez également incrémenter d’une unité le paramètre Count de votre macro BEGIN_PROPPAGEIDS. La ligne suivante le montre :

[!code-cpp[NVC_MFC_AxPic#2](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_2.cpp)]

Pour ajouter le membre de données `CPictureHolder` à la classe de contrôle, insérez la ligne suivante sous la section protégée de la déclaration de la classe de contrôle dans le fichier d’en-tête du contrôle (.H) :

[!code-cpp[NVC_MFC_AxPic#3](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_3.h)]

Il n’est pas nécessaire de nommer le membre de données *m_pic*; tout nom suffira.

Ensuite, ajoutez une propriété personnalisée qui prend en charge un type Picture :

#### <a name="to-add-a-custom-picture-property-using-the-add-property-wizard"></a>Pour ajouter une propriété Picture personnalisée à l’aide de l’Assistant Ajout de propriété

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. Dans le menu contextuel, choisissez **Ajouter** , puis **Ajouter une propriété**.

1. Dans la zone **Nom de la propriété** , tapez le nom de la propriété. À titre d’exemple, `ControlPicture` est utilisé dans cette procédure.

1. Dans la zone **type de propriété** , sélectionnez **IPictureDisp** <strong>\*</strong> pour le type de propriété.

1. Pour **Type d’implémentation**, cliquez sur **Méthodes Get/Set**.

1. Tapez un nom unique pour vos fonctions Get et Set, ou acceptez les noms par défaut. (Dans cet exemple, les noms par défaut `GetControlPicture` et `SetControlPicture` sont utilisés.)

1. Cliquez sur **Terminer**.

L’Assistant Ajout de propriété ajoute le code suivant entre les commentaires de la table de dispatch dans le fichier d’en-tête (.H) du contrôle :

[!code-cpp[NVC_MFC_AxPic#4](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_4.h)]

En outre, le code suivant a été inséré dans la table de dispatch du fichier d’implémentation (.CPP) du contrôle :

[!code-cpp[NVC_MFC_AxPic#5](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_5.cpp)]

L’Assistant Ajout de propriété ajoute également les deux fonctions stub suivantes dans le fichier d’implémentation du contrôle :

[!code-cpp[NVC_MFC_AxPic#6](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_6.cpp)]

> [!NOTE]
> Les noms de la classe et des fonctions de votre contrôle peuvent différer de l’exemple ci-dessus.

### <a name="modifications-to-your-control-project"></a><a name="_core_modifications_to_your_control_project"></a>Modifications apportées à votre projet de contrôle

Après avoir effectué les ajouts nécessaires au projet de contrôle, vous devez modifier plusieurs fonctions qui affectent le rendu de votre contrôle ActiveX. Ces fonctions, `OnResetState`, `OnDraw`et les fonctions Get/Set d’une propriété Picture personnalisée, se trouvent dans le fichier d’implémentation du contrôle. (Notez que dans cet exemple, la classe de contrôle est appelée `CSampleCtrl` , le `CPictureHolder` membre de données est appelé *m_pic*, et le nom de la propriété d’image personnalisée est `ControlPicture` .)

Dans la fonction `OnResetState` du contrôle, ajoutez la ligne facultative suivante après l’appel à `COleControl::OnResetState`:

[!code-cpp[NVC_MFC_AxPic#7](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_7.cpp)]

Ceci définit l’image du contrôle sur une image vide.

Pour dessiner l’image correctement, effectuez un appel à [CPictureHolder::Render](reference/cpictureholder-class.md#render) dans la fonction `OnDraw` du contrôle. Modifier votre fonction de façon à ce qu’elle ressemble à l’exemple suivant :

[!code-cpp[NVC_MFC_AxPic#8](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_8.cpp)]

Dans la fonction Get de la propriété Picture personnalisée du contrôle, ajoutez la ligne suivante :

[!code-cpp[NVC_MFC_AxPic#9](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_9.cpp)]

Dans la fonction Get de la propriété Picture personnalisée du contrôle, ajoutez les lignes suivantes :

[!code-cpp[NVC_MFC_AxPic#10](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_10.cpp)]

La propriété Picture doit être rendue persistante, pour que les informations ajoutées au moment de la conception s’affichent au moment de l’exécution. Ajoutez la ligne suivante à la fonction `COleControl`de la classe dérivée de `DoPropExchange` :

[!code-cpp[NVC_MFC_AxPic#11](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_11.cpp)]

> [!NOTE]
> Les noms de votre classe et de vos fonctions peuvent différer de l’exemple ci-dessus.

Une fois les modifications terminées, régénérez votre projet pour incorporer les nouvelles fonctionnalités de la propriété Picture personnalisée et utilisez le conteneur de test pour tester la nouvelle propriété. Pour plus d’informations sur la façon d’accéder au conteneur de test, consultez la page [Test des propriétés et des événements avec le conteneur de test](testing-properties-and-events-with-test-container.md) .

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : utilisation des polices](mfc-activex-controls-using-fonts.md)<br/>
[Contrôles ActiveX MFC : pages de propriétés](mfc-activex-controls-property-pages.md)
