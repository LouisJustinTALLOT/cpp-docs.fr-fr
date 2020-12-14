---
description: 'En savoir plus sur : conteneurs de contrôles ActiveX : programmation de contrôles ActiveX dans un conteneur de contrôles ActiveX'
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
ms.openlocfilehash: 34a5a2aaa1d7ec940ea31ae2fbe8c89ba3d84818
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251009"
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>Conteneurs de contrôles ActiveX : programmation de contrôles ActiveX dans un conteneur de contrôles ActiveX

Cet article décrit le processus d’accès aux [méthodes](../mfc/mfc-activex-controls-methods.md) exposées et aux [Propriétés](../mfc/mfc-activex-controls-properties.md) des contrôles ActiveX incorporés.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

En fait, procédez comme suit :

1. [Insérez un contrôle ActiveX dans le projet de conteneur ActiveX](../mfc/inserting-a-control-into-a-control-container-application.md) à l’aide de la Galerie.

1. [Définissez une variable membre](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) (ou une autre forme d’accès) du même type que la classe wrapper de contrôle ActiveX.

1. [Programmez le contrôle ActiveX](#_core_programming_the_activex_control) à l’aide de fonctions membres prédéfinies de la classe wrapper.

Pour cette discussion, supposons que vous avez créé un projet basé sur des boîtes de dialogue (conteneur nommé) avec prise en charge des contrôles ActiveX. L’exemple de contrôle CIRC, CIRC, sera ajouté au projet résultant.

Une fois le contrôle Circ inséré dans le projet (étape 1), insérez une instance du contrôle Circ dans la boîte de dialogue principale de l’application.

## <a name="procedures"></a>Procédures

#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>Pour ajouter le contrôle Circ au modèle de boîte de dialogue

1. Chargez le projet conteneur de contrôles ActiveX. Pour cet exemple, utilisez le `Container` projet.

1. Cliquez sur l’onglet Affichage des ressources.

1. Ouvrez le dossier **boîte de dialogue** .

1. Double-cliquez sur le modèle de boîte de dialogue principale. Pour cet exemple, utilisez **IDD_CONTAINER_DIALOG**.

1. Cliquez sur l’icône de contrôle Circ dans la boîte à outils.

1. Cliquez sur un emplacement dans la boîte de dialogue pour insérer le contrôle Circ.

1. Dans le menu **fichier** , choisissez **enregistrer tout** pour enregistrer toutes les modifications apportées au modèle de boîte de dialogue.

## <a name="modifications-to-the-project"></a>Modifications apportées au projet

Pour permettre à l’application de conteneur d’accéder au contrôle CIRC, Visual C++ ajoute automatiquement le fichier d’implémentation de classe wrapper ( `CCirc` ) (. CPP) au projet de conteneur et à l’en-tête de classe wrapper (. H) dans le fichier d’en-tête de boîte de dialogue :

[!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]

## <a name="the-wrapper-class-header-h-file"></a><a name="_core_the_wrapper_class_header_28h29_file"></a> En-tête de classe wrapper (. H)

Pour obtenir et définir des propriétés (et appeler des méthodes) pour le contrôle CIRC, la `CCirc` classe wrapper fournit une déclaration de toutes les méthodes et propriétés exposées. Dans l’exemple, ces déclarations se trouvent dans CIRC. H. L’exemple suivant est la partie de la classe `CCirc` qui définit les interfaces exposées du contrôle ActiveX :

[!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]

Ces fonctions peuvent ensuite être appelées à partir d’autres procédures de l’application à l’aide de la syntaxe C++ normale. Pour plus d’informations sur l’utilisation de cette fonction membre définie pour accéder aux méthodes et propriétés du contrôle, consultez la section [programmation du contrôle ActiveX](#_core_programming_the_activex_control).

## <a name="member-variable-modifications-to-the-project"></a><a name="_core_member_variable_modifications_to_the_project"></a> Modifications des variables membres du projet

Une fois que le contrôle ActiveX a été ajouté au projet et incorporé dans un conteneur de boîte de dialogue, il est accessible par d’autres parties du projet. Le moyen le plus simple d’accéder au contrôle consiste à [créer une variable membre](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) de la classe Dialog, `CContainerDlg` (étape 2), qui est du même type que la classe wrapper ajoutée au projet par Visual C++. Vous pouvez ensuite utiliser la variable membre pour accéder au contrôle incorporé à tout moment.

Quand la boîte de dialogue **Ajouter une variable membre** ajoute la variable membre *m_circctl* au projet, elle ajoute également les lignes suivantes au fichier d’en-tête (. H) de la `CContainerDlg` classe :

[!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]

En outre, un appel à **DDX_Control** est automatiquement ajouté à l' `CContainerDlg` implémentation de `DoDataExchange` :

[!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]

## <a name="programming-the-activex-control"></a><a name="_core_programming_the_activex_control"></a> Programmation du contrôle ActiveX

À ce stade, vous avez inséré le contrôle ActiveX dans votre modèle de boîte de dialogue et créé une variable membre pour celui-ci. Vous pouvez maintenant utiliser la syntaxe C++ commune pour accéder aux propriétés et aux méthodes du contrôle incorporé.

Comme indiqué (dans [l’en-tête de classe wrapper (. H)](#_core_the_wrapper_class_header_28h29_file)), le fichier d’en-tête (. H) pour la `CCirc` classe wrapper, dans ce cas CIRC. H, contient une liste de fonctions membres que vous pouvez utiliser pour obtenir et définir toute valeur de propriété exposée. Les fonctions membres pour les méthodes exposées sont également disponibles.

La `OnInitDialog` fonction membre de la classe de boîte de dialogue principale constitue un emplacement courant pour modifier les propriétés du contrôle. Cette fonction est appelée juste avant que la boîte de dialogue ne s’affiche et est utilisée pour initialiser son contenu, y compris l’un de ses contrôles.

L’exemple de code suivant utilise la variable membre *m_circctl* pour modifier les propriétés Caption et CircleShape du contrôle Circ incorporé :

[!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]

## <a name="see-also"></a>Voir aussi

[Conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md)
