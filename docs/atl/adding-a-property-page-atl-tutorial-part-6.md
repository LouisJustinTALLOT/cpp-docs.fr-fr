---
title: Ajout d'une page de propriétés (Didacticiel ATL, Partie 6)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
ms.openlocfilehash: 2c487d1446f5d1050868f2066359e9639f474ba3
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524683"
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>Ajout d'une page de propriétés (Didacticiel ATL, Partie 6)

> [!NOTE] 
> L’Assistant Fournisseur OLE DB ATL n’est pas disponible dans Visual Studio 2019 et versions ultérieures.

Les pages de propriétés sont implémentées en tant qu’objets COM distincts, ce qui leur permet d’être partagées si nécessaire. Au cours de cette étape, vous allez exécuter les tâches suivantes pour ajouter une page de propriétés au contrôle :

- Création de la ressource de page de propriétés

- Ajout du code nécessaire pour créer et gérer la page de propriétés

- Ajout de la page de propriétés au contrôle

## <a name="creating-the-property-page-resource"></a>Création de la ressource de page de propriétés

Pour ajouter une page de propriétés à votre contrôle, utilisez le modèle de page de propriétés ATL.

### <a name="to-add-a-property-page"></a>Pour ajouter une page de propriétés

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur `Polygon`.

1. Dans le menu contextuel, cliquez sur **Ajouter** > **Nouvel élément**.

1. Dans la liste des modèles, sélectionnez **ATL** > **Page de propriétés ATL** et cliquez sur **Ajouter**.

1. Lorsque **l’Assistant Page de propriétés ATL** s’affiche, entrez *PolyProp* dans le champ **Nom court**.

1. Cliquez sur **Chaînes** pour ouvrir la page **Chaînes** et entrez **&Polygon** dans le champ **Titre**.

   Le **titre** de la page de propriétés est la chaîne qui apparaît dans l’onglet correspondant à cette page. La **chaîne doc** est une description qu’un frame de propriété utilise pour placer une ligne d’état ou une info-bulle. Notez qu’actuellement le frame de propriété standard n’utilise pas cette chaîne, vous pouvez donc conserver son contenu par défaut. Vous n’allez pas générer de **fichier d’aide** pour le moment, vous pouvez donc supprimer l’entrée dans cette zone de texte.

1. Cliquez sur **Terminer** pour que l’objet de page de propriétés soit créé.

Les trois fichiers suivants sont créés :

|Fichier|Description|
|----------|-----------------|
|PolyProp.h|Contient la classe C++ `CPolyProp` qui implémente la page de propriétés.|
|PolyProp.cpp|Contient le fichier PolyProp.h.|
|PolyProp.rgs|Le script de registre qui enregistre l’objet de page de propriétés.|

Les modifications suivantes sont également apportées au code :

- La nouvelle page de propriétés est ajoutée au mappage des entrées d’objets dans Polygon.cpp.

- La classe `PolyProp` est ajoutée au fichier Polygon.idl.

- Le nouveau fichier de script de registre PolyProp.rgs est ajouté à la ressource du projet.

- Un modèle de boîte de dialogue est ajouté à la ressource du projet pour la page de propriétés.

- Les chaînes de la propriété que vous avez spécifiées sont ajoutées à la table de chaînes de la ressource.

Ajoutez maintenant les champs que vous souhaitez afficher sur la page de propriétés.

### <a name="to-add-fields-to-the-property-page"></a>Pour ajouter des champs à la page de propriétés

1. Dans **l’Explorateur de solutions**, double-cliquez sur le fichier de ressources Polygon.rc. Cela permet d’ouvrir **Affichage des ressources**.

1. Dans **Affichage des ressources**, développez le nœud `Dialog` et double-cliquez sur `IDD_POLYPROP`. Notez que la boîte de dialogue qui s’affiche est vide, à l’exception d’une étiquette qui vous demande d’insérer vos contrôles ici.

1. Sélectionnez cette étiquette et modifiez-la pour lire `Sides:` en modifiant le texte dans **Légende** de la fenêtre **Propriétés**.

1. Redimensionnez la zone d’étiquette pour qu’elle corresponde à la taille du texte.

1. Faites glisser un **contrôle d’édition** de la **boîte à outils** vers le côté droit de l’étiquette.

1. Enfin, changez **l’ID** du contrôle d’édition en `IDC_SIDES` à l’aide de la fenêtre **Propriétés**.

Le processus de création de la ressource de page de propriétés est maintenant terminé.

## <a name="adding-code-to-create-and-manage-the-property-page"></a>Ajout du code nécessaire pour créer et gérer la page de propriétés

Maintenant que vous avez créé la ressource de la page de propriétés, vous devez écrire le code d’implémentation.

Commencez par activer la classe `CPolyProp` pour définir le nombre de côtés de votre objet lors de l’appui sur le bouton **Appliquer**.

### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>Pour modifier la fonction Appliquer pour définir le nombre de côtés

1. Remplacez la fonction `Apply` dans PolyProp.h par le code suivant :

    [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]

Plusieurs clients peuvent être attachés à une page de propriétés ; par conséquent, la fonction `Apply` crée des boucles autour et appelle `put_Sides` sur chaque client avec la valeur récupérée du champ de modification. Vous utilisez la classe [CComQIPtr](../atl/reference/ccomqiptr-class.md), qui effectue l’opération `QueryInterface` sur chaque objet pour obtenir l’interface `IPolyCtl` à partir de l’interface `IUnknown` (stockée dans le tableau `m_ppUnk`).

