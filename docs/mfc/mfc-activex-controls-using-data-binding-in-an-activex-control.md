---
title: 'Contrôles ActiveX MFC : À l’aide de la liaison de données dans un contrôle ActiveX | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- bindable
- requestedit
- defaultbind
- displaybind
- dispid
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], data binding
- data binding [MFC], MFC ActiveX controls
- data-bound controls [MFC], MFC ActiveX controls
- controls [MFC], data binding
- bound controls [MFC], MFC ActiveX
ms.assetid: 476b590a-bf2a-498a-81b7-dd476bd346f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 267d47b7e061e3bde39b199cd948ba9875dea16b
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929729"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>Contrôles ActiveX MFC : utilisation de la liaison de données dans un contrôle ActiveX
Une des utilisations plus puissantes de contrôles ActiveX est la liaison de données, ce qui permet une propriété du contrôle à lier à un champ spécifique dans une base de données. Lorsqu’un utilisateur modifie les données de cette propriété liée, le contrôle notifie la base de données et les demandes que le champ d’enregistrement est mis à jour. La base de données puis vous avertit que le contrôle de la réussite ou l’échec de la demande.  
  
 Cet article traite du côté du contrôle de votre tâche. Mise en œuvre les interactions de liaison de données avec la base de données est la responsabilité du conteneur de contrôle. Comment gérer les interactions de la base de données dans votre conteneur est dépasse le cadre de cette documentation. Comment vous préparez le contrôle de liaison de données est expliqué dans le reste de cet article.  
  
 ![Diagramme conceptuel d’une donnée&#45;contrôle lié aux](../mfc/media/vc374v1.gif "vc374v1")  
Diagramme conceptuel d’un contrôle lié aux données  
  
 La `COleControl` classe fournit deux fonctions membres qui implémentent du processus de liaison de données. La première fonction [BoundPropertyRequestEdit](../mfc/reference/colecontrol-class.md#boundpropertyrequestedit), est utilisé pour demander l’autorisation de modifier la valeur de propriété. [BoundPropertyChanged](../mfc/reference/colecontrol-class.md#boundpropertychanged), la deuxième fonction est appelée une fois que la valeur de propriété a été modifiée.  
  
 Cet article couvre les rubriques suivantes :  
  
-   [Création d’une propriété Stock](#vchowcreatingbindablestockproperty)  
  
-   [Création d’une méthode Get/Set pouvant être liées](#vchowcreatingbindablegetsetmethod)  
  
##  <a name="vchowcreatingbindablestockproperty"></a> Création d’une propriété Stock  
 Il est possible de créer une propriété stock lié aux données, même s’il est probable que vous pouvez un [méthode get/set peut être liée](#vchowcreatingbindablegetsetmethod).  
  
> [!NOTE]
>  Propriétés stock ont le `bindable` et `requestedit` les attributs par défaut.  
  
#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>Pour ajouter une propriété stock peut être liée à l’aide de l’Assistant Ajout de propriété  
  
1.  Commencer un projet à l’aide de la [Assistant contrôle ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md).  
  
2.  Cliquez sur le nœud de l’interface de votre contrôle.  
  
     Le menu contextuel s’ouvre.  
  
3.  Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter une propriété**.  
  
4.  Sélectionnez une entrées à partir de la **nom de la propriété** liste déroulante. Par exemple, vous pouvez sélectionner **texte**.  
  
     Étant donné que **texte** est une propriété stock, les **pouvant être liés** et **requestedit** attributs sont déjà activées.  
  
5.  Sélectionnez les cases à cocher suivantes à partir de la **attributs IDL** onglet : **displaybind** et **defaultbind** pour ajouter les attributs à la définition de propriété dans le fichier. Fichier IDL. Ces attributs rendre le contrôle visible par l’utilisateur et faire de la propriété pouvant être liée par défaut de la propriété stock.  
  
 À ce stade, votre contrôle peut afficher des données à partir d’une source de données, mais l’utilisateur ne sera pas en mesure de mettre à jour les champs de données. Si vous souhaitez que votre contrôle également être en mesure de mettre à jour des données, de modifier le `OnOcmCommand` [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) afin de se présenter comme suit :  
  
 [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]  
  
 Vous pouvez ensuite générer le projet, qui enregistrera le contrôle. Lorsque vous insérez le contrôle dans une boîte de dialogue, la **champ de données** et **Source de données** propriétés a été ajoutées et vous pouvez maintenant sélectionner une source de données et le champ à afficher dans le contrôle.  
  
##  <a name="vchowcreatingbindablegetsetmethod"></a> Création d’une méthode Get/Set pouvant être liées  
 En plus d’une propriété get/set (méthode), vous pouvez également créer un [propriété stock peut être liée](#vchowcreatingbindablestockproperty).  
  
> [!NOTE]
>  Cette procédure suppose que vous avez un contrôle ActiveX qui sous-classe un contrôle Windows du projet.  
  
#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>Pour ajouter une méthode get/set peut être liée à l’aide de l’Assistant Ajout de propriété  
  
1.  Chargez votre projet de contrôle.  
  
2.  Sur le **paramètres de contrôle** , sélectionnez une classe de fenêtre pour le contrôle à la sous-classe. Par exemple, vous voudrez sous-classe un contrôle d’édition.  
  
3.  Chargez votre projet de contrôle.  
  
4.  Cliquez sur le nœud de l’interface de votre contrôle.  
  
     Le menu contextuel s’ouvre.  
  
5.  Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter une propriété**.  
  
6.  Tapez le nom de propriété dans le **nom de la propriété** boîte. Utilisez `MyProp` pour cet exemple.  
  
7.  Sélectionnez un type de données à partir de la **Type de propriété** zone de liste déroulante. Utilisez **court** pour cet exemple.  
  
8.  Pour **Type d’implémentation**, cliquez sur **Méthodes Get/Set**.  
  
9. Activez les cases à cocher suivantes à partir de l’onglet Attributs IDL : **pouvant être liés**, **requestedit**, **displaybind**, et **defaultbind** à ajouter les attributs à la définition de propriété dans le fichier. Fichier IDL. Ces attributs rendre le contrôle visible par l’utilisateur et faire de la propriété pouvant être liée par défaut de la propriété stock.  
  
10. Cliquez sur **Terminer**.  
  
11. Modifier le corps de la `SetMyProp` de fonction pour qu’il contienne le code suivant :  
  
     [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]  
  
12. Le paramètre passé à la `BoundPropertyChanged` et `BoundPropertyRequestEdit` fonctions est le dispid de la propriété, qui est le paramètre passé à l’attribut id() pour la propriété dans le. Fichier IDL.  
  
13. Modifier la [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) fonctionnent et qu’il contient le code suivant :  
  
     [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]  
  
14. Modifier la `OnDraw` de fonction pour qu’il contienne le code suivant :  
  
     [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]  
  
15. À la section public du fichier d’en-tête du fichier d’en-tête pour votre classe de contrôle, ajoutez les définitions suivantes (constructeurs) pour les variables membres :  
  
     [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]  
  
16. Vérifiez la ligne suivante de la dernière ligne dans le `DoPropExchange` (fonction) :  
  
     [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]  
  
17. Modifier la `OnResetState` de fonction pour qu’il contienne le code suivant :  
  
     [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]  
  
18. Modifier la `GetMyProp` de fonction pour qu’il contienne le code suivant :  
  
     [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]  
  
 Vous pouvez ensuite générer le projet, qui enregistrera le contrôle. Lorsque vous insérez le contrôle dans une boîte de dialogue, la **champ de données** et **Source de données** propriétés a été ajoutées et vous pouvez maintenant sélectionner une source de données et le champ à afficher dans le contrôle.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)   

