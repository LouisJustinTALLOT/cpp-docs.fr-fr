---
title: 'Contrôles ActiveX MFC : utilisation de la liaison de données dans un contrôle ActiveX'
ms.date: 11/19/2018
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
ms.openlocfilehash: 41ac0180242aea3143a1df2c32dc81fb18cd7dca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370778"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>Contrôles ActiveX MFC : utilisation de la liaison de données dans un contrôle ActiveX

L’une des utilisations les plus puissantes des contrôles ActiveX est la liaison de données, qui permet à une propriété du contrôle de se lier à un champ spécifique dans une base de données. Lorsqu’un utilisateur modifie les données de cette propriété liée, le contrôle avise la base de données et demande que le champ d’enregistrement soit mis à jour. La base de données informe ensuite le contrôle du succès ou de l’échec de la demande.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne devrait pas être utilisée pour de nouveaux développements. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, voir [ActiveX Controls](activex-controls.md).

Cet article couvre le côté de contrôle de votre tâche. La mise en œuvre des interactions de liaison de données avec la base de données est la responsabilité du conteneur de contrôle. La façon dont vous gérez les interactions de base de données dans votre conteneur dépasse la portée de cette documentation. La façon dont vous préparez le contrôle de la liaison de données est expliquée dans le reste de cet article.

![Diagramme conceptuel d’un contrôle lié&#45;de données](../mfc/media/vc374v1.gif "Diagramme conceptuel d’un contrôle lié&#45;de données") <br/>
Diagramme conceptuel d’un contrôle lié des données

La `COleControl` classe fournit deux fonctions de membre qui rendent la liaison de données un processus facile à mettre en œuvre. La première fonction, [BoundPropertyRequestEdit](../mfc/reference/colecontrol-class.md#boundpropertyrequestedit), est utilisée pour demander la permission de modifier la valeur de la propriété. [BoundPropertyChanged](../mfc/reference/colecontrol-class.md#boundpropertychanged), la deuxième fonction, est appelée après que la valeur de la propriété a été changée avec succès.

Cet article aborde les thèmes suivants :

- [Création d’une propriété d’actions liants](#vchowcreatingbindablestockproperty)

- [Création d’une méthode Get/Set lisible](#vchowcreatingbindablegetsetmethod)

## <a name="creating-a-bindable-stock-property"></a><a name="vchowcreatingbindablestockproperty"></a>Création d’une propriété d’actions liants

Il est possible de créer une propriété de stock liée à des données, bien qu’il soit plus probable que vous voudrez une [méthode li bindable obtenir / ensemble](#vchowcreatingbindablegetsetmethod).

> [!NOTE]
> Les propriétés `bindable` `requestedit` boursières ont les attributs et les attributs par défaut.

#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>Pour ajouter une propriété de stock liant utilisant le Magicien de propriété d’ajouter

1. Commencez un projet à l’aide du [MFC ActiveX Control Wizard](../mfc/reference/mfc-activex-control-wizard.md).

1. Cliquez à droite sur le nœud d’interface pour votre contrôle.

   Cela ouvre le menu raccourci.

1. À partir du menu raccourci, cliquez sur **Ajouter** et cliquez ensuite **ajouter la propriété**.

1. Sélectionnez l’une des entrées de la liste d’abandon **du nom de propriété.** Par exemple, vous pouvez sélectionner **le texte**.

   Parce que **le texte** est une propriété de stock, les attributs **liants** et **demandés** sont déjà vérifiés.

1. Sélectionnez les cases de cocher suivantes de l’onglet **Attributs IDL** : **displaybind** et **defaultbind** pour ajouter les attributs à la définition de propriété dans le projet . Fichier IDL. Ces attributs rendent le contrôle visible à l’utilisateur et font de la propriété stock la propriété liant par défaut.

À ce stade, votre contrôle peut afficher des données à partir d’une source de données, mais l’utilisateur ne sera pas en mesure de mettre à jour les champs de données. Si vous souhaitez que votre contrôle soit également `OnOcmCommand` en mesure de mettre à jour les données, modifiez la fonction [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) pour voir ce qui suit :

[!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

Vous pouvez maintenant construire le projet, qui enregistrera le contrôle. Lorsque vous insérez le contrôle dans une boîte de dialogue, les propriétés **Data Field** et **Data Source** auront été ajoutées et vous pouvez maintenant sélectionner une source de données et un champ pour afficher dans le contrôle.

## <a name="creating-a-bindable-getset-method"></a><a name="vchowcreatingbindablegetsetmethod"></a>Création d’une méthode Get/Set lisible

En plus d’une méthode d’achat/ensemble de données, vous pouvez également créer une [propriété de stock liant.](#vchowcreatingbindablestockproperty)

> [!NOTE]
> Cette procédure suppose que vous avez un projet de contrôle ActiveX qui sous-classe un contrôle Windows.

#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>Pour ajouter une méthode d’obtenir/ensemble liant à l’aide de l’Assistant De la Propriété Add

1. Chargez votre projet de contrôle.

1. Sur la page **Paramètres de contrôle,** sélectionnez une classe de fenêtre pour que le contrôle sous-classe. Par exemple, vous pouvez sous-classer un contrôle EDIT.

1. Chargez votre projet de contrôle.

1. Cliquez à droite sur le nœud d’interface pour votre contrôle.

   Cela ouvre le menu raccourci.

1. À partir du menu raccourci, cliquez sur **Ajouter** et cliquez ensuite **ajouter la propriété**.

1. Tapez le nom de propriété dans la boîte **de nom de propriété.** Utilisez `MyProp` pour cet exemple.

1. Sélectionnez un type de données dans la case de liste d’abandon **du type de propriété.** Utilisez **court** pour cet exemple.

1. Pour **Type d’implémentation**, cliquez sur **Méthodes Get/Set**.

1. Sélectionnez les cases de cocher suivantes de l’onglet Attributs IDL: **liant**, **demandé**, **displaybind**, et **defaultbind** pour ajouter les attributs à la définition de propriété dans le projet . Fichier IDL. Ces attributs rendent le contrôle visible à l’utilisateur et font de la propriété stock la propriété liant par défaut.

1. Cliquez sur **Terminer**.

1. Modifier le corps `SetMyProp` de la fonction afin qu’il contienne le code suivant :

   [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]

1. Le paramètre `BoundPropertyChanged` transmis `BoundPropertyRequestEdit` à la et les fonctions est l’insipide de la propriété, qui est le paramètre transmis à l’id () attribut pour la propriété dans le . Fichier IDL.

1. Modifier la fonction [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) afin qu’il contienne le code suivant :

   [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

1. Modifier `OnDraw` la fonction afin qu’elle contienne le code suivant :

   [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]

1. À la section publique du fichier d’en-tête du fichier d’en-tête pour votre classe de contrôle, ajoutez les définitions suivantes (constructeurs) pour les variables des membres :

   [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]

1. Faites la ligne suivante la `DoPropExchange` dernière ligne de la fonction :

   [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]

1. Modifier `OnResetState` la fonction afin qu’elle contienne le code suivant :

   [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]

1. Modifier `GetMyProp` la fonction afin qu’elle contienne le code suivant :

   [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]

Vous pouvez maintenant construire le projet, qui enregistrera le contrôle. Lorsque vous insérez le contrôle dans une boîte de dialogue, les propriétés **Data Field** et **Data Source** auront été ajoutées et vous pouvez maintenant sélectionner une source de données et un champ pour afficher dans le contrôle.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)
