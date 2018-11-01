---
title: Ajout d'une propriété au contrôle (Didacticiel ATL, Partie 3)
ms.custom: get-started-article
ms.date: 09/26/2018
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
ms.openlocfilehash: 9b8744e964274acb35c32a1ace02f71d0fed5c2d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466857"
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>Ajout d'une propriété au contrôle (Didacticiel ATL, Partie 3)

`IPolyCtl` est l’interface qui contient les propriétés et les méthodes du contrôle personnalisé, et vous allez ajouter une propriété à celui-ci.

### <a name="to-add-the-property-definitions-to-your-project"></a>Pour ajouter les définitions de propriétés à votre projet

1. Dans **affichage de classes**, développez le `Polygon` branche.

1. Avec le bouton droit `IPolyCtl`.

1. Dans le menu contextuel, cliquez sur **ajouter**, puis cliquez sur **ajouter une propriété**. Le **ajouter une propriété** Assistant s’affiche.

1. Type `Sides` en tant que le **nom de la propriété**.

1. Dans la liste déroulante des **Type de propriété**, sélectionnez `short`.

1. Cliquez sur **OK** pour terminer l’ajout de la propriété.

1. À partir de **l’Explorateur de solutions**, ouvrez Polygon.idl et remplacez les lignes suivantes à la fin de la `IPolyCtl : IDispatch` interface :

    ```cpp
    short get_Sides();
    void set_Sides(short value);
    ```

    par

    ```cpp
    [propget, id(1), helpstring("property Sides")] HRESULT Sides([out, retval] short *pVal);
    [propput, id(1), helpstring("property Sides")] HRESULT Sides([in] short newVal);
    ```

1. À partir de **l’Explorateur de solutions**, ouvrez PolyCtl.h et ajoutez les lignes suivantes après la définition de `m_clrFillColor`:

    [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]

Bien que vous avez désormais des fonctions squelettes pour définir et récupérer la propriété et une variable pour stocker la propriété, vous devez implémenter les fonctions en conséquence.

### <a name="to-update-the-get-and-put-methods"></a>Pour mettre à jour de la méthode get et put de méthodes

1. Définissez la valeur par défaut de `m_nSides`. Vérifiez la valeur par défaut de la forme d’un triangle en ajoutant une ligne au constructeur dans PolyCtl.h :

    [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]

1. Implémentez le `Get` et `Put` méthodes. Le `get_Sides` et `put_Sides` déclarations de fonction ont été ajoutées à PolyCtl.h. Ajoutez maintenant le code pour `get_Sides` et `put_Sides` à PolyCtl.cpp par le code suivant :

    [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]

Le `get_Sides` méthode retourne la valeur actuelle de la `Sides` propriété via le `pVal` pointeur. Dans le `put_Sides` (méthode), le code garantit l’utilisateur consiste à définir le `Sides` propriété à une valeur acceptable. La valeur minimale doit être 3, et un tableau de points sera utilisé pour chaque côté, 100 est une limite raisonnable pour une valeur maximale.

Vous disposez maintenant d’une propriété appelée `Sides`. Dans l’étape suivante, vous allez modifier le code de dessin pour l’utiliser.

[À l’étape 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [à l’étape 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)

## <a name="see-also"></a>Voir aussi

[Didacticiel](../atl/active-template-library-atl-tutorial.md)
