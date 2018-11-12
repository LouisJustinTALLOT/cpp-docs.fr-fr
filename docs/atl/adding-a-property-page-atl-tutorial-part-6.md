---
title: Ajout d'une page de propriétés (Didacticiel ATL, Partie 6)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
ms.openlocfilehash: bd9386395b0655eab68a6c772c8d6216b7eeafe5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519481"
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>Ajout d'une page de propriétés (Didacticiel ATL, Partie 6)

Pages de propriétés sont implémentées comme des objets COM séparés, qui lui permettront d’être partagé si nécessaire. Dans cette étape, vous exécuterez les tâches suivantes pour ajouter une page de propriétés au contrôle :

- Création de la ressource de Page de propriété

- Ajout de Code pour créer et gérer la Page de propriétés

- Ajout de la Page de propriétés au contrôle

## <a name="creating-the-property-page-resource"></a>Création de la ressource de Page de propriété

Pour ajouter une page de propriétés à votre contrôle, utilisez le modèle de Page de propriétés ATL.

### <a name="to-add-a-property-page"></a>Pour ajouter une Page de propriétés

1. Dans **l’Explorateur de solutions**, avec le bouton droit `Polygon`.

1. Dans le menu contextuel, cliquez sur **ajouter** > **un nouvel élément**.

1. Dans la liste des modèles, sélectionnez **ATL** > **Page de propriétés ATL** et cliquez sur **ajouter**.

1. Lorsque le **Assistant Page de propriétés ATL** s’affiche, entrez *PolyProp* en tant que le **court** nom.

1. Cliquez sur **chaînes** pour ouvrir le **chaînes** page et entrez **& polygone** en tant que le **titre**.

   Le **titre** de la propriété page est la chaîne qui apparaît dans l’onglet correspondant à cette page. Le **Chaîne Doc** est une description qui utilise d’un frame de propriété à placer dans une info-bulle état ligne ou outil. Notez que le frame de propriété standard actuellement n’utilise pas cette chaîne, vous pouvez donc laisser il avec le contenu par défaut. Vous n’allez pas générer un **fichier d’aide** pour le moment, par conséquent, supprimez l’entrée dans cette zone de texte.

1. Cliquez sur **Terminer**, et l’objet de page de propriété sera créé.

Les trois fichiers suivants sont créés :

|Fichier|Description|
|----------|-----------------|
|PolyProp.h|Contient la classe C++ `CPolyProp`, qui implémente la page de propriétés.|
|PolyProp.cpp|Contient le fichier PolyProp.h.|
|PolyProp.rgs|Le script de Registre qui enregistre l’objet de page de propriétés.|

Les modifications de code suivantes sont également effectuées :

- La nouvelle page de propriété est ajoutée à la table d’entrée objets dans Polygon.cpp.

- Le `PolyProp` classe est ajoutée au fichier Polygon.idl.

- Le nouveau fichier de script de registre PolyProp.rgs est ajouté à la ressource de projet.

- Un modèle de boîte de dialogue est ajouté à la ressource de projet pour la page de propriétés.

- Les chaînes de propriété que vous avez spécifiés sont ajoutés à la table de chaînes de ressources.

Ajoutez maintenant les champs que vous souhaitez voir apparaître sur la page de propriétés.

### <a name="to-add-fields-to-the-property-page"></a>Pour ajouter des champs à la Page de propriétés

1. Dans **l’Explorateur de solutions**, double-cliquez sur le fichier de ressources Polygon.rc. Ceci ouvrira **affichage des ressources**.

1. Dans **affichage des ressources**, développez le `Dialog` nœud et double-cliquez sur `IDD_POLYPROP`. Notez que la boîte de dialogue qui s’affiche est vide à l’exception d’une étiquette qui vous demande d’insérer vos contrôles ici.

1. Sélectionnez l’étiquette et modifiez-le pour lire `Sides:` en modifiant le **légende** texte dans le **propriétés** fenêtre.

1. Redimensionner la zone d’étiquette afin qu’elle s’adapte la taille du texte.

1. Faites glisser un **Edit Control** à partir de la **boîte à outils** à droite de l’étiquette.

1. Enfin, changez le **ID** du contrôle d’édition à `IDC_SIDES` à l’aide de la **propriétés** fenêtre.

Cette étape termine le processus de création de la ressource de page de propriétés.

## <a name="adding-code-to-create-and-manage-the-property-page"></a>Ajout de Code pour créer et gérer la Page de propriétés

Maintenant que vous avez créé la ressource de page de propriété, vous devez écrire le code d’implémentation.

Tout d’abord activer le `CPolyProp` classe pour définir le nombre de côtés dans votre objet lors de la **appliquer** bouton est enfoncé.

### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>Pour modifier la fonction Appliquer pour définir le nombre de côtés

1. Remplacez le `Apply` fonction dans PolyProp.h avec le code suivant :

    [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]

Une page de propriété peut avoir plusieurs clients attachées à la fois, par conséquent, le `Apply` fonction boucle et appelle `put_Sides` sur chaque client avec la valeur récupérée à partir de la zone d’édition. Vous utilisez le [CComQIPtr](../atl/reference/ccomqiptr-class.md) (classe), qui effectue la `QueryInterface` sur chaque objet pour obtenir le `IPolyCtl` interface à partir de la `IUnknown` interface (stockées dans le `m_ppUnk` tableau).

