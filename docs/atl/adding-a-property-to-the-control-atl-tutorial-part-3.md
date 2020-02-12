---
title: Ajout d'une propriété au contrôle (Didacticiel ATL, Partie 3)
ms.custom: get-started-article
ms.date: 09/26/2018
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
ms.openlocfilehash: 288dc9f5af57c02639d15a9a971419a633cfc08d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127585"
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>Ajout d'une propriété au contrôle (Didacticiel ATL, Partie 3)

`IPolyCtl` est l’interface qui contient les méthodes et les propriétés personnalisées du contrôle, et vous y ajoutez une propriété.

### <a name="to-add-the-property-definitions-to-your-project"></a>Pour ajouter les définitions de propriétés à votre projet

1. Dans **affichage de classes**, développez la branche `Polygon`.

1. Cliquez avec le bouton droit sur `IPolyCtl`.

1. Dans le menu contextuel, cliquez sur **Ajouter**, puis sur **Ajouter une propriété**. L’Assistant **Ajouter une propriété** s’affiche.

1. Tapez `Sides` comme nom de la **propriété**.

1. Dans la liste déroulante de **type de propriété**, sélectionnez `short`.

1. Cliquez sur **OK** pour terminer l’ajout de la propriété.

1. À partir de **Explorateur de solutions**, ouvrez Polygon. idl et remplacez les lignes suivantes à la fin de l’interface `IPolyCtl : IDispatch` :

    ```cpp
    short get_Sides();
    void set_Sides(short value);
    ```

    par

    ```cpp
    [propget, id(1), helpstring("property Sides")] HRESULT Sides([out, retval] short *pVal);
    [propput, id(1), helpstring("property Sides")] HRESULT Sides([in] short newVal);
    ```

1. À partir de **Explorateur de solutions**, ouvrez PolyCtl. h et ajoutez les lignes suivantes après la définition de `m_clrFillColor`:

    [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]

Bien que vous ayez maintenant des fonctions squelettes pour définir et récupérer la propriété et une variable pour stocker la propriété, vous devez implémenter les fonctions en conséquence.

### <a name="to-update-the-get-and-put-methods"></a>Pour mettre à jour les méthodes d’extraction et de placement

1. Définissez la valeur par défaut de `m_nSides`. Définissez la forme par défaut sur un triangle en ajoutant une ligne au constructeur dans PolyCtl. h :

    [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]

1. Implémentez les méthodes `Get` et `Put`. Les déclarations de fonction `get_Sides` et `put_Sides` ont été ajoutées à PolyCtl. h. Ajoutez maintenant le code pour `get_Sides` et `put_Sides` à PolyCtl. cpp avec les éléments suivants :

    [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]

La méthode `get_Sides` retourne la valeur actuelle de la propriété `Sides` par le biais du pointeur `pVal`. Dans la méthode `put_Sides`, le code garantit que l’utilisateur définit la propriété `Sides` sur une valeur acceptable. La valeur minimale doit être 3, et comme un tableau de points sera utilisé pour chaque côté, 100 est une limite raisonnable pour une valeur maximale.

Vous disposez maintenant d’une propriété appelée `Sides`. À l’étape suivante, vous allez modifier le code de dessin pour l’utiliser.

[Retour à l’étape 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; à l' [étape 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)

## <a name="see-also"></a>Voir aussi

[Didacticiel](../atl/active-template-library-atl-tutorial.md)
