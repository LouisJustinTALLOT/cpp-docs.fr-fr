---
title: Ajout d'un événement (Didacticiel ATL, Partie 5)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
ms.openlocfilehash: 57fc2adaadcca52cfc25736b5f9010fcb65a2ff0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252561"
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>Ajout d'un événement (Didacticiel ATL, Partie 5)

Dans cette étape, vous allez ajouter un `ClickIn` et un `ClickOut` événement à votre contrôle ATL. Vous activeront le `ClickIn` événement si l’utilisateur clique dans le polygone et incendie `ClickOut` si l’utilisateur clique en dehors. Les tâches pour ajouter un événement sont les suivantes :

- Ajout de la `ClickIn` et `ClickOut` méthodes

- Génération de la bibliothèque de types

- Implémentation des Interfaces de Point de connexion

## <a name="adding-the-clickin-and-clickout-methods"></a>Ajouter les méthodes ClickIn et ClickOut

Lorsque vous avez créé le contrôle ATL à l’étape 2, vous avez sélectionné le **points de connexion** case à cocher. Cela a créé le `_IPolyCtlEvents` interface dans le fichier Polygon.idl. Notez que le nom d’interface commence par un trait de soulignement. Il s’agit d’une convention pour indiquer que l’interface est une interface interne. Par conséquent, les programmes qui vous permettent de parcourir les objets COM peuvent choisir de ne l’interface à l’utilisateur. Notez également que la sélection **points de connexion** ajouté la ligne suivante dans le fichier Polygon.idl pour indiquer que `_IPolyCtlEvents` est l’interface source par défaut :

`[default, source] dispinterface _IPolyCtlEvents;`

L’attribut source indique que le contrôle est la source des notifications, donc il appellera cette interface sur le conteneur.

Ajoutez maintenant le `ClickIn` et `ClickOut` méthodes pour le `_IPolyCtlEvents` interface.

### <a name="to-add-the-clickin-and-clickout-methods"></a>Pour ajouter les méthodes ClickIn et ClickOut

1. Dans **l’Explorateur de solutions**, ouvrez Polygon.idl et ajoutez le code suivant sous `methods:` dans le `dispInterface_IPolyCtlEvents` déclaration de la bibliothèque PolygonLib :

    ```cpp
   [id(1), helpstring("method ClickIn")] void ClickIn([in] LONG x,[in] LONG y);
   [id(2), helpstring("method ClickOut")] void ClickOut([in] LONG x,[in] LONG y);
    ```

Le `ClickIn` et `ClickOut` take méthodes x et les coordonnées y de l’utilisateur a cliqué dessu point en tant que paramètres.

## <a name="generating-the-type-library"></a>Génération de la bibliothèque de types

Générer la bibliothèque de types à ce stade, car le projet va l’utiliser pour obtenir les informations nécessaires construire une interface de point de connexion et une interface de conteneur de point de connexion pour votre contrôle.

### <a name="to-generate-the-type-library"></a>Pour générer la bibliothèque de types

1. Régénérez votre projet.

     - ou -

1. Cliquez sur le fichier Polygon.idl dans **l’Explorateur de solutions** et cliquez sur **compiler** dans le menu contextuel.

Cela créera le fichier Polygon.tlb, qui est votre bibliothèque de types. Le fichier Polygon.tlb n’est pas visible à partir de **l’Explorateur de solutions**, car il est un fichier binaire et ne peut pas être affiché ou modifié directement.

## <a name="implementing-the-connection-point-interfaces"></a>Implémentation des Interfaces de Point de connexion

Implémenter une interface de point de connexion et une interface de conteneur de point de connexion pour votre contrôle. Dans COM, les événements sont implémentés via le mécanisme de points de connexion. Pour recevoir des événements à partir d’un objet COM, un conteneur établit une connexion au point de connexion qui implémente l’objet COM de notifications. Comme un objet COM peut avoir plusieurs points de connexion, l’objet COM implémente également une interface de conteneur de point de connexion. Via cette interface, le conteneur peut déterminer les points de connexion sont prises en charge.

L’interface qui implémente un point de connexion est appelée `IConnectionPoint`, et l’interface qui implémente un conteneur de point de connexion est appelée `IConnectionPointContainer`.

Pour aider à implémenter `IConnectionPoint`, vous allez utiliser l’Assistant Implémentation d’un Point de connexion. Cet Assistant génère le `IConnectionPoint` interface en lisant votre bibliothèque de types et en implémentant une fonction pour chaque événement qui peut être déclenché.

