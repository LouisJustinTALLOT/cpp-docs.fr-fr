---
description: 'En savoir plus sur : ajout d’un événement (Didacticiel ATL, partie 5)'
title: Ajout d'un événement (Didacticiel ATL, Partie 5)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
ms.openlocfilehash: 70c3b570eefa274d2cab9e31420729949d4c7974
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166250"
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>Ajout d'un événement (Didacticiel ATL, Partie 5)

Dans cette étape, vous allez ajouter un `ClickIn` et un `ClickOut` événement à votre contrôle ATL. Vous déclenchez l' `ClickIn` événement si l’utilisateur clique dans le polygone et se déclenche `ClickOut` si l’utilisateur clique à l’extérieur. Les tâches d’ajout d’un événement sont les suivantes :

- Ajout des `ClickIn` `ClickOut` méthodes et

- Génération de la bibliothèque de types

- Implémentation des interfaces de point de connexion

## <a name="adding-the-clickin-and-clickout-methods"></a>Ajout des méthodes Click et ClickOut

Lorsque vous avez créé le contrôle ATL à l’étape 2, vous avez activé la case à cocher **points de connexion** . Cela a créé l' `_IPolyCtlEvents` interface dans le fichier Polygon. idl. Notez que le nom de l’interface commence par un trait de soulignement. Il s’agit d’une convention pour indiquer que l’interface est une interface interne. Ainsi, les programmes qui vous permettent de parcourir les objets COM peuvent choisir de ne pas afficher l’interface de l’utilisateur. Notez également que la sélection de **points de connexion** a ajouté la ligne suivante dans le fichier Polygon. idl pour indiquer que `_IPolyCtlEvents` est l’interface source par défaut :

`[default, source] dispinterface _IPolyCtlEvents;`

L’attribut source indique que le contrôle est la source des notifications. il appellera donc cette interface sur le conteneur.

Ajoutez maintenant les `ClickIn` `ClickOut` méthodes et à l' `_IPolyCtlEvents` interface.

### <a name="to-add-the-clickin-and-clickout-methods"></a>Pour ajouter les méthodes Click et ClickOut

1. Dans **Explorateur de solutions**, ouvrez Polygon. idl et ajoutez le code suivant sous `methods:` dans la `dispInterface_IPolyCtlEvents` déclaration de la bibliothèque PolygonLib :

    ```cpp
   [id(1), helpstring("method ClickIn")] void ClickIn([in] LONG x,[in] LONG y);
   [id(2), helpstring("method ClickOut")] void ClickOut([in] LONG x,[in] LONG y);
    ```

Les `ClickIn` `ClickOut` méthodes et prennent les coordonnées x et y du point cliqué en tant que paramètres.

## <a name="generating-the-type-library"></a>Génération de la bibliothèque de types

Générez la bibliothèque de types à ce stade, car le projet l’utilisera pour obtenir les informations dont il a besoin pour construire une interface de point de connexion et une interface de conteneur de point de connexion pour votre contrôle.

### <a name="to-generate-the-type-library"></a>Pour générer la bibliothèque de types

1. Régénérez votre projet.

     -ou-

1. Cliquez avec le bouton droit sur le fichier Polygon. idl dans **Explorateur de solutions** , puis cliquez sur **compiler** dans le menu contextuel.

Cette opération crée le fichier Polygon. tlb, qui est votre bibliothèque de types. Le fichier Polygon. tlb n’est pas visible à partir de **Explorateur de solutions**, car il s’agit d’un fichier binaire qui ne peut pas être affiché ou modifié directement.

## <a name="implementing-the-connection-point-interfaces"></a>Implémentation des interfaces de point de connexion

Implémentez une interface de point de connexion et une interface de conteneur de point de connexion pour votre contrôle. Dans COM, les événements sont implémentés par le biais du mécanisme des points de connexion. Pour recevoir des événements d’un objet COM, un conteneur établit une connexion de notifications au point de connexion que l’objet COM implémente. Comme un objet COM peut avoir plusieurs points de connexion, l’objet COM implémente également une interface de conteneur de point de connexion. Grâce à cette interface, le conteneur peut déterminer les points de connexion pris en charge.

L’interface qui implémente un point de connexion est appelée `IConnectionPoint` et l’interface qui implémente un conteneur de point de connexion est appelée `IConnectionPointContainer` .

Pour faciliter l’implémentation `IConnectionPoint` , vous allez utiliser l’Assistant Implémentation d’un point de connexion. Cet Assistant génère l' `IConnectionPoint` interface en lisant votre bibliothèque de types et en implémentant une fonction pour chaque événement qui peut être déclenché.

### <a name="to-implement-the-connection-points"></a>Pour implémenter les points de connexion

