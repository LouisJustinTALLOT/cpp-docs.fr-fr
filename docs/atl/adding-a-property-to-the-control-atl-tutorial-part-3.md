---
title: Ajout d’une propriété au contrôle (didacticiel ATL, partie 3) | Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1e90da3fe44613b0c530e801d963eaddd9d783e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43756902"
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>Ajout d'une propriété au contrôle (Didacticiel ATL, Partie 3)

`IPolyCtl` est l’interface qui contient les propriétés et les méthodes du contrôle personnalisé, et vous allez ajouter une propriété à celui-ci.

### <a name="to-add-a-property-using-the-add-property-wizard"></a>Pour ajouter une propriété à l’aide de l’Assistant Ajout de propriété

1. Dans l’affichage de classes, développez la branche de polygone.

2. Avec le bouton droit IPolyCtl.

3. Dans le menu contextuel, cliquez sur **ajouter**, puis cliquez sur **ajouter une propriété**.

     L’Assistant Ajout de propriété s’affiche.

4. Dans la liste déroulante des types de propriété, sélectionnez `SHORT`.

5. Type *côtés* comme le **nom de la propriété.**

6. Cliquez sur **Terminer** pour terminer l’ajout de la propriété.

Lorsque vous ajoutez la propriété à l’interface, MIDL (le programme qui compile les fichiers .idl) définit un `Get` méthode pour récupérer sa valeur et un `Put` méthode pour définir une nouvelle valeur. Les méthodes sont nommées en ajoutant le préfixe `put_` et `get_` au nom de propriété.

L’Assistant Ajout de propriété ajoute les lignes nécessaires au fichier .idl. Il ajoute également le `Get` et `Put` à la définition de classe dans PolyCtl.h des prototypes de fonction et ajoute une implémentation vide à PolyCtl.cpp. Vous pouvez le vérifier en ouvrant PolyCtl.cpp et en recherchant les fonctions `get_Sides` et `put_Sides`.

Bien que vous avez désormais des fonctions squelettes pour définir et récupérer la propriété, il a besoin d’un emplacement à stocker. Vous allez créer une variable pour stocker la propriété et mettre à jour les fonctions en conséquence.

#### <a name="to-create-a-variable-to-store-the-property-and-update-the-put-and-get-methods"></a>Pour créer une variable pour stocker la propriété et mettre à jour le put et des méthodes get

1. À partir de l’Explorateur de solutions, ouvrez PolyCtl.h et ajoutez la ligne suivante après la définition de `m_clrFillColor`:

     [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]

2. Définissez la valeur par défaut de `m_nSides`. Vérifiez la valeur par défaut de la forme d’un triangle en ajoutant une ligne au constructeur dans PolyCtl.h :

     [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]

3. Implémentez le `Get` et `Put` méthodes. Le `get_Sides` et `put_Sides` déclarations de fonction ont été ajoutées à PolyCtl.h. Remplacez le code dans PolyCtl.cpp pour `get_Sides` et `put_Sides` avec le code suivant :

     [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]

Le `get_Sides` méthode retourne la valeur actuelle de la `Sides` propriété via le `pVal` pointeur. Dans le `put_Sides` (méthode), le code garantit l’utilisateur consiste à définir le `Sides` propriété à une valeur acceptable. La valeur minimale doit être 3, et un tableau de points sera utilisé pour chaque côté, 100 est une limite raisonnable pour une valeur maximale.

Vous disposez maintenant d’une propriété appelée `Sides`. Dans l’étape suivante, vous allez modifier le code de dessin pour l’utiliser.

[À l’étape 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [à l’étape 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)

## <a name="see-also"></a>Voir aussi

[Didacticiel](../atl/active-template-library-atl-tutorial.md)

