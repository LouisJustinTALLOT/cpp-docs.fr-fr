---
title: 'Conteneurs de contrôles ActiveX : programmation de contrôles ActiveX dans un conteneur de contrôles ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- Confirm Classes dialog box
- wrapper classes [MFC], ActiveX controls
- ActiveX control containers [MFC], wrapper classes
- ActiveX controls [MFC], accessing
- MFC ActiveX controls [MFC], accessing in containers
- header files [MFC], for ActiveX control wrapper class
- wrapper classes [MFC], using
- ActiveX controls [MFC], wrapper classes
ms.assetid: ef9b2480-92d6-4191-b16e-8055c4fd7b73
ms.openlocfilehash: 9620f4d47197147db4972c9f2024f6018a705902
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371189"
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>Conteneurs de contrôles ActiveX : programmation de contrôles ActiveX dans un conteneur de contrôles ActiveX

Cet article décrit le processus d’accès aux [méthodes](../mfc/mfc-activex-controls-methods.md) et propriétés exposées des contrôles ActiveX [intégrés.](../mfc/mfc-activex-controls-properties.md)

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne devrait pas être utilisée pour de nouveaux développements. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, voir [ActiveX Controls](activex-controls.md).

Fondamentalement, vous suivrez ces étapes:

1. [Insérez un contrôle ActiveX dans le projet de conteneurs ActiveX](../mfc/inserting-a-control-into-a-control-container-application.md) à l’aide de Gallery.

1. [Définir une variable de membre](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) (ou toute autre forme d’accès) du même type que la classe d’emballage de contrôle ActiveX.

1. [Programmez le contrôle ActiveX](#_core_programming_the_activex_control) à l’aide des fonctions prédéfinies des membres de la classe d’emballage.

Pour cette discussion, supposons que vous avez créé un projet basé sur le dialogue (nommé Container) avec le support de contrôle ActiveX. Le contrôle de l’échantillon Circ, Circ, sera ajouté au projet qui en résultera.

Une fois que le contrôle du Circ est inséré dans le projet (étape 1), insérez une instance du contrôle du Circ dans la boîte de dialogue principale de l’application.

## <a name="procedures"></a>Procédures

#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>Pour ajouter le contrôle du Circ au modèle de dialogue

1. Chargez le projet de conteneur de contrôle ActiveX. Pour cet exemple, `Container` utilisez le projet.

1. Cliquez sur l’onglet Vue sur les ressources.

1. Ouvrez le dossier **Dialog.**

1. Double-cliquez sur le modèle principal de boîte de dialogue. Pour cet exemple, utiliser **IDD_CONTAINER_DIALOG**.

1. Cliquez sur l’icône de contrôle Circ sur la boîte à outils.

1. Cliquez sur un endroit dans la boîte de dialogue pour insérer le contrôle du Circ.

1. Du menu **Fichier,** choisissez **Save All** pour enregistrer toutes les modifications au modèle de boîte de dialogue.

## <a name="modifications-to-the-project"></a>Modifications apportées au projet

Pour permettre à l’application Container d’accéder au contrôle Circ,`CCirc`Visual CMMD ajoute automatiquement le fichier d’implémentation de la classe d’emballage (). CPP) au projet Container et à l’en-tête de la classe d’emballage (. H) fichier au fichier d’en-tête de boîte de dialogue :

[!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]

## <a name="the-wrapper-class-header-h-file"></a><a name="_core_the_wrapper_class_header_28h29_file"></a>The Wrapper Class Header (. H) Fichier

Pour obtenir et définir des propriétés (et invoquer des méthodes) pour le contrôle Circ, la `CCirc` classe d’emballage fournit une déclaration de toutes les méthodes et propriétés exposées. Dans l’exemple, ces déclarations se trouvent dans le CIRC. H. L’échantillon suivant est `CCirc` la partie de classe qui définit les interfaces exposées du contrôle ActiveX :

[!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]

Ces fonctions peuvent alors être appelées à partir d’autres procédures de l’application à l’aide d’une syntaxe normale de C. Pour plus d’informations sur l’utilisation de cette fonction membre définie pour accéder aux méthodes et aux propriétés du contrôle, voir la section [Programmation du contrôle ActiveX](#_core_programming_the_activex_control).

## <a name="member-variable-modifications-to-the-project"></a><a name="_core_member_variable_modifications_to_the_project"></a>Modifications variables des membres au projet

Une fois que le contrôle ActiveX a été ajouté au projet et intégré dans un conteneur de boîte de dialogue, il peut être consulté par d’autres parties du projet. La façon la plus simple d’accéder au contrôle est `CContainerDlg` de créer une variable de [membre](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) de la classe de dialogue, (étape 2), qui est du même type que la classe d’emballage ajoutée au projet par Visual C. Vous pouvez ensuite utiliser la variable du membre pour accéder au contrôle intégré à tout moment.

Lorsque la boîte de dialogue **Variable Add Member** ajoute la variable *m_circctl* membre au projet, elle ajoute également les lignes suivantes au fichier d’en-tête (. H) de `CContainerDlg` la classe:

[!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]

En outre, un appel à **DDX_Control** est `CContainerDlg`automatiquement ajouté `DoDataExchange`à la mise en œuvre de :

[!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]

## <a name="programming-the-activex-control"></a><a name="_core_programming_the_activex_control"></a>Programmation du contrôle ActiveX

À ce stade, vous avez inséré le contrôle ActiveX dans votre modèle de dialogue et créé une variable de membre pour cela. Vous pouvez maintenant utiliser la syntaxe CMD commune pour accéder aux propriétés et aux méthodes du contrôle intégré.

Comme indiqué (dans [The Wrapper Class Header (. H) Fichier](#_core_the_wrapper_class_header_28h29_file)), le fichier d’en-tête (. H) pour `CCirc` la classe d’emballage, dans ce cas CIRC. H, contient une liste des fonctions des membres que vous pouvez utiliser pour obtenir et définir n’importe quelle valeur de propriété exposée. Des fonctions de membre pour les méthodes exposées sont également disponibles.

Un endroit commun pour modifier les propriétés du contrôle est dans la `OnInitDialog` fonction membre de la classe principale de dialogue. Cette fonction est appelée juste avant l’apparition de la boîte de dialogue et est utilisée pour initialiser son contenu, y compris l’un de ses contrôles.

L’exemple de code suivant utilise la variable *m_circctl* membre pour modifier les propriétés caption et CircleShape du contrôle intégré du Circ :

[!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]

## <a name="see-also"></a>Voir aussi

[Conteneurs de contrôle ActiveX](../mfc/activex-control-containers.md)
