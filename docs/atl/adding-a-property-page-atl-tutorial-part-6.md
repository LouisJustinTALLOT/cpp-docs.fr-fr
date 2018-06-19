---
title: Ajout d’une Page de propriétés (ATL didacticiel, partie 6) | Documents Microsoft
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf7f0383697fbc1e23e179936a2616d1d236b5f2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361588"
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>Ajout d'une page de propriétés (Didacticiel ATL, Partie 6)
Pages de propriétés sont implémentées en tant qu’objets COM distincts, et les autoriser à être partagé si nécessaire. Dans cette étape, vous exécuterez les tâches suivantes pour ajouter une page de propriétés au contrôle :  
  
-   Création de la ressource de Page de propriété  
  
-   Ajout d’un Code pour créer et gérer la Page de propriétés  
  
-   Ajout de la Page de propriétés au contrôle  
  
## <a name="creating-the-property-page-resource"></a>Création de la ressource de Page de propriété  
 Pour ajouter une page de propriétés à votre contrôle, utilisez l’Assistant Ajout de classes ATL.  
  
#### <a name="to-add-a-property-page"></a>Pour ajouter une Page de propriétés  
  
1.  Dans l’Explorateur de solutions, cliquez sur le polygone.  
  
2.  Dans le menu contextuel, cliquez sur **ajouter**, puis cliquez sur **ajouter une classe**.  
  
3.  Dans la liste des modèles, sélectionnez **Page de propriétés ATL** et cliquez sur **ajouter**.  
  
4.  Lorsque l’Assistant Page de propriétés ATL apparaît, entrez `PolyProp` comme le **court** nom.  
  
5.  Cliquez sur **chaînes** pour ouvrir le **chaînes** page et entrez **& polygone** comme le **titre**.  
  
     Le **titre** de la propriété page est la chaîne qui apparaît dans l’onglet correspondant à cette page. Le **Chaîne Doc** est une description qui utilise d’un frame de propriété à placer dans une info-bulle état ligne ou l’outil. Notez que le frame de propriété standard actuellement n’utilise pas cette chaîne, donc vous pouvez la laisser avec le contenu par défaut. Vous n’allez pas générer un **fichier d’aide** pour le moment, par conséquent, supprimez l’entrée dans cette zone de texte.  
  
6.  Cliquez sur **Terminer**, et l’objet de page de propriété sera créé.  
  
 Les trois fichiers suivants sont créés :  
  
|Fichier|Description|  
|----------|-----------------|  
|PolyProp.h|Contient la classe C++ `CPolyProp`, qui implémente la page de propriétés.|  
|PolyProp.cpp|Contient le fichier PolyProp.h.|  
|PolyProp.rgs|Le script de Registre qui enregistre l’objet de page de propriétés.|  
  
 Les modifications de code suivantes sont également effectuées :  
  
-   La nouvelle page de propriétés est ajoutée à la table d’entrée d’objet dans Polygon.cpp.  
  
-   La `PolyProp` classe est ajoutée au fichier Polygon.idl.  
  
-   Le nouveau fichier de script de registre PolyProp.rgs est ajouté aux ressources du projet.  
  
-   Un modèle de boîte de dialogue est ajouté à la ressource de projet pour la page de propriétés.  
  
-   Les chaînes de propriétés que vous avez spécifiées sont ajoutées à la table de chaînes de ressources.  
  
 Maintenant, ajoutez les champs que vous souhaitez voir apparaître sur la page de propriétés.  
  
#### <a name="to-add-fields-to-the-property-page"></a>Pour ajouter des champs à la Page de propriétés  
  
1.  Dans l’Explorateur de solutions, double-cliquez sur le fichier de ressources Polygon.rc. Affichage des ressources s’ouvre.  
  
2.  Dans l’affichage des ressources, développez le nœud de la boîte de dialogue et double-cliquez IDD_POLYPROP. Notez que la boîte de dialogue qui s’affiche est vide à l’exception d’une étiquette qui vous demande d’insérer votre contrôle.  
  
3.  Sélectionnez l’étiquette et modifiez-le pour lire `Sides:` en modifiant le **légende** texte dans le **propriétés** fenêtre.  
  
4.  Redimensionner la zone de l’étiquette afin qu’elle s’adapte à la taille du texte.  
  
5.  Faites glisser un contrôle d’édition à partir de la boîte à outils vers la droite de l’étiquette.  
  
6.  Enfin, modifiez le **ID** du contrôle d’édition pour `IDC_SIDES` à l’aide de la fenêtre Propriétés.  
  
 Cette étape termine le processus de création de la ressource de page de propriétés.  
  
## <a name="adding-code-to-create-and-manage-the-property-page"></a>Ajout d’un Code pour créer et gérer la Page de propriétés  
 Maintenant que vous avez créé la ressource de page de propriétés, vous devez écrire le code d’implémentation.  
  
 Tout d’abord, activez la `CPolyProp` classe pour définir le nombre de côtés dans votre objet lors de la **appliquer** bouton est enfoncé.  
  
#### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>Pour modifier la fonction Appliquer pour définir le nombre de côtés  
  
