---
title: Ajout d'un contrôle (Didacticiel ATL, Partie 2)
ms.custom: get-started-article
ms.date: 09/26/2018
ms.assetid: c9575a75-1064-41f1-9697-7aada560c669
ms.openlocfilehash: 45841c33ad30ff427f9b792a779d135b4f6e7eca
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283226"
---
# <a name="adding-a-control-atl-tutorial-part-2"></a>Ajout d'un contrôle (Didacticiel ATL, Partie 2)

Dans cette étape, vous ajoutez un contrôle à votre projet, générez-le et testez-la sur une page Web.

## <a name="procedures"></a>Procédures

### <a name="to-add-an-object-to-an-atl-project"></a>Pour ajouter un objet à un projet ATL

1. Dans **l’Explorateur de solutions**, avec le bouton droit le `Polygon` projet.

1. Pointez sur **ajouter** sur le menu contextuel, puis cliquez sur **un nouvel élément** dans le sous-menu.

    La boîte de dialogue **Ajouter un nouvel élément** s’affiche. Les différentes catégories d’objet sont répertoriées dans l’arborescence sur la gauche.

1. Cliquez sur le **ATL** dossier.

1. Dans la liste des modèles sur la droite, sélectionnez **contrôle ATL**. Cliquez sur **Ajouter**. Le **contrôle ATL** Assistant s’ouvre et vous pouvez configurer le contrôle.

1. Type `PolyCtl` comme nom court et notez que les autres champs sont automatiquement complétés. Ne cliquez pas sur **Terminer** encore, le fait d’avoir à apporter des modifications.

Le **contrôle ATL** l’Assistant **noms** page contient les champs suivants :

|Champ|Sommaire|
|-----------|--------------|
|**Nom court**|Le nom que vous avez entré pour le contrôle.|
|**Classe**|Le nom de classe C++ créé pour implémenter le contrôle.|
|**Fichier .h**|Le fichier est créé pour contenir la définition de la classe C++.|
|**Fichier .cpp**|Le fichier est créé pour contenir l’implémentation de la classe C++.|
|**CoClass**|Le nom de la classe de composant pour ce contrôle.|
|**Interface**|Le nom de l’interface sur laquelle le contrôle implémente ses méthodes et propriétés personnalisées.|
|**Type**|Une description pour le contrôle.|
|**ProgID**|Nom lisible qui peut être utilisé pour rechercher le CLSID du contrôle.|

Vous devez effectuer plusieurs paramètres supplémentaires dans le **contrôle ATL** Assistant.

### <a name="to-enable-support-for-rich-error-information-and-connection-points"></a>Pour activer la prise en charge pour les connexions et les informations d’erreur complètes points

1. Cliquez sur **Options** pour ouvrir le **Options** page.

1. Sélectionnez le **points de connexion** case à cocher. Cela créera la prise en charge pour une interface sortante dans le fichier IDL.

Vous pouvez également ajouter des interfaces pour étendre les fonctionnalités du contrôle.

### <a name="to-extend-the-controls-functionality"></a>Pour étendre les fonctionnalités du contrôle

1. Cliquez sur **Interfaces** pour ouvrir le **Interfaces** page.

1. Sélectionnez `IProvideClassInfo2` et cliquez sur le **des** flèche pour la déplacer vers le **pris en charge** liste.

1. Sélectionnez `ISpecifyPropertyPages` et cliquez sur le **des** flèche pour la déplacer vers le **pris en charge** liste.

Vous pouvez également rendre le contrôle insérable, ce qui signifie qu’il peut être incorporé dans des applications qui prennent en charge les objets incorporés, tels qu’Excel ou Word.

### <a name="to-make-the-control-insertable"></a>Pour rendre le contrôle insérable

1. Cliquez sur **apparence** pour ouvrir le **apparence** page.

1. Sélectionnez le **Insertable** case à cocher.

Le polygone affiché par l’objet aura une couleur de remplissage unie, vous devez donc ajouter une `Fill Color` propriété stock.

### <a name="to-add-a-fill-color-stock-property-and-create-the-control"></a>Pour ajouter une propriété stock de couleur de remplissage et créer le contrôle

1. Cliquez sur **Propriétés Stock** pour ouvrir le **Propriétés Stock** page.

1. Sous **ne pas pris en charge**, défiler la liste des propriétés stock possibles. Sélectionnez `Fill Color` et cliquez sur le **des** flèche pour la déplacer vers le **pris en charge** liste.

1. Cela termine les options pour le contrôle. Cliquez sur **Terminer**.

Comme l’Assistant a créé le contrôle, plusieurs modifications de code et les ajouts de fichiers s’est produite. Les fichiers suivants ont été créés :

|Fichier|Description|
|----------|-----------------|
|PolyCtl.h|Contient la majeure partie de l’implémentation de la classe C++ `CPolyCtl`.|
|PolyCtl.cpp|Contient les parties restantes de `CPolyCtl`.|
|PolyCtl.rgs|Un fichier texte qui contient le script de Registre utilisé pour inscrire le contrôle.|
|PolyCtl.htm|Une page Web contenant une référence au contrôle nouvellement créé.|

L’Assistant a effectuées également les modifications de code suivantes :

- Ajouter un `#include` instruction aux fichiers stdafx.h et stdafx.cpp pour inclure la bibliothèque ATL fichiers nécessaire pour prendre en charge des contrôles.

- Polygon.idl modifié pour inclure les détails du nouveau contrôle.

- Ajouté le nouveau contrôle au mappage d’objets dans Polygon.cpp.

Vous pouvez maintenant générer le contrôle pour le voir en action.

## <a name="building-and-testing-the-control"></a>Création et test du contrôle

### <a name="to-build-and-test-the-control"></a>Pour générer et tester le contrôle

1. Sur le **Build** menu, cliquez sur **générer le polygone**.

    Une fois que le contrôle a terminé la création, cliquez sur PolyCtl.htm dans **l’Explorateur de solutions** et sélectionnez **afficher dans le navigateur**. La page HTML Web contenant le contrôle s’affichera. Vous devez voir une page avec le titre « ATL 8.0 page de test pour l’objet PolyCtl » et le texte PolyCtl. Il s’agit de votre contrôle.

> [!NOTE]
> Si le contrôle n’est pas visible, savoir que certains navigateurs nécessitent des réglages de paramètres pour exécuter les contrôles ActiveX. Reportez-vous à la documentation du navigateur sur l’activation des contrôles ActiveX.

> [!NOTE]
> Quand ils auront terminé ce didacticiel, si vous recevez un message d’erreur où le fichier DLL ne peut pas être créé, fermez le fichier PolyCtl.htm et l’ActiveX Control Test container et regénérez la solution. Si vous ne pouvez toujours pas créer la DLL, redémarrez l’ordinateur ou fermez la session (si vous utilisez des Services Terminal Server).

Ensuite, vous allez ajouter une propriété personnalisée au contrôle.

[À l’étape 1](../atl/creating-the-project-atl-tutorial-part-1.md) &#124; [à l’étape 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md)

## <a name="see-also"></a>Voir aussi

[Tutoriel](../atl/active-template-library-atl-tutorial.md)
