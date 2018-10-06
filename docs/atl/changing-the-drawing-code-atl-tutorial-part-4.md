---
title: Modification du Code de dessin (didacticiel ATL, partie 4) | Microsoft Docs
ms.custom: get-started-article
ms.date: 09/26/2018
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
ms.openlocfilehash: 4ad8be0655d43fac063a3551f43e667a04caa27b
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821060"
---
# <a name="changing-the-drawing-code-atl-tutorial-part-4"></a>Changement du code de dessin (Didacticiel ATL, partie 4)

Par défaut, code de dessin du contrôle affiche un carré et le texte **PolyCtl**. Dans cette étape, vous allez modifier le code pour afficher quelque chose de plus intéressant. Les tâches suivantes sont impliqués :

- Modification du fichier d’en-tête

- Modification de la `OnDraw` (fonction)

- Ajout d’une méthode pour calculer les Points du polygone

- L’initialisation de la couleur de remplissage

## <a name="modifying-the-header-file"></a>Modification du fichier d’en-tête

Commencez par ajouter la prise en charge pour les fonctions mathématiques `sin` et `cos`, qui sera utilisée calculer les points du polygone et en créant un tableau pour stocker les positions.

### <a name="to-modify-the-header-file"></a>Pour modifier le fichier d’en-tête

1. Ajoutez la ligne `#include <math.h>` au début du PolyCtl.h. En haut du fichier doit ressembler à ceci :

    [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]

1. Implémentez le `IProvideClassInfo` interface pour fournir des informations de méthode pour le contrôle, en ajoutant le code suivant à PolyCtl.h. Dans le `CPolyCtl` de classe, remplacez la ligne :

    ```cpp
    public CComControl<CPolyCtl>
    ```

    par

    ```cpp
    public CComControl<CPolyCtl>,
    public IProvideClassInfo2Impl<&CLSID_PolyCtl, &DIID__IPolyCtlEvents, &LIBID_PolygonLib>
    ```

    puis, dans `BEGIN_COM_MAP(CPolyCtl)`, ajoutez les lignes :

    ```cpp
    COM_INTERFACE_ENTRY(IProvideClassInfo)
    COM_INTERFACE_ENTRY(IProvideClassInfo2)
    ```

1. Une fois que les points de polygone sont calculées, ils sont stockés dans un tableau de type `POINT`, donc ajouter le tableau après l’instruction de définition `short m_nSides;` dans PolyCtl.h :

    [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_2.h)]

## <a name="modifying-the-ondraw-method"></a>Modification de la méthode OnDraw

Maintenant que vous devez modifier le `OnDraw` méthode dans PolyCtl.h. Le code que vous allez ajouter crée un nouveau stylet et le pinceau avec lequel dessiner votre polygone et appelle ensuite la `Ellipse` et `Polygon` fonctions API Win32 pour effectuer le dessin proprement dit.

### <a name="to-modify-the-ondraw-function"></a>Pour modifier la fonction OnDraw

1. Remplacer la `OnDraw` méthode dans PolyCtl.h avec le code suivant :

    [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]

## <a name="adding-a-method-to-calculate-the-polygon-points"></a>Ajout d’une méthode pour calculer les Points du polygone

Ajoutez une méthode appelée `CalcPoints`, qui calcule les coordonnées des points qui composent le périmètre du polygone. Ces calculs doit reposer sur la variable RECT qui est transmise à la fonction.

### <a name="to-add-the-calcpoints-method"></a>Pour ajouter la méthode CalcPoints

1. Ajoutez la déclaration de `CalcPoints` à la `IPolyCtl` section publique de la `CPolyCtl` classe dans PolyCtl.h :

    [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_4.h)]

    La dernière partie de la section publique de la `CPolyCtl` classe se présente comme suit :

    [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_5.h)]

1. Ajoutez cette implémentation de la `CalcPoints` (fonction) à la fin de PolyCtl.cpp :

    [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]

## <a name="initializing-the-fill-color"></a>L’initialisation de la couleur de remplissage

Initialiser `m_clrFillColor` avec une couleur par défaut.

### <a name="to-initialize-the-fill-color"></a>Pour initialiser la couleur de remplissage

1. Utilisez le vert comme couleur par défaut en ajoutant cette ligne à la `CPolyCtl` constructeur dans PolyCtl.h :

    [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_7.h)]

Le constructeur ressemble maintenant à ceci :