1.  Remplacez le `Apply` fonction dans PolyProp.h avec le code suivant :  
  
     [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]  
  
 Une page de propriétés peut avoir plusieurs clients joints à la fois, donc la `Apply` fonction boucle et appelle `put_Sides` sur chaque client avec la valeur récupérée à partir de la zone d’édition. Vous utilisez la [CComQIPtr](../atl/reference/ccomqiptr-class.md) (classe), qui effectue la `QueryInterface` sur chaque objet pour obtenir le `IPolyCtl` à partir de l’interface le **IUnknown** interface (stockées dans le `m_ppUnk` tableau).  
  
 Le code vérifie désormais ce paramètre la `Sides` propriété effectivement travaillée. En cas d’échec, le code affiche une boîte de message affiche les détails d’erreur à partir de la **IErrorInfo** interface. En règle générale, un conteneur interroge un objet pour le **ISupportErrorInfo** interface et les appels `InterfaceSupportsErrorInfo` première, afin de déterminer si l’objet prend en charge les informations d’erreur de paramètre. Vous pouvez ignorer cette tâche.  
  
 [CComPtr](../atl/reference/ccomptr-class.md) vous aide à en gérant automatiquement le décompte de références, vous n’avez pas besoin d’appeler `Release` sur l’interface. `CComBSTR` vous aide à avec `BSTR` du traitement, donc vous n’avez pas à effectuer la dernière `SysFreeString` appeler. Vous utiliser l’une des classes de conversion de chaîne différentes, vous pouvez convertir le `BSTR` si nécessaire (c’est pourquoi le `USES_CONVERSION` macro est au début de la fonction).  
  
 Vous devez également définir l’indicateur de changement de la page de propriété pour indiquer que le **appliquer** bouton doit être activé. Cela se produit lorsque l’utilisateur modifie la valeur dans la **côtés** zone d’édition.  
  
#### <a name="to-handle-the-apply-button"></a>Pour traiter le bouton Appliquer  
  
1.  Dans l’affichage de classes, avec le bouton droit CPolyProp, puis cliquez sur **propriétés** dans le menu contextuel.  
  
2.  Dans la fenêtre Propriétés, cliquez sur le **événements** icône.  
  
3.  Développez le `IDC_SIDES` nœud dans la liste des événements.  
  
4.  Sélectionnez `EN_CHANGE`et dans le menu déroulant situé à droite, cliquez sur  **\<Ajouter > OnEnChangeSides**. Le `OnEnChangeSides` déclaration du gestionnaire sera ajoutée à Polyprop.h et l’implémentation du gestionnaire à Polyprop.cpp.  
  
 Ensuite, vous allez modifier le gestionnaire.  
  
#### <a name="to-modify-the-onenchangesides-method"></a>Pour modifier la méthode OnEnChangeSides  
  
1.  Ajoutez le code suivant dans Polyprop.cpp à la `OnEnChangeSides` (méthode) (la suppression de tout code de l’Assistant) :  
  
     [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]  
  
 `OnEnChangeSides` sera appelée lorsque un **WM_COMMAND** message est envoyé avec la **EN_CHANGE** notification pour le `IDC_SIDES` contrôle. `OnEnChangeSides` appelle ensuite `SetDirty` et passe `TRUE` pour indiquer la propriété de la page est désormais incorrecte et **appliquer** bouton doit être activé.  
  
## <a name="adding-the-property-page-to-the-control"></a>Ajout de la Page de propriétés au contrôle  
 L’Assistant Ajout de classes ATL et l’Assistant Page de propriétés ATL n’ajoutent pas la page de propriétés à votre contrôle pour vous automatiquement, car il peut y avoir plusieurs contrôles dans votre projet. Vous devez ajouter une entrée au mappage de propriété du contrôle.  
  
#### <a name="to-add-the-property-page"></a>Pour ajouter la page de propriétés  
  
1.  Ouvrez PolyCtl.h et ajoutez cette ligne à la table de propriétés :  
  
     [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]  
  
 Mappage de propriété du contrôle ressemble maintenant à ceci :  
  
 [!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]  
  
 Vous auriez pu ajouter un `PROP_PAGE` macro avec le CLSID de votre page de propriétés, mais si vous utilisez la `PROP_ENTRY` macro comme indiqué, le `Sides` valeur de la propriété est également enregistrée lorsque le contrôle est enregistré.  
  
 Les trois paramètres à la macro sont la description de la propriété, le DISPID de la propriété et le CLSID de la page de propriétés qui comporte la propriété. Cela est utile si, par exemple, vous chargez le contrôle dans Visual Basic et définissez le nombre de côtés au moment du design. Étant donné que le nombre de côtés est enregistré, lorsque vous rechargez votre projet Visual Basic, le nombre de côtés sera restauré.  
  
## <a name="building-and-testing-the-control"></a>Génération et test du contrôle  
 Maintenant générer ce contrôle et insérez-le dans ActiveX Control Test Container. Dans le conteneur de Test, sur le **modifier** menu, cliquez sur **objet classe PolyCtl**. La page de propriétés s’affiche. Cliquez sur le **polygone** onglet.  
  
 Le **appliquer** bouton est désactivé initialement. Commencez à taper une valeur dans la **côtés** boîte et **appliquer** bouton est activé. Après avoir entré la valeur, cliquez sur le **appliquer** bouton. Les modifications d’affichage de contrôle et le **appliquer** bouton est désactivé à nouveau. Essayez d’entrer une valeur non valide. Vous verrez une boîte de message contenant la description d’erreur que vous définissez à partir de la `put_Sides` (fonction).  
  
 Ensuite, vous allez placer votre contrôle sur une page Web.  
  
 [À l’étape 5](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [à l’étape 7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel](../atl/active-template-library-atl-tutorial.md)

