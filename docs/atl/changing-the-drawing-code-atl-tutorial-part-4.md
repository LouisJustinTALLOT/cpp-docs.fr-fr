---
title: Changement du code de dessin (Didacticiel ATL, partie 4)
ms.custom: get-started-article
ms.date: 09/26/2018
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
ms.openlocfilehash: 4244dae532f467f28a5ca53e15ee601344999233
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79509373"
---
# <a name="changing-the-drawing-code-atl-tutorial-part-4"></a>Changement du code de dessin (Didacticiel ATL, partie 4)

Par défaut, le code de dessin du contrôle affiche un carré et le texte **PolyCtl**. Dans cette étape, vous allez modifier le code pour afficher un résultat plus intéressant. Les tâches suivantes sont impliquées :

- Modification du fichier d’en-tête

- Modification de la fonction `OnDraw`

- Ajout d’une méthode pour calculer les points de polygone

- Initialisation de la couleur de remplissage

## <a name="modifying-the-header-file"></a>Modification du fichier d’en-tête

Commencez par ajouter la prise en charge des fonctions mathématiques `sin` et `cos`, qui seront utilisées pour calculer les points de polygone et en créant un tableau pour stocker les positions.

### <a name="to-modify-the-header-file"></a>Pour modifier le fichier d’en-tête

1. Ajoutez la ligne `#include <math.h>` en haut de PolyCtl. h. Le haut du fichier doit ressembler à ceci :

    [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]

1. Implémentez l’interface `IProvideClassInfo` pour fournir des informations de méthode pour le contrôle, en ajoutant le code suivant à PolyCtl. h. Dans la classe `CPolyCtl`, remplacez Line :

    ```cpp
    public CComControl<CPolyCtl>
    ```

    par

    ```cpp
    public CComControl<CPolyCtl>,
    public IProvideClassInfo2Impl<&CLSID_PolyCtl, &DIID__IPolyCtlEvents, &LIBID_PolygonLib>
    ```

    et dans `BEGIN_COM_MAP(CPolyCtl)`, ajoutez les lignes :

    ```cpp
    COM_INTERFACE_ENTRY(IProvideClassInfo)
    COM_INTERFACE_ENTRY(IProvideClassInfo2)
    ```

1. Une fois les points de polygone calculés, ils sont stockés dans un tableau de type `POINT`, par conséquent, ajoutez le tableau après l’instruction de définition `short m_nSides;` dans PolyCtl. h :

    [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_2.h)]

## <a name="modifying-the-ondraw-method"></a>Modification de la méthode OnDraw

À présent, vous devez modifier la méthode `OnDraw` dans PolyCtl. h. Le code que vous ajouterez crée un stylet et un pinceau avec lesquels dessiner votre polygone, puis il appelle la `Ellipse` et `Polygon` fonctions de l’API Win32 pour effectuer le dessin réel.

### <a name="to-modify-the-ondraw-function"></a>Pour modifier la fonction OnDraw

1. Remplacez la méthode `OnDraw` existante dans PolyCtl. h par le code suivant :

    [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]

## <a name="adding-a-method-to-calculate-the-polygon-points"></a>Ajout d’une méthode pour calculer les points de polygone

Ajoutez une méthode, appelée `CalcPoints`, qui calcule les coordonnées des points qui composent le périmètre du polygone. Ces calculs seront basés sur la variable RECT transmise dans la fonction.

### <a name="to-add-the-calcpoints-method"></a>Pour ajouter la méthode CalcPoints

1. Ajoutez la déclaration de `CalcPoints` à la section publique `IPolyCtl` de la classe `CPolyCtl` dans PolyCtl. h :

    [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_4.h)]

    La dernière partie de la section publique de la classe `CPolyCtl` se présente comme suit :

    [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_5.h)]

1. Ajoutez cette implémentation de la fonction `CalcPoints` à la fin de PolyCtl. cpp :

    [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]

## <a name="initializing-the-fill-color"></a>Initialisation de la couleur de remplissage

Initialisez `m_clrFillColor` avec une couleur par défaut.

### <a name="to-initialize-the-fill-color"></a>Pour initialiser la couleur de remplissage

1. Utilisez le vert comme couleur par défaut en ajoutant cette ligne au constructeur `CPolyCtl` dans PolyCtl. h :

    [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_7.h)]

Le constructeur ressemble maintenant à ceci :

[!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_8.h)]

