---
title: Ajout d'un contrôle (Didacticiel ATL, Partie 2)
ms.custom: get-started-article
ms.date: 08/19/2019
ms.assetid: c9575a75-1064-41f1-9697-7aada560c669
ms.openlocfilehash: b7952f42b24c4211a2c44ea71fd17e4f65c3421a
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630708"
---
# <a name="adding-a-control-atl-tutorial-part-2"></a>Ajout d'un contrôle (Didacticiel ATL, Partie 2)

Au cours de cette étape, vous allez ajouter un contrôle à votre projet, le générer et le tester sur une page Web.

## <a name="procedures"></a>Procédures

### <a name="to-add-an-object-to-an-atl-project"></a>Pour ajouter un objet à un projet ATL

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet `Polygon`.

1. Pointez sur **Ajouter** dans le menu contextuel, puis cliquez sur **nouvel élément** dans le sous-menu.

    La boîte de dialogue **Ajouter un nouvel élément** s’affiche. Les différentes catégories d’objets sont répertoriées dans l’arborescence à gauche.

1. Cliquez sur le dossier **ATL** .

1. Dans la liste des modèles sur la droite, sélectionnez **contrôle ATL**. Cliquez sur **Ajouter**. L’Assistant **contrôle ATL** s’ouvre et vous pouvez configurer le contrôle.

1. Tapez `PolyCtl` comme nom abrégé et notez que les autres champs sont automatiquement complétés. Ne cliquez pas encore sur **Terminer** , car vous devez apporter d’autres modifications.

La page **noms** de l’Assistant **contrôle ATL** contient les champs suivants:

|Champ|Sommaire|
|-----------|--------------|
|**Nom court**|Nom que vous avez entré pour le contrôle.|
|**Classe**|Nom C++ de classe créé pour implémenter le contrôle.|
|**Fichier .h**|Fichier créé pour contenir la définition de la C++ classe.|
|**Fichier .cpp**|Fichier créé pour contenir l’implémentation de la C++ classe.|
|**CoClass**|Nom de la classe de composant pour ce contrôle.|
|**Interface**|Nom de l’interface sur laquelle le contrôle implémente ses propriétés et méthodes personnalisées.|
|**Type**|Description du contrôle.|
|**ProgID**|Nom lisible qui peut être utilisé pour rechercher le CLSID du contrôle.|

Vous trouverez plusieurs paramètres supplémentaires qui doivent être modifiés dans l’Assistant **contrôle ATL** .

### <a name="to-enable-support-for-rich-error-information-and-connection-points"></a>Pour activer la prise en charge des informations d’erreur et des points de connexion enrichis

1. Cliquez sur **options** pour ouvrir la page **options** .

1. Activez la case à cocher **points de connexion** . Cette option crée la prise en charge d’une interface sortante dans le fichier IDL.

Vous pouvez également ajouter des interfaces pour étendre les fonctionnalités du contrôle.

### <a name="to-extend-the-controls-functionality"></a>Pour étendre les fonctionnalités du contrôle

1. Cliquez sur **interfaces** pour ouvrir la page **interfaces** .

1. Sélectionnez `IProvideClassInfo2` et cliquez sur la flèche vers le **haut** pour la déplacer vers la liste **pris en charge** .

1. Sélectionnez `ISpecifyPropertyPages` et cliquez sur la flèche vers le **haut** pour la déplacer vers la liste **pris en charge** .

Vous pouvez également rendre le contrôle pouvant être *inséré*, ce qui signifie qu’il peut être incorporé dans des applications qui prennent en charge des objets incorporés, tels qu’Excel ou Word.

### <a name="to-make-the-control-insertable"></a>Pour rendre le contrôle

1. Cliquez sur **apparence** pour ouvrir la page **apparence** .

1. Activez la case à cocher à **Insérer** .

Le polygone affiché par l’objet aura une couleur de remplissage unie. vous devez donc ajouter une `Fill Color` propriété stock.

### <a name="to-add-a-fill-color-stock-property-and-create-the-control"></a>Pour ajouter une propriété stock de couleur de remplissage et créer le contrôle

1. Cliquez sur **stock Properties** pour ouvrir la page de **propriétés stock** .

1. Sous **non pris en charge**, faites défiler la liste des propriétés stock possibles. Sélectionnez `Fill Color` et cliquez sur la flèche vers le **haut** pour la déplacer vers la liste **pris en charge** .

1. Choisissez **Terminer**.

Lorsque l’Assistant crée le contrôle, plusieurs modifications de code et ajouts de fichiers se produisent. Les fichiers suivants sont créés:

|Fichier|Description|
|----------|-----------------|
|PolyCtl. h|Contient la plus grande partie de l' C++ implémentation `CPolyCtl`de la classe.|
|PolyCtl.cpp|Contient les parties restantes de `CPolyCtl`.|
|PolyCtl.rgs|Fichier texte qui contient le script de registre utilisé pour inscrire le contrôle.|
|PolyCtl. htm|Page Web contenant une référence au contrôle nouvellement créé.|

L’Assistant effectue également les modifications de code suivantes:

- Ajoute une `#include` instruction aux fichiers d’en-tête précompilés pour inclure les fichiers ATL nécessaires à la prise en charge des contrôles.

- Modifie Polygon. idl pour inclure les détails du nouveau contrôle.

- Ajoute le nouveau contrôle à la table d’objets dans Polygon. cpp.

Vous pouvez maintenant générer le contrôle pour le voir en action.

## <a name="building-and-testing-the-control"></a>Création et test du contrôle

### <a name="to-build-and-test-the-control"></a>Pour générer et tester le contrôle

1. Dans le menu **générer** , cliquez sur **générer un polygone**.

    Une fois la génération du contrôle terminée, cliquez avec le bouton droit sur PolyCtl. htm dans **Explorateur de solutions** , puis sélectionnez **afficher dans le navigateur**. La page Web HTML contenant le contrôle s’affiche. Vous devez voir une page intitulée «ATL 8,0 test page pour l’objet PolyCtl» et votre contrôle, le texte PolyCtl.

> [!NOTE]
> Si le contrôle n’est pas visible, sachez que certains navigateurs nécessitent des ajustements de paramètres pour exécuter les contrôles ActiveX. Reportez-vous à la documentation du navigateur sur l’activation des contrôles ActiveX.

> [!NOTE]
> Lorsque vous aurez terminé ce didacticiel, si vous recevez un message d’erreur indiquant que le fichier DLL ne peut pas être créé, fermez le fichier PolyCtl. htm et le conteneur ActiveX Control Test, puis générez à nouveau la solution. Si vous ne pouvez toujours pas créer la DLL, redémarrez l’ordinateur ou fermez la session si vous utilisez les services Terminal Server.

Ensuite, vous allez ajouter une propriété personnalisée au contrôle.

[Retour à l’étape 1](../atl/creating-the-project-atl-tutorial-part-1.md) &#124; À l' [étape 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md)

## <a name="see-also"></a>Voir aussi

[Tutoriel](../atl/active-template-library-atl-tutorial.md)
