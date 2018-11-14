---
title: 'Contrôles ActiveX MFC : utilisation de la liaison de données dans un contrôle ActiveX'
ms.date: 09/12/2018
f1_keywords:
- bindable
- requestedit
- defaultbind
- displaybind
- dispid
helpviewer_keywords:
- MFC ActiveX controls [MFC], data binding
- data binding [MFC], MFC ActiveX controls
- data-bound controls [MFC], MFC ActiveX controls
- controls [MFC], data binding
- bound controls [MFC], MFC ActiveX
ms.assetid: 476b590a-bf2a-498a-81b7-dd476bd346f1
ms.openlocfilehash: 9efac8ba0889d648def622ca045b9398c8eeef11
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518487"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>Contrôles ActiveX MFC : utilisation de la liaison de données dans un contrôle ActiveX

Une des utilisations plus puissantes de contrôles ActiveX est la liaison de données, ce qui permet à une propriété du contrôle à lier à un champ spécifique dans une base de données. Lorsqu’un utilisateur modifie les données de cette propriété liée, le contrôle notifie la base de données et les demandes que les champs d’enregistrements être mis à jour. La base de données puis vous avertit que le contrôle de la réussite ou l’échec de la demande.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

Cet article traite du côté du contrôle de votre tâche. Mise en œuvre les interactions de liaison de données avec la base de données est la responsabilité du conteneur de contrôle. Comment gérer les interactions de la base de données dans votre conteneur est dépasse le cadre de cette documentation. Comment vous préparez le contrôle pour la liaison de données est expliquée dans le reste de cet article.

![Diagramme conceptuel d’un data&#45;contrôle lié aux](../mfc/media/vc374v1.gif "vc374v1") diagramme conceptuel d’un contrôle lié aux données

Le `COleControl` classe fournit deux fonctions membres qui rendent un implémentation du processus de liaison de données. La première fonction [BoundPropertyRequestEdit](../mfc/reference/colecontrol-class.md#boundpropertyrequestedit), est utilisé pour demander l’autorisation de modifier la valeur de propriété. [BoundPropertyChanged](../mfc/reference/colecontrol-class.md#boundpropertychanged), la deuxième fonction est appelée une fois que la valeur de propriété a été modifiée.

Cet article aborde les rubriques suivantes :

- [Création d’une propriété Stock peut être liée](#vchowcreatingbindablestockproperty)

- [Création d’une méthode Get/Set peut être liée](#vchowcreatingbindablegetsetmethod)

##  <a name="vchowcreatingbindablestockproperty"></a> Création d’une propriété Stock peut être liée

Il est possible de créer une propriété stock lié aux données, bien qu’il est plus probable que vous souhaitez un [méthode get/set peut être liée](#vchowcreatingbindablegetsetmethod).

> [!NOTE]
> Propriétés stock ont le `bindable` et `requestedit` attributs par défaut.

#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>Pour ajouter une propriété stock peut être liée à l’aide de l’Assistant Ajout de propriété

1. Commencer un projet à l’aide de la [Assistant contrôle ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md).

1. Cliquez sur le nœud de l’interface de votre contrôle.

   Cette opération ouvre le menu contextuel.

1. Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter une propriété**.

1. Sélectionnez une des entrées à partir de la **nom de la propriété** liste déroulante. Par exemple, vous pouvez sélectionner **texte**.

   Étant donné que **texte** est une propriété stock, les **peut être liée** et **requestedit** attributs sont déjà activés.

1. Sélectionnez les cases à cocher suivantes à partir de la **attributs IDL** onglet : **displaybind** et **defaultbind** pour ajouter les attributs à la définition de propriété dans le projet. Fichier IDL. Ces attributs Assurez-vous le contrôle visible par l’utilisateur et la propriété stock la propriété peut être liée par défaut.

À ce stade, votre contrôle peut afficher des données à partir d’une source de données, mais l’utilisateur ne sera pas en mesure de mettre à jour les champs de données. Si vous souhaitez que votre contrôle également être en mesure de mettre à jour des données, de modifier le `OnOcmCommand` [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) fonction permettant de se présenter comme suit :

[!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

Vous pouvez maintenant générer le projet, qui enregistrera le contrôle. Lorsque vous insérez le contrôle dans une boîte de dialogue, le **champ de données** et **Source de données** propriétés a été ajoutées et vous pouvez maintenant sélectionner une source de données et le champ à afficher dans le contrôle.

##  <a name="vchowcreatingbindablegetsetmethod"></a> Création d’une méthode Get/Set peut être liée

En plus d’une propriété get/set (méthode), vous pouvez également créer un [propriétés stock peut être liée](#vchowcreatingbindablestockproperty).

> [!NOTE]
> Cette procédure suppose que vous avez un contrôle ActiveX qui sous-classe un contrôle Windows du projet.

#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>Pour ajouter une méthode get/set peut être liée à l’aide de l’Assistant Ajout de propriété

1. Chargez votre projet de contrôle.

1. Sur le **paramètres de contrôle** , sélectionnez une classe de fenêtre pour le contrôle à la sous-classe. Par exemple, vous souhaiterez sous-classe un contrôle d’édition.

1. Chargez votre projet de contrôle.

1. Cliquez sur le nœud de l’interface de votre contrôle.

   Cette opération ouvre le menu contextuel.

1. Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter une propriété**.

1. Tapez le nom de propriété dans le **nom de la propriété** boîte. Utilisez `MyProp` pour cet exemple.

1. Sélectionnez un type de données à partir de la **Type de propriété** zone de liste déroulante. Utilisez **court** pour cet exemple.

1. Pour **Type d’implémentation**, cliquez sur **Méthodes Get/Set**.

1. Sélectionnez les cases à cocher suivantes à partir de l’onglet Attributs IDL : **peut être liée**, **requestedit**, **displaybind**, et **defaultbind** à ajouter les attributs à la définition de propriété dans le projet. Fichier IDL. Ces attributs Assurez-vous le contrôle visible par l’utilisateur et la propriété stock la propriété peut être liée par défaut.

1. Cliquez sur **Terminer**.

1. Modifier le corps de la `SetMyProp` de fonction pour qu’il contienne le code suivant :

   [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]

1. Le paramètre passé à la `BoundPropertyChanged` et `BoundPropertyRequestEdit` fonctions est le dispid de la propriété, qui est le paramètre passé à l’attribut id() pour la propriété dans le. Fichier IDL.

1. Modifier le [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) fonction afin qu’il contient le code suivant :

   [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

1. Modifier le `OnDraw` fonction pour qu’il contienne le code suivant :

   [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]

1. À la section publique du fichier d’en-tête du fichier d’en-tête pour votre classe de contrôle, ajoutez les définitions suivantes (constructeurs) pour les variables membres :

   [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]

1. Vérifiez la ligne suivante à la dernière ligne dans le `DoPropExchange` (fonction) :

   [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]

1. Modifier le `OnResetState` fonction pour qu’il contienne le code suivant :

   [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]

1. Modifier le `GetMyProp` fonction pour qu’il contienne le code suivant :

   [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]

Vous pouvez maintenant générer le projet, qui enregistrera le contrôle. Lorsque vous insérez le contrôle dans une boîte de dialogue, le **champ de données** et **Source de données** propriétés a été ajoutées et vous pouvez maintenant sélectionner une source de données et le champ à afficher dans le contrôle.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