### <a name="to-implement-the-connection-points"></a>Pour implémenter les points de connexion

1. Dans **l’Explorateur de solutions**, ouvrez _IPolyCtlEvents_CP.h et ajoutez le code suivant sous le `public:` instruction dans le `CProxy_IPolyCtlEvents` classe :

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

Vous verrez que ce fichier contient une classe appelée `CProxy_IPolyCtlEvents` qui dérive de `IConnectionPointImpl`. _IPolyCtlEvents_CP.h définit à présent les deux méthodes `Fire_ClickIn` et `Fire_ClickOut`, qui accepte les deux paramètres des coordonnées. Vous appelez ces méthodes lorsque vous souhaitez déclencher un événement à partir de votre contrôle.

En créant le contrôle avec **points de connexion** option est sélectionnée, le fichier _IPolyCtlEvents_CP.h a été générée pour vous. Informatique également ajouté `CProxy_PolyEvents` et `IConnectionPointContainerImpl` à la liste d’héritage multiple de votre contrôle et exposées `IConnectionPointContainer` pour vous en ajoutant les entrées appropriées au mappage COM.

Vous avez terminé l’implémentation du code pour prendre en charge des événements. Maintenant, ajoutez du code pour déclencher les événements au moment approprié. N’oubliez pas, vous vous apprêtez à déclencher un `ClickIn` ou `ClickOut` événement lorsque l’utilisateur clique sur le bouton gauche de la souris dans le contrôle. Pour déterminer à quel moment l’utilisateur clique sur le bouton, ajoutez un gestionnaire pour le `WM_LBUTTONDOWN` message.

### <a name="to-add-a-handler-for-the-wmlbuttondown-message"></a>Pour ajouter un gestionnaire pour le message WM_LBUTTONDOWN

1. Dans **affichage de classes**, cliquez sur le `CPolyCtl` classe et cliquez sur **propriétés** dans le menu contextuel.

1. Dans le **propriétés** fenêtre, cliquez sur le **Messages** icône, puis cliquez sur `WM_LBUTTONDOWN` dans la liste sur la gauche.

1. Dans la liste déroulante qui s’affiche, cliquez sur  **\<Ajouter > OnLButtonDown**. Le `OnLButtonDown` déclaration du gestionnaire sera ajoutée à PolyCtl.h, et l’implémentation du gestionnaire sera ajoutée à PolyCtl.cpp.

Ensuite, modifiez le gestionnaire.

### <a name="to-modify-the-onlbuttondown-method"></a>Pour modifier la méthode OnLButtonDown

1. Modifier le code qui comprend le `OnLButtonDown` méthode dans PolyCtl.cpp (en supprimant tout code placé par l’Assistant) afin qu’il ressemble à ceci :

    [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]

Cela rend de code utilise les points calculés dans le `OnDraw` (fonction) pour créer une région qui détecte les clics de la souris de l’utilisateur avec l’appel à `PtInRegion`.

Le *uMsg* paramètre est l’ID du message Windows en cours de traitement. Cela vous permet d’avoir une fonction qui gère une série de messages. Le *wParam* et *lParam* paramètres sont les valeurs standard pour le message en cours de traitement. Le paramètre *bHandled* vous permet de spécifier si la fonction a traité le message ou non. Par défaut, la valeur est définie sur TRUE pour indiquer que la fonction a traité le message, mais vous pouvez le définir sur FALSE. Cela entraîne ATL continuer la recherche d’une autre fonction de gestionnaire de messages à envoyer le message.

## <a name="building-and-testing-the-control"></a>Création et test du contrôle

Essayer maintenant vos événements. Générer le contrôle et recommencer l’ActiveX Control Test Container. Cette fois-ci, affichez la fenêtre de journal des événements. Pour acheminer des événements dans la fenêtre Sortie, cliquez sur **journalisation** à partir de la **Options** menu et sélectionnez **journal dans la fenêtre sortie**. Insérez le contrôle et essayez de cliquer dans la fenêtre. Notez que `ClickIn` est déclenché si vous cliquez à l’intérieur du polygone plein, et `ClickOut` est déclenché lorsque vous cliquez en dehors de celle-ci.

Ensuite, vous allez ajouter une page de propriétés.

[À l’étape 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [à l’étape 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="see-also"></a>Voir aussi

[Tutoriel](../atl/active-template-library-atl-tutorial.md)