Le code vérifie maintenant ce paramètre la `Sides` propriété réellement travaillée. En cas d’échec, le code affiche une boîte de message affiche les détails d’erreur à partir de la `IErrorInfo` interface. En règle générale, un conteneur demande à un objet pour le `ISupportErrorInfo` interface et les appels `InterfaceSupportsErrorInfo` tout d’abord, pour déterminer si l’objet prend en charge les informations d’erreur de paramètre. Vous pouvez ignorer cette tâche.

[CComPtr](../atl/reference/ccomptr-class.md) vous aide à en gérant automatiquement le décompte, donc vous n’avez pas besoin d’appeler `Release` sur l’interface. `CComBSTR` vous aide à vous avec traitement BSTR, donc vous n’avez pas à effectuer la dernière `SysFreeString` appeler. Vous également utiliser une des classes de conversion de chaîne différentes, vous pouvez convertir le BSTR si nécessaire (c’est la raison pour laquelle la macro USES_CONVERSION est au début de la fonction).

Vous devez également définir l’indicateur de changement de la page de propriété pour indiquer que le **appliquer** bouton doit être activé. Cela se produit lorsque l’utilisateur modifie la valeur dans le **côtés** zone d’édition.

### <a name="to-handle-the-apply-button"></a>Pour gérer le bouton Appliquer

1. Dans **affichage de classes**, avec le bouton droit `CPolyProp` et cliquez sur **propriétés** dans le menu contextuel.

1. Dans le **propriétés** fenêtre, cliquez sur le **événements** icône.

1. Développez le `IDC_SIDES` nœud dans la liste des événements.

1. Sélectionnez `EN_CHANGE`, dans le menu déroulant à droite, cliquez sur  **\<Ajouter > OnEnChangeSides**. Le `OnEnChangeSides` déclaration de gestionnaire sera ajoutée à Polyprop.h et l’implémentation du gestionnaire à Polyprop.cpp.

Ensuite, vous allez modifier le gestionnaire.

### <a name="to-modify-the-onenchangesides-method"></a>Pour modifier la méthode OnEnChangeSides

1. Ajoutez le code suivant dans Polyprop.cpp à la `OnEnChangeSides` (méthode) (en supprimant tout code de l’Assistant) :

    [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]

`OnEnChangeSides` est appelée lorsqu’un `WM_COMMAND` message est envoyé avec la `EN_CHANGE` notification pour le `IDC_SIDES` contrôle. `OnEnChangeSides` appelle ensuite `SetDirty` et passe la valeur TRUE pour indiquer la page de propriétés a été modifiée et le **appliquer** bouton doit être activé.

## <a name="adding-the-property-page-to-the-control"></a>Ajout de la Page de propriétés au contrôle

L’Assistant et le modèle de Page de propriétés ATL n’ajoutent pas la page de propriétés à votre contrôle pour vous automatiquement, car il existe plusieurs contrôles dans votre projet. Vous devez ajouter une entrée au mappage des propriétés du contrôle.

### <a name="to-add-the-property-page"></a>Pour ajouter la page de propriétés

1. Ouvrez PolyCtl.h et ajoutez ces lignes au mappage de propriété :

    [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]

Mappage des propriétés du contrôle ressemble maintenant à ceci :

[!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]

Vous auriez pu ajouter un `PROP_PAGE` macro avec le CLSID de votre page de propriétés, mais si vous utilisez le `PROP_ENTRY` macro comme indiqué, le `Sides` valeur de propriété est également enregistrée lorsque le contrôle est enregistré.

Les trois paramètres dans la macro sont la description de la propriété, le DISPID de la propriété et le CLSID de la page de propriété qui possède la propriété dessus. Cela est utile si, par exemple, vous chargez le contrôle dans Visual Basic et définissez le nombre de côtés au moment du design. Étant donné que le nombre de côtés est enregistré lorsque vous rechargez votre projet Visual Basic, le nombre de côtés sera restauré.

## <a name="building-and-testing-the-control"></a>Création et test du contrôle

Maintenant générer ce contrôle et insérez-le dans ActiveX Control Test Container. Dans **Test Container**, dans le **modifier** menu, cliquez sur **objet classe PolyCtl**. La page de propriétés s’affiche avec les informations que vous avez ajouté.

Le **appliquer** bouton est désactivé initialement. Commencez à taper une valeur dans le **côtés** boîte et le **appliquer** bouton est activé. Une fois que vous avez terminé d’entrer la valeur, cliquez sur le **appliquer** bouton. Les modifications d’affichage de contrôle et le **appliquer** bouton est désactivé à nouveau. Essayez d’entrer une valeur non valide. Vous verrez une boîte de message contenant la description d’erreur que vous définissez à partir de la `put_Sides` (fonction).

Ensuite, vous allez placer votre contrôle sur une page Web.

[À l’étape 5](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [à étape 7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)

## <a name="see-also"></a>Voir aussi

[Didacticiel](../atl/active-template-library-atl-tutorial.md)
