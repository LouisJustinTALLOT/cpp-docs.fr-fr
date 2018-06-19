---
title: La modification du Code de dessin (ATL didacticiel, partie 4) | Documents Microsoft
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c077aca8c3276fac963eda8cdd2c413a9d6d5f5b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358910"
---
# <a name="changing-the-drawing-code-atl-tutorial-part-4"></a>Changement du code de dessin (Didacticiel ATL, partie 4)
Par défaut, code de dessin du contrôle affiche un carré et le texte **PolyCtl**. Dans cette étape, vous allez modifier le code pour afficher plus intéressant. Les tâches suivantes sont impliquées :  
  
-   Modification du fichier d’en-tête  
  
-   Modification de la `OnDraw` (fonction)  
  
-   Ajout d’une méthode pour calculer les Points du polygone  
  
-   L’initialisation de la couleur de remplissage  
  
## <a name="modifying-the-header-file"></a>Modification du fichier d’en-tête  
 Commencez par ajouter la prise en charge pour les fonctions mathématiques `sin` et `cos`, qui sera utilisée calculer les points du polygone et en créant un tableau pour stocker les positions.  
  
#### <a name="to-modify-the-header-file"></a>Pour modifier le fichier d’en-tête  
  
1.  Ajoutez la ligne `#include <math.h>` au début du PolyCtl.h. En haut du fichier doit ressembler à ceci :  
  
     [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]  
  
2.  Une fois que les points du polygone sont calculés, ils sont stockés dans un tableau de type `POINT`, par conséquent, ajoutez la baie après la définition de `m_nSides` dans PolyCtl.h :  
  
     [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_2.h)]  
  
## <a name="modifying-the-ondraw-method"></a>Modification de la méthode OnDraw  
 Maintenant que vous devez modifier le `OnDraw` méthode dans PolyCtl.h. Le code que vous allez ajouter crée un nouveau stylet et le pinceau utilisé dessiner votre polygone et appelle ensuite la `Ellipse` et `Polygon` les fonctions API Win32 pour effectuer le dessin proprement dit.  
  
#### <a name="to-modify-the-ondraw-function"></a>Pour modifier la fonction OnDraw  
  
1.  Remplacer la `OnDraw` méthode dans PolyCtl.h avec le code suivant :  
  
     [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]  
  
## <a name="adding-a-method-to-calculate-the-polygon-points"></a>Ajout d’une méthode pour calculer les Points du polygone  
 Ajoutez une méthode appelée `CalcPoints`, qui calcule les coordonnées des points qui composent le périmètre du polygone. Ces calculs doit reposer sur la variable RECT qui est passée dans la fonction.  
  
#### <a name="to-add-the-calcpoints-method"></a>Pour ajouter la méthode CalcPoints  
  
1.  Ajoutez la déclaration de `CalcPoints` à la `IPolyCtl` section public de la `CPolyCtl` classe dans PolyCtl.h :  
  
     [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_4.h)]  
  
     La dernière partie de la section public de la `CPolyCtl` classe doit ressembler à ceci :  
  
     [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_5.h)]  
  
2.  Ajoutez cette implémentation de la `CalcPoints` à la fin de PolyCtl.cpp :  
  
     [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]  
  
## <a name="initializing-the-fill-color"></a>L’initialisation de la couleur de remplissage  
 Initialiser `m_clrFillColor` avec une couleur par défaut.  
  
#### <a name="to-initialize-the-fill-color"></a>Pour initialiser la couleur de remplissage  
  
1.  Utilisez le vert comme couleur par défaut en ajoutant cette ligne à la `CPolyCtl` constructeur dans PolyCtl.h :  
  
     [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_7.h)]  
  
 Le constructeur ressemble maintenant à ceci :  
  
 [!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_8.h)]  
  
## <a name="building-and-testing-the-control"></a>Génération et test du contrôle  
 Régénérez le contrôle. Assurez-vous que le fichier PolyCtl.htm est fermé si elle est toujours ouverte, puis cliquez sur **générer Polygon** sur la **générer** menu. Vous pouvez afficher le contrôle à nouveau à partir de la page PolyCtl.htm, mais cette fois-ci, utilisez ActiveX Control Test Container.  
  
#### <a name="to-use-the-activex-control-test-container"></a>Pour utiliser le contrôle ActiveX Test Container  
  
1.  Créez et démarrez ActiveX Control Test Container. Pour plus d’informations, consultez [exemple TSTCON : ActiveX Control Test Container](../visual-cpp-samples.md).  
  
2.  Dans le conteneur de Test, sur le **modifier** menu, cliquez sur **insérer un nouveau contrôle**.  
  
3.  Recherchez votre contrôle, qui sera appelée `PolyCtl Class`, puis cliquez sur **OK**. Vous verrez un triangle vert dans un cercle.  
  
 Essayez de modifier le nombre de côtés en suivant la procédure suivante. Pour modifier les propriétés sur une interface double à partir de conteneur de Test, utilisez **appeler les méthodes**.  
  
#### <a name="to-modify-a-controls-property-from-within-the-test-container"></a>Pour modifier la propriété d’un contrôle à partir du conteneur de Test  
  
1.  Dans le conteneur de Test, cliquez sur **appeler les méthodes** sur la **contrôle** menu.  
  
     Le **appeler une méthode** boîte de dialogue s’affiche.  
  
2.  Sélectionnez le **PropPut** version de la **côtés** propriété à partir de la **nom de la méthode** zone de liste déroulante.  
  
3.  Type `5` dans les **la valeur du paramètre** , cliquez sur **définir la valeur**, puis cliquez sur **Invoke**.  
  
 Notez que le contrôle ne change pas. Bien que vous avez modifié le nombre de côtés en interne en définissant le `m_nSides` variable, cela n’a pas provoqué le contrôle à redessiner. Si vous basculez vers une autre application et puis rebasculez vers le conteneur de Test, vous trouverez que le contrôle a été redessiné et possède un nombre correct de côtés.  
  
 Pour corriger ce problème, ajoutez un appel à la `FireViewChange` fonction, définie dans `IViewObjectExImpl`, après avoir défini le nombre de côtés. Si le contrôle s’exécute dans sa propre fenêtre, `FireViewChange` appellera la `InvalidateRect` directement la méthode. Si le contrôle est en cours d’exécution sans fenêtre, le `InvalidateRect` méthode sera appelée sur l’interface du conteneur site. Cela force le contrôle à redessiner.  
  
#### <a name="to-add-a-call-to-fireviewchange"></a>Pour ajouter un appel à FireViewChange  
  
1.  Mettre à jour PolyCtl.cpp en ajoutant l’appel à `FireViewChange` à la `put_Sides` (méthode). Lorsque vous avez terminé, le `put_Sides` méthode doit ressembler à ceci :  
  
     [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]  
  
 Après avoir ajouté `FireViewChange`, reconstruire et essayez du contrôle dans ActiveX Control Test Container. Cette fois, lorsque vous modifiez le nombre de côtés et cliquez sur `Invoke`, vous devez voir le contrôle à modifier immédiatement.  
  
 Dans l’étape suivante, vous allez ajouter un événement.  
  
 [À l’étape 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124; [à l’étape 5](../atl/adding-an-event-atl-tutorial-part-5.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel](../atl/active-template-library-atl-tutorial.md)   
 [Test des propriétés et des événements avec le conteneur de test](../mfc/testing-properties-and-events-with-test-container.md)