## <a name="building-and-testing-the-control"></a>Création et test du contrôle

Régénérez le contrôle. Assurez-vous que le fichier PolyCtl. htm est fermé s’il est toujours ouvert, puis cliquez sur **générer le polygone** dans le menu **générer** . Vous pouvez afficher à nouveau le contrôle à partir de la page PolyCtl. htm, mais cette fois, utilisez le conteneur de test ActiveX Control.

### <a name="to-use-the-activex-control-test-container"></a>Pour utiliser ActiveX Control Test Container

1. Générez et démarrez le conteneur test de contrôle ActiveX. L' [exemple TSTCON : ActiveX Control Test Container](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole/TstCon) se trouve sur GitHub.

    > [!NOTE]
    > Pour les erreurs impliquant `ATL::CW2AEX`, dans script. cpp, remplacez Line `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT );` par `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT.m_psz );`et Line `TRACE( "Source Text: %s\n", COLE2CT( bstrSourceLineText ) );` par `TRACE( "Source Text: %s\n", bstrSourceLineText );`.<br/>
    > Pour les erreurs impliquant `HMONITOR`, ouvrez StdAfx. h dans le projet `TCProps` et remplacez :
    >
    > ```
    > #ifndef WINVER
    > #define WINVER 0x0400
    > #endif
    > ```
    >
    > par
    >
    > ```
    > #ifndef WINVER
    > #define WINVER 0x0500
    > #define _WIN32_WINNT 0x0500
    > #endif
    > ```

1. Dans **Test Container**, dans le menu **Edition** , cliquez sur **Insérer un nouveau contrôle**.

1. Localisez votre contrôle, qui sera appelé `PolyCtl class`, puis cliquez sur **OK**. Vous verrez un triangle vert dans un cercle.

Essayez de modifier le nombre de côtés en suivant la procédure suivante. Pour modifier les propriétés d’une interface double à partir du **conteneur de test**, utilisez des **méthodes Invoke**.

### <a name="to-modify-a-controls-property-from-within-the-test-container"></a>Pour modifier la propriété d’un contrôle à partir du conteneur de test

1. Dans **Test Container**, cliquez sur **appeler les méthodes** dans le menu **contrôle** .

    La boîte de dialogue **appeler la méthode** s’affiche.

1. Sélectionnez la version **propput** de la propriété **Sides** dans la zone de liste déroulante nom de la **méthode** .

1. Tapez `5` dans la zone **valeur du paramètre** , cliquez sur définir la **valeur**, puis sur **appeler**.

Notez que le contrôle ne change pas. Bien que vous ayez modifié le nombre de côtés en interne en définissant la variable `m_nSides`, cela n’a pas provoqué le contrôle à repeindre. Si vous basculez vers une autre application, puis revenez au **conteneur de test**, vous constaterez que le contrôle a été repeint et qu’il a le nombre correct de côtés.

Pour corriger ce problème, ajoutez un appel à la fonction `FireViewChange`, définie dans `IViewObjectExImpl`, après avoir défini le nombre de côtés. Si le contrôle s’exécute dans sa propre fenêtre, `FireViewChange` appellera directement la méthode `InvalidateRect`. Si le contrôle s’exécute sans fenêtre, la méthode `InvalidateRect` sera appelée sur l’interface de site du conteneur. Cela force le contrôle à se repeindre lui-même.

### <a name="to-add-a-call-to-fireviewchange"></a>Pour ajouter un appel à FireViewChange

1. Mettez à jour PolyCtl. cpp en ajoutant l’appel à `FireViewChange` à la méthode `put_Sides`. Lorsque vous avez terminé, la méthode `put_Sides` doit se présenter comme suit :

    [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]

Après avoir ajouté `FireViewChange`, régénérez et réessayez le contrôle dans le conteneur de test de contrôle ActiveX. Cette fois-ci, lorsque vous modifiez le nombre de côtés et cliquez sur `Invoke`, le contrôle change immédiatement.

À l’étape suivante, vous allez ajouter un événement.

[Retour à l’étape 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124; à l' [étape 5](../atl/adding-an-event-atl-tutorial-part-5.md)

## <a name="see-also"></a>Voir aussi

[Didacticiel](../atl/active-template-library-atl-tutorial.md)<br/>
[Test des propriétés et des événements avec le conteneur de test](../mfc/testing-properties-and-events-with-test-container.md)