Le code vérifie maintenant que la définition de la propriété `Sides` a bien fonctionné. En cas d’échec, le code affiche une boîte de message qui indique les détails de l’erreur de l’interface `IErrorInfo`. En règle générale, un conteneur demande l’interface `ISupportErrorInfo` à un objet et commence par appeler `InterfaceSupportsErrorInfo` pour déterminer si l’objet prend en charge la définition des informations de l’erreur. Vous pouvez ignorer cette tâche.

[CComPtr](../atl/reference/ccomptr-class.md) vous aide en gérant automatiquement le nombre de références ; vous n’avez donc pas besoin d’appeler `Release` sur l’interface. `CComBSTR` vous aide avec le traitement BSTR ; vous n’avez donc pas besoin d’effectuer le dernier appel `SysFreeString`. Vous pouvez également utiliser l’une des différentes classes de conversion de chaîne de façon à pouvoir convertir le BSTR si nécessaire (c’est la raison pour laquelle la macro USES_CONVERSION se trouve au début de la fonction).

Vous devez également définir l’indicateur modifié de la page de propriétés pour signaler que le bouton **Appliquer** doit être activé. Cela se produit lorsque l’utilisateur modifie la valeur dans le champ de modification **Côtés**.

### <a name="to-handle-the-apply-button"></a>Pour gérer le bouton Appliquer

1. Dans **Affichage de classes**, cliquez avec le bouton droit sur `CPolyProp` et cliquez sur **Propriétés** dans le menu contextuel.

1. Dans la fenêtre **Propriétés**, cliquez sur l’icône **Événements**.

1. Développez le nœud `IDC_SIDES` dans la liste des événements.

1. Sélectionnez `EN_CHANGE` et cliquez sur **\<Ajouter > OnEnChangeSides** dans le menu déroulant à droite. La déclaration du gestionnaire `OnEnChangeSides` est ajoutée à Polyprop.h, et l’implémentation du gestionnaire à Polyprop.cpp.

Ensuite, vous allez modifier le gestionnaire.

### <a name="to-modify-the-onenchangesides-method"></a>Pour modifier la méthode OnEnChangeSides

1. Ajoutez le code suivant dans Polyprop.cpp à la méthode `OnEnChangeSides` (en supprimant le code placé par l’Assistant) :

    [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]

`OnEnChangeSides` est appelé lorsqu’un message `WM_COMMAND` est envoyé avec la notification `EN_CHANGE` pour le contrôle `IDC_SIDES`. `OnEnChangeSides` appelle ensuite `SetDirty` et transmet la valeur TRUE pour indiquer que la page de propriétés est modifiée et que le bouton **Appliquer** doit être activé.

## <a name="adding-the-property-page-to-the-control"></a>Ajout de la page de propriétés au contrôle

L’Assistant et le modèle de page de propriétés ATL n’ajoutent pas automatiquement la page de propriétés à votre contrôle, car il peut y avoir plusieurs contrôles dans votre projet. Vous devez ajouter une entrée au mappage des propriétés du contrôle.

### <a name="to-add-the-property-page"></a>Pour ajouter la page de propriétés

1. Ouvrez PolyCtl.h et ajoutez ces lignes au mappage de propriétés :

    [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]

La mappage de propriétés du contrôle ressemble maintenant à ce qui suit :

[!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]

Vous auriez pu ajouter une macro `PROP_PAGE` au CLSID de votre page de propriétés, mais si vous utilisez la macro `PROP_ENTRY` comme indiqué, la valeur de propriété `Sides` est également enregistrée lorsque le contrôle est enregistré.

Les trois paramètres dans la macro sont la description de la propriété, le DISPID de la propriété et le CLSID de la page de propriétés sur laquelle se trouve la propriété. Cela est utile si, par exemple, vous chargez le contrôle dans Visual Basic et définissez le nombre de côtés au moment de la conception. Puisque le nombre de côtés est enregistré, lorsque vous rechargez votre projet Visual Basic, le nombre de côtés est restauré.

## <a name="building-and-testing-the-control"></a>Création et test du contrôle

Créez maintenant ce contrôle et insérez-le dans le conteneur de test de contrôles ActiveX. Dans **Test Container** (Conteneur de test), dans le menu **Édition**, cliquez sur **PolyCtl Class Object** (Objet de classe PolyCtl). La page de propriétés s’affiche avec les informations que vous avez ajoutées.

Le bouton **Appliquer** est initialement désactivé. Commencez à taper une valeur dans le champ **Côtés** et le bouton **Appliquer** va s’activer. Après avoir entré la valeur, cliquez sur le bouton **Appliquer**. L’affichage du contrôle est modifié, et le bouton **Appliquer** est encore désactivé. Essayez d’entrer une valeur non valide. Une boîte de message contenant la description de l’erreur que vous avez définie dans la fonction `put_Sides` s’affiche.

Ensuite, vous allez placer votre contrôle sur une page Web.

[Revenir à l’étape 5](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [Passer à l’étape 7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)

## <a name="see-also"></a>Voir aussi

[Tutoriel](../atl/active-template-library-atl-tutorial.md)
