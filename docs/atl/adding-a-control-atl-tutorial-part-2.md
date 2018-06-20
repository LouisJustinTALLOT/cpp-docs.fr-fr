---
title: Ajout d’un contrôle (ATL didacticiel, partie 2) | Documents Microsoft
ms.custom: get-started-article
ms.date: 06/18/2018
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c9575a75-1064-41f1-9697-7aada560c669
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1547d48b5b5914d9b32ff8b476b0c007f972067
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238706"
---
# <a name="adding-a-control-atl-tutorial-part-2"></a>Ajout d'un contrôle (Didacticiel ATL, Partie 2)
Dans cette étape, vous ajoutez un contrôle à votre projet, générez-le et tester sur une page Web.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-add-an-object-to-an-atl-project"></a>Pour ajouter un objet à un projet ATL  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le projet de polygone.  
  
2.  Pointez sur **ajouter** dans le menu contextuel, cliquez sur **un nouvel élément** dans le sous-menu.  
  
     La boîte de dialogue **Ajouter un nouvel élément** s’affiche. Les différentes catégories d’objet sont répertoriées dans l’arborescence à gauche.  
  
3.  Cliquez sur le **ATL** dossier.  
  
4.  Dans la liste des modèles à droite, sélectionnez **contrôle ATL**. Cliquez sur **Ajouter**. L’Assistant contrôle ATL s’ouvre et vous pouvez configurer le contrôle.  
  
5.  Type `PolyCtl` comme nom court et notez que les autres champs sont complétés automatiquement. Ne cliquez pas sur **Terminer** encore, car vous devez apporter des modifications.  
  
 L’Assistant contrôle ATL **noms** page contient les champs suivants :  
  
|Champ|Sommaire|  
|-----------|--------------|  
|**Nom court**|Le nom que vous avez entré pour le contrôle.|  
|**Classe**|Le nom de classe C++ créé pour implémenter le contrôle.|  
|**Fichier .h**|Le fichier est créé pour contenir la définition de la classe C++.|  
|**Fichier .cpp**|Le fichier est créé pour contenir l’implémentation de la classe C++.|  
|**Coclasse**|Le nom de la classe de composant pour ce contrôle.|  
|**Interface**|Le nom de l’interface sur laquelle le contrôle implémentera ses méthodes et propriétés personnalisées.|  
|**Type**|Description pour le contrôle.|  
|**ProgID**|Nom lisible qui peut être utilisé pour rechercher le CLSID du contrôle.|  
  
 Vous avez à faire de plusieurs paramètres supplémentaires dans l’Assistant contrôle ATL.  
  
#### <a name="to-enable-support-for-rich-error-information-and-connection-points"></a>Pour activer la prise en charge pour les connexions et les informations d’erreur complètes des points  
  
1.  Cliquez sur **Options** pour ouvrir le **Options** page.  
  
2.  Sélectionnez le **points de connexion** case à cocher. Cela crée la prise en charge pour une interface sortante dans le fichier IDL.  
  
 Vous pouvez également rendre le contrôle pouvant être inséré, ce qui signifie qu’il peut être incorporé dans des applications qui prennent en charge les objets incorporés, tels qu’Excel ou Word.  
  
#### <a name="to-make-the-control-insertable"></a>Pour rendre le contrôle à insérer  
  
1.  Cliquez sur **apparence** pour ouvrir le **apparence** page.  
  
2.  Sélectionnez le **Insertable** case à cocher.  
  
 Le polygone affiché par l’objet aura une couleur de remplissage unie, donc vous devez ajouter un `Fill Color` propriété stock.  
  
#### <a name="to-add-a-fill-color-stock-property-and-create-the-control"></a>Pour ajouter une propriété stock couleur de remplissage et de créer le contrôle  
  
1.  Cliquez sur **Propriétés Stock** pour ouvrir le **Propriétés Stock** page.  
  
2.  Sous **ne pas pris en charge**, faites défiler vers le bas la liste des propriétés stock possibles. Double-cliquez sur `Fill Color` pour le déplacer vers le **pris en charge** liste.  
  
3.  Les options pour le contrôle est terminée. Cliquez sur **Terminer**.  
  
 Comme l’Assistant a créé le contrôle, plusieurs modifications de code et les ajouts de fichiers s’est produite. Les fichiers suivants ont été créés :  
  
|Fichier|Description|  
|----------|-----------------|  
|PolyCtl.h|Contient la plupart de l’implémentation de la classe C++ `CPolyCtl`.|  
|PolyCtl.cpp|Contient les parties restantes du `CPolyCtl`.|  
|PolyCtl.rgs|Un fichier texte qui contient le script de Registre utilisé pour inscrire le contrôle.|  
|PolyCtl.htm|Une page Web contenant une référence au contrôle nouvellement créé.|  
  
 L’Assistant a effectuées également les modifications de code suivantes :  
  
-   Ajouter un `#include` instruction aux fichiers stdafx.h et stdafx.cpp pour inclure la bibliothèque ATL fichiers nécessaire pour prendre en charge des contrôles.  
  
-   Fichier Polygon.idl pour inclure les détails du nouveau contrôle.  
  
-   Ajouté le nouveau contrôle au mappage d’objets dans Polygon.cpp.  
  
 Vous pouvez maintenant générer le contrôle pour le voir en action.  
  
## <a name="building-and-testing-the-control"></a>Génération et test du contrôle  
  
#### <a name="to-build-and-test-the-control"></a>Pour générer et tester le contrôle  
  
1.  Sur le **générer** menu, cliquez sur **générer Polygon**.  
  
     Une fois que le contrôle a terminé la construction, avec le bouton droit PolyCtl.htm dans **l’Explorateur de solutions** et sélectionnez **afficher dans le navigateur**. La page HTML Web contenant le contrôle s’affichera. Vous devez voir une page avec le titre « ATL 8.0 page de test pour l’objet PolyCtl » et le texte **PolyCtl**. Il s’agit de votre contrôle.  
  
> [!NOTE]
>  Lorsque vous aurez terminé ce didacticiel, si vous recevez un message d’erreur dans lequel le fichier DLL ne peut pas être créé, fermez le fichier PolyCtl.htm et le conteneur de Test du contrôle ActiveX et régénérez la solution. Si vous ne pouvez toujours pas créer la DLL, redémarrez l’ordinateur, ou fermez la session (si vous utilisez des Services Terminal Server).  
  
 Ensuite, vous allez ajouter une propriété personnalisée au contrôle.  
  
 [À l’étape 1](../atl/creating-the-project-atl-tutorial-part-1.md) &#124; [à l’étape 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel](../atl/active-template-library-atl-tutorial.md)