1. Dans **Explorateur de solutions**, ouvrez _IPolyCtlEvents_CP. h et ajoutez le code suivant sous l' `public:` instruction de la `CProxy_IPolyCtlEvents` classe :

    ```cpp
    VOID Fire_ClickIn(LONG x, LONG y)
    {
        T* pT = static_cast<T*>(this);
        int nConnectionIndex;
        CComVariant* pvars = new CComVariant[2];
        int nConnections = m_vec.GetSize();

        for (nConnectionIndex = 0; nConnectionIndex < nConnections; nConnectionIndex++)
        {
            pT->Lock();
            CComPtr<IUnknown> sp = m_vec.GetAt(nConnectionIndex);
            pT->Unlock();
            IDispatch* pDispatch = reinterpret_cast<IDispatch*>(sp.p);
            if (pDispatch != NULL)
            {
                pvars[1].vt = VT_I4;
                pvars[1].lVal = x;
                pvars[0].vt = VT_I4;
                pvars[0].lVal = y;
                DISPPARAMS disp = { pvars, NULL, 2, 0 };
                pDispatch->Invoke(0x1, IID_NULL, LOCALE_USER_DEFAULT, DISPATCH_METHOD, &disp, NULL, NULL, NULL);
            }
        }
        delete[] pvars;

    }
    VOID Fire_ClickOut(LONG x, LONG y)
    {
        T* pT = static_cast<T*>(this);
        int nConnectionIndex;
        CComVariant* pvars = new CComVariant[2];
        int nConnections = m_vec.GetSize();

        for (nConnectionIndex = 0; nConnectionIndex < nConnections; nConnectionIndex++)
        {
            pT->Lock();
            CComPtr<IUnknown> sp = m_vec.GetAt(nConnectionIndex);
            pT->Unlock();
            IDispatch* pDispatch = reinterpret_cast<IDispatch*>(sp.p);
            if (pDispatch != NULL)
            {
                pvars[1].vt = VT_I4;
                pvars[1].lVal = x;
                pvars[0].vt = VT_I4;
                pvars[0].lVal = y;
                DISPPARAMS disp = { pvars, NULL, 2, 0 };
                pDispatch->Invoke(0x2, IID_NULL, LOCALE_USER_DEFAULT, DISPATCH_METHOD, &disp, NULL, NULL, NULL);
            }
        }
        delete[] pvars;

    }
    ```

Vous verrez que ce fichier a une classe appelée `CProxy_IPolyCtlEvents` qui dérive de `IConnectionPointImpl` . _IPolyCtlEvents_CP. h définit maintenant les deux méthodes `Fire_ClickIn` et `Fire_ClickOut` , qui prennent les deux paramètres de coordonnée. Vous appelez ces méthodes lorsque vous souhaitez déclencher un événement à partir de votre contrôle.

En créant l’option contrôle avec des **points de connexion** sélectionnée, le fichier _IPolyCtlEvents_CP. h a été généré pour vous. Elle a également ajouté `CProxy_PolyEvents` et `IConnectionPointContainerImpl` à la liste d’héritage multiple de votre contrôle et est exposée `IConnectionPointContainer` pour vous en ajoutant des entrées appropriées au mappage com.

Vous avez terminé l’implémentation du code pour prendre en charge les événements. À présent, ajoutez du code pour activer les événements au moment opportun. N’oubliez pas que vous allez déclencher un `ClickIn` `ClickOut` événement ou lorsque l’utilisateur clique sur le bouton gauche de la souris dans le contrôle. Pour savoir quand l’utilisateur clique sur le bouton, ajoutez un gestionnaire pour le `WM_LBUTTONDOWN` message.

### <a name="to-add-a-handler-for-the-wm_lbuttondown-message"></a>Pour ajouter un gestionnaire pour le message WM_LBUTTONDOWN

1. Dans **affichage de classes**, cliquez avec le bouton droit sur la `CPolyCtl` classe, puis cliquez sur **Propriétés** dans le menu contextuel.

1. Dans la fenêtre **Propriétés** , cliquez sur l’icône **messages** , puis cliquez `WM_LBUTTONDOWN` dans la liste à gauche.

1. Dans la liste déroulante qui s’affiche, cliquez sur **\<Add> OnLButtonDown**. La `OnLButtonDown` déclaration du gestionnaire sera ajoutée à PolyCtl. h, et l’implémentation du gestionnaire sera ajoutée à PolyCtl. cpp.

Ensuite, modifiez le gestionnaire.

### <a name="to-modify-the-onlbuttondown-method"></a>Pour modifier la méthode OnLButtonDown

1. Modifiez le code qui comprend la `OnLButtonDown` méthode dans PolyCtl. cpp (en supprimant tout code placé par l’Assistant) afin qu’il se présente comme suit :

    [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]

Ce code utilise les points calculés dans la `OnDraw` fonction pour créer une région qui détecte les clics de souris de l’utilisateur avec l’appel à `PtInRegion` .

Le paramètre *uMsg* est l’ID du message Windows géré. Cela vous permet d’avoir une fonction qui gère une plage de messages. Les paramètres *wParam* et *lParam* sont les valeurs standard du message en cours de traitement. Le paramètre *bHandled* vous permet de spécifier si la fonction a géré ou non le message. Par défaut, la valeur est définie sur TRUE pour indiquer que la fonction a géré le message, mais vous pouvez lui affecter la valeur FALSe. ATL continue alors à rechercher une autre fonction de gestionnaire de messages à laquelle envoyer le message.

## <a name="building-and-testing-the-control"></a>Création et test du contrôle

Essayez maintenant vos événements. Générez le contrôle et redémarrez le conteneur test de contrôle ActiveX. Cette fois, affichez la fenêtre du journal des événements. Pour acheminer les événements vers la fenêtre sortie, cliquez sur **journalisation** dans le menu **options** et sélectionnez **Journal dans la fenêtre Sortie**. Insérez le contrôle et essayez de cliquer dans la fenêtre. Notez que `ClickIn` est déclenché si vous cliquez dans le polygone plein et qu' `ClickOut` il est déclenché lorsque vous cliquez en dehors de celui-ci.

Vous allez ensuite ajouter une page de propriétés.

[Retour à l’étape 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [à l’étape 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="see-also"></a>Voir aussi

[Didacticiel](../atl/active-template-library-atl-tutorial.md)
