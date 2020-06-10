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
ms.openlocfilehash: 3f16ea3ad77c676695a9d5ca6e2deb10637de455
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621184"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>Contrôles ActiveX MFC : utilisation de la liaison de données dans un contrôle ActiveX

L’une des utilisations les plus puissantes des contrôles ActiveX est la liaison de données, qui permet à une propriété du contrôle d’être liée à un champ spécifique dans une base de données. Lorsqu’un utilisateur modifie des données dans cette propriété liée, le contrôle notifie la base de données et demande que le champ d’enregistrement soit mis à jour. La base de données avertit ensuite le contrôle de la réussite ou de l’échec de la requête.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

Cet article couvre le côté contrôle de votre tâche. L’implémentation des interactions de liaison de données avec la base de données est la responsabilité du conteneur de contrôle. La façon dont vous gérez les interactions de la base de données dans votre conteneur dépasse le cadre de cette documentation. La façon dont vous préparez le contrôle pour la liaison de données est expliquée dans le reste de cet article.

![Diagramme conceptuel d’un contrôle lié à un&#45;de données](../mfc/media/vc374v1.gif "Diagramme conceptuel d’un contrôle lié à un&#45;de données") <br/>
Diagramme conceptuel d’un contrôle lié aux données

La `COleControl` classe fournit deux fonctions membres qui rendent la liaison de données facile à implémenter. La première fonction, [BoundPropertyRequestEdit](reference/colecontrol-class.md#boundpropertyrequestedit), est utilisée pour demander l’autorisation de modifier la valeur de la propriété. [BoundPropertyChanged](reference/colecontrol-class.md#boundpropertychanged), la deuxième fonction, est appelée une fois que la valeur de la propriété a été modifiée avec succès.

Cet article aborde les thèmes suivants :

- [Création d’une propriété stock pouvant être liée](#vchowcreatingbindablestockproperty)

- [Création d’une méthode d’extraction/définition pouvant être liée](#vchowcreatingbindablegetsetmethod)

## <a name="creating-a-bindable-stock-property"></a><a name="vchowcreatingbindablestockproperty"></a>Création d’une propriété stock pouvant être liée

Il est possible de créer une propriété stock liée aux données, bien qu’il soit plus probable que vous souhaitiez une [méthode d’extraction/définition pouvant être liée](#vchowcreatingbindablegetsetmethod).

> [!NOTE]
> Par défaut, les propriétés stock ont les `bindable` `requestedit` attributs et.

#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>Pour ajouter une propriété stock pouvant être liée à l’aide de l’Assistant Ajout de propriété

1. Commencez un projet à l’aide de l' [Assistant contrôle ActiveX MFC](reference/mfc-activex-control-wizard.md).

1. Cliquez avec le bouton droit sur le nœud interface de votre contrôle.

   Le menu contextuel s’ouvre.

1. Dans le menu contextuel, cliquez sur **Ajouter** , puis sur **Ajouter une propriété**.

1. Sélectionnez l’une des entrées dans la liste déroulante nom de la **propriété** . Par exemple, vous pouvez sélectionner du **texte**.

   Étant donné que le **texte** est une propriété stock, les attributs **pouvant être liés** et **modification** sont déjà vérifiés.

1. Activez les cases à cocher suivantes à partir de l’onglet **attributs IDL** : **displaybind** et **defaultbind** pour ajouter les attributs à la définition de propriété dans le du projet. Fichier IDL. Ces attributs rendent le contrôle visible pour l’utilisateur et font de la propriété stock la propriété pouvant être liée par défaut.

À ce stade, votre contrôle peut afficher des données à partir d’une source de données, mais l’utilisateur ne pourra pas mettre à jour les champs de données. Si vous souhaitez que votre contrôle soit également en mesure de mettre à jour les données, modifiez la `OnOcmCommand` fonction [OnOcmCommand](mfc-activex-controls-subclassing-a-windows-control.md) pour qu’elle ressemble à ce qui suit :

[!code-cpp[NVC_MFC_AxData#1](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

Vous pouvez maintenant générer le projet, ce qui permet d’inscrire le contrôle. Lorsque vous insérez le contrôle dans une boîte de dialogue, les propriétés du **champ de données** et de la **source de données** ont été ajoutées. vous pouvez maintenant sélectionner une source de données et un champ à afficher dans le contrôle.

## <a name="creating-a-bindable-getset-method"></a><a name="vchowcreatingbindablegetsetmethod"></a>Création d’une méthode d’extraction/définition pouvant être liée

Outre une méthode d’extraction/définition liée aux données, vous pouvez également créer une [propriété stock pouvant être liée](#vchowcreatingbindablestockproperty).

> [!NOTE]
> Cette procédure suppose que vous disposez d’un projet de contrôle ActiveX qui sous-classe un contrôle Windows.

#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>Pour ajouter une méthode d’extraction/définition pouvant être liée à l’aide de l’Assistant Ajout de propriété

1. Chargez votre projet de contrôle.

1. Sur la page **paramètres du contrôle** , sélectionnez une classe de fenêtre pour la sous-classe du contrôle. Par exemple, vous souhaiterez peut-être sous-classer un contrôle d’édition.

1. Chargez votre projet de contrôle.

1. Cliquez avec le bouton droit sur le nœud interface de votre contrôle.

   Le menu contextuel s’ouvre.

1. Dans le menu contextuel, cliquez sur **Ajouter** , puis sur **Ajouter une propriété**.

1. Tapez le nom de la propriété dans la zone nom de la **propriété** . Utilisez `MyProp` pour cet exemple.

1. Sélectionnez un type de données dans la zone de liste déroulante **type de propriété** . Utilisez **short** pour cet exemple.

1. Pour **Type d’implémentation**, cliquez sur **Méthodes Get/Set**.

1. Activez les cases à cocher suivantes à partir de l’onglet Attributs IDL : **Bindable**, **modification**, **displaybind**et **defaultbind** pour ajouter les attributs à la définition de propriété dans le du projet. Fichier IDL. Ces attributs rendent le contrôle visible pour l’utilisateur et font de la propriété stock la propriété pouvant être liée par défaut.

1. Cliquez sur **Terminer**.

1. Modifiez le corps de la `SetMyProp` fonction afin qu’elle contienne le code suivant :

   [!code-cpp[NVC_MFC_AxData#2](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]

1. Le paramètre passé aux `BoundPropertyChanged` fonctions et `BoundPropertyRequestEdit` est le DISPID de la propriété, qui est le paramètre passé à l’attribut ID () de la propriété dans le. Fichier IDL.

1. Modifiez la fonction [OnOcmCommand](mfc-activex-controls-subclassing-a-windows-control.md) pour qu’elle contienne le code suivant :

   [!code-cpp[NVC_MFC_AxData#1](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

1. Modifiez la `OnDraw` fonction afin qu’elle contienne le code suivant :

   [!code-cpp[NVC_MFC_AxData#3](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]

1. Dans la section publique du fichier d’en-tête fichier d’en-tête pour votre classe de contrôle, ajoutez les définitions suivantes (constructeurs) pour les variables membres :

   [!code-cpp[NVC_MFC_AxData#4](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]

1. Faites de la ligne suivante la dernière ligne de la `DoPropExchange` fonction :

   [!code-cpp[NVC_MFC_AxData#5](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]

1. Modifiez la `OnResetState` fonction afin qu’elle contienne le code suivant :

   [!code-cpp[NVC_MFC_AxData#6](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]

1. Modifiez la `GetMyProp` fonction afin qu’elle contienne le code suivant :

   [!code-cpp[NVC_MFC_AxData#7](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]

Vous pouvez maintenant générer le projet, ce qui permet d’inscrire le contrôle. Lorsque vous insérez le contrôle dans une boîte de dialogue, les propriétés du **champ de données** et de la **source de données** ont été ajoutées. vous pouvez maintenant sélectionner une source de données et un champ à afficher dans le contrôle.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)
