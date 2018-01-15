---
title: "Conteneurs de contrôles ActiveX : Programmation de contrôles ActiveX dans un conteneur de contrôles ActiveX | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5a608d98b43e6daf340ab09c7adb275849f347a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>Conteneurs de contrôles ActiveX : programmation de contrôles ActiveX dans un conteneur de contrôles ActiveX
Cet article décrit le processus permettant d’accéder à l’exposé [méthodes](../mfc/mfc-activex-controls-methods.md) et [propriétés](../mfc/mfc-activex-controls-properties.md) de contrôles ActiveX intégrés. En fait, vous suivez ces étapes :  
  
1.  [Insérer un contrôle ActiveX dans le projet de conteneur ActiveX](../mfc/inserting-a-control-into-a-control-container-application.md) à l’aide de la galerie.  
  
2.  [Définir une variable membre](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) (ou autre forme d’accès) du même type que ActiveX classe wrapper du contrôle.  
  
3.  [Programmer le contrôle ActiveX](#_core_programming_the_activex_control) utilisant des fonctions membres de la classe wrapper.  
  
 Pour cet exemple, supposons que vous avez créé un projet basé sur la boîte de dialogue (nommé Container) avec prise en charge du contrôle ActiveX. L’exemple de contrôle Circ Circ, sera ajouté au projet obtenu.  
  
 Une fois le contrôle Circ inséré dans le projet (étape 1), insérez une instance du contrôle Circ dans la boîte de dialogue principale de l’application.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>Pour ajouter le contrôle Circ au modèle de boîte de dialogue  
  
1.  Charger le projet de conteneur de contrôle ActiveX. Pour cet exemple, utilisez le `Container` projet.  
  
2.  Cliquez sur l’onglet Affichage des ressources.  
  
3.  Ouvrez le **boîte de dialogue** dossier.  
  
4.  Double-cliquez sur le modèle de boîte de dialogue principale. Pour cet exemple, utilisez **IDD_CONTAINER_DIALOG**.  
  
5.  Cliquez sur l’icône du contrôle Circ dans la boîte à outils.  
  
6.  Cliquez sur un emplacement de la boîte de dialogue pour insérer le contrôle Circ.  
  
7.  À partir de la **fichier** menu, choisissez **Enregistrer tout** pour enregistrer toutes les modifications apportées au modèle de boîte de dialogue.  
  
## <a name="modifications-to-the-project"></a>Modifications apportées au projet  
 Pour activer l’application conteneur accéder au contrôle Circ, Visual C++ ajoute automatiquement la classe wrapper (`CCirc`) fichier d’implémentation (. CPP) pour le projet de conteneur et de l’en-tête de la classe wrapper (. H) fichier pour le fichier d’en-tête de la boîte de dialogue :  
  
 [!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]  
  
##  <a name="_core_the_wrapper_class_header_28h29_file"></a>L’en-tête de la classe Wrapper (. (H) fichier  
 Pour obtenir et définir les propriétés (et appeler les méthodes) du contrôle Circ, la `CCirc` classe wrapper fournit une déclaration de toutes les méthodes et propriétés. Dans l’exemple, ces déclarations sont trouvent dans CIRC. H. L’exemple suivant est la partie de la classe `CCirc` qui définit les interfaces exposées du contrôle ActiveX :  
  
 [!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]  
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]  
  
 Ces fonctions peuvent ensuite être appelées à partir d’autres procédures de l’application à l’aide de la syntaxe C++ normale. Pour plus d’informations sur l’utilisation de cette fonction membre définie pour accéder aux méthodes et les propriétés du contrôle, consultez la section [programmation du contrôle ActiveX](#_core_programming_the_activex_control).  
  
##  <a name="_core_member_variable_modifications_to_the_project"></a>Modifications des variables membres pour le projet  
 Une fois le contrôle ActiveX a été ajouté au projet et incorporé dans un conteneur de boîte de dialogue, il est accessible par d’autres parties du projet. Pour le contrôle d’accès le plus simple consiste à [créer une variable membre](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) de la classe de boîte de dialogue, `CContainerDlg` (étape 2), qui est du même type que la classe wrapper ajoutée au projet par Visual C++. Vous pouvez ensuite utiliser la variable membre pour accéder au contrôle incorporé à tout moment.  
  
 Lorsque le **ajouter une Variable membre** boîte de dialogue ajoute le `m_circctl` membre variable au projet, il ajoute également les lignes suivantes au fichier d’en-tête (. (H) de la `CContainerDlg` classe :  
  
 [!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]  
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]  
  
 En outre, un appel à **DDX_Control** est automatiquement ajouté à la `CContainerDlg`d’implémentation de `DoDataExchange`:  
  
 [!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]  
  
##  <a name="_core_programming_the_activex_control"></a>Programmation du contrôle ActiveX  
 À ce stade, vous avez inséré le contrôle ActiveX dans votre modèle de boîte de dialogue et créé une variable membre pour lui. Vous pouvez maintenant utiliser la syntaxe C++ courante pour accéder aux propriétés et méthodes du contrôle incorporé.  
  
 Comme indiqué (dans [le fichier d’en-tête (. Fichier H)](#_core_the_wrapper_class_header_28h29_file)), le fichier d’en-tête (. H) pour la `CCirc` classe wrapper, en l’occurrence CIRC. H, contient une liste des fonctions membres que vous pouvez utiliser pour obtenir et définir une valeur de propriété exposée. Fonctions membres des méthodes exposées sont également disponibles.  
  
 Un emplacement commun pour modifier les propriétés du contrôle est dans le `OnInitDialog` fonction membre de la classe de boîte de dialogue principale. Cette fonction est appelée juste avant que la boîte de dialogue s’affiche et est utilisée pour initialiser son contenu, y compris un de ses contrôles.  
  
 Le code suivant exemple utilise le `m_circctl` variable de membre pour modifier les propriétés Caption et CircleShape du contrôle Circ incorporé :  
  
 [!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md)