[!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_8.h)]

## <a name="building-and-testing-the-control"></a>Création et test du contrôle

Régénérez le contrôle. Assurez-vous que le fichier PolyCtl.htm est fermé s’il est toujours ouvert, puis cliquez sur **générer le polygone** sur le **Build** menu. Vous pouvez afficher le contrôle une fois encore à partir de la page PolyCtl.htm, mais cette fois utiliser ActiveX Control Test Container.

### <a name="to-use-the-activex-control-test-container"></a>Pour utiliser le contrôle ActiveX Test Container

1. Créez et démarrez ActiveX Control Test Container. Le [exemple TSTCON : ActiveX Control Test Container](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole/TstCon) trouverez sur GitHub.

    > [!NOTE]
    > Pour les erreurs impliquant `ATL::CW2AEX`, dans Script.Cpp, remplacez la ligne `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT );` avec `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT.m_psz );`et la ligne `TRACE( "Source Text: %s\n", COLE2CT( bstrSourceLineText ) );` avec `TRACE( "Source Text: %s\n", bstrSourceLineText );`.<br/>
    > Pour les erreurs impliquant `HMONITOR`, ouvrez StdAfx.h dans le `TCProps` de projet et remplacez :
    > ```
    > #ifndef WINVER  
    > #define WINVER 0x0400   
    > #endif
    > ```
    > par
    > ```
    > #ifndef WINVER  
    > #define WINVER 0x0500
    > #define _WIN32_WINNT 0x0500
    > #endif
    > ```

1. Dans **Test Container**, dans le **modifier** menu, cliquez sur **insérer un nouveau contrôle**.

1. Recherchez votre contrôle, qui sera appelée `PolyCtl class`, puis cliquez sur **OK**. Vous verrez un triangle vert dans un cercle.

Essayez de modifier le nombre de côtés en suivant la procédure suivante. Pour modifier les propriétés sur une interface double depuis **Test Container**, utilisez **appeler les méthodes**.

### <a name="to-modify-a-controls-property-from-within-the-test-container"></a>Pour modifier la propriété d’un contrôle à partir du conteneur de Test

1. Dans **Test Container**, cliquez sur **appeler les méthodes** sur le **contrôle** menu.

    Le **appeler une méthode** boîte de dialogue s’affiche.

1. Sélectionnez le **PropPut** version de la **côtés** propriété à partir de la **nom de la méthode** zone de liste déroulante.

1. Type `5` dans le **valeur du paramètre** , cliquez sur **définir la valeur**, puis cliquez sur **Invoke**.

Notez que le contrôle ne change pas. Bien que vous avez modifié le nombre de côtés en interne en définissant le `m_nSides` variable, cela n’a pas entraîné le contrôle à redessiner. Si vous basculez vers une autre application et revenez ensuite à **Test Container**, vous constaterez que le contrôle a été redessiné et a le nombre correct de côtés.

Pour corriger ce problème, ajoutez un appel à la `FireViewChange` fonction, définie dans `IViewObjectExImpl`, après avoir défini le nombre de côtés. Si le contrôle s’exécute dans sa propre fenêtre, `FireViewChange` appellera le `InvalidateRect` directement la méthode. Si le contrôle est en cours d’exécution sans fenêtre, le `InvalidateRect` méthode sera appelée sur l’interface du conteneur site. Cela force le contrôle à se redessiner.

### <a name="to-add-a-call-to-fireviewchange"></a>Pour ajouter un appel à FireViewChange

1. Mettre à jour PolyCtl.cpp en ajoutant l’appel à `FireViewChange` à la `put_Sides` (méthode). Lorsque vous avez terminé, le `put_Sides` méthode doit ressembler à ceci :

    [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]

Après avoir ajouté `FireViewChange`, reconstruire et essayez le contrôle dans le contrôle ActiveX Test Container. Cette fois, lorsque vous modifiez le nombre de côtés et cliquez sur `Invoke`, vous devez voir le contrôle changer immédiatement.

Dans l’étape suivante, vous allez ajouter un événement.

[À l’étape 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124; [à l’étape 5](../atl/adding-an-event-atl-tutorial-part-5.md)

## <a name="see-also"></a>Voir aussi

[Didacticiel](../atl/active-template-library-atl-tutorial.md)<br/>
[Test des propriétés et des événements avec le conteneur de test](../mfc/testing-properties-and-events-with-test-container.md)
