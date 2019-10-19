---
title: Disposition dynamique
ms.date: 09/09/2019
ms.assetid: 8598cfb2-c8d4-4f5a-bf2b-59dc4653e042
ms.openlocfilehash: 1b0d035d3c551fd309d515ccb8b22159218c1b0a
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "70907548"
---
# <a name="dynamic-layout"></a>Disposition dynamique

Avec MFC dans Visual Studio 2015, vous pouvez créer des boîtes de dialogue que l’utilisateur peut redimensionner, et vous pouvez contrôler la façon dont la disposition s’ajuste à la modification de la taille. Par exemple, vous pouvez ancrer des boutons au bas d'une boîte de dialogue sur le bord inférieur afin qu'ils restent toujours affichés à cet endroit. Vous pouvez également créer des contrôles, tels que des zones de liste, des zones d’édition et des champs de texte, qui se développent quand l’utilisateur développe la boîte de dialogue.

## <a name="specifying-dynamic-layout-settings-for-an-mfc-dialog-box"></a>Spécification des paramètres de disposition dynamique pour une boîte de dialogue MFC

Quand l'utilisateur redimensionne une boîte de dialogue, les contrôles qui y figurent peuvent être redimensionnés ou déplacés dans les directions X et Y. Le changement de la taille ou de l'emplacement d'un contrôle quand l'utilisateur redimensionne une boîte de dialogue est appelé disposition dynamique. Par exemple, voici une boîte de dialogue initiale, avant un redimensionnement :

![Boîte de dialogue avant le redimensionnement.](../mfc/media/mfcdynamiclayout4.png "Boîte de dialogue avant redimensionnement.")

Après le redimensionnement de la boîte de dialogue, nous voyons que la zone de liste a été agrandie pour afficher davantage d'éléments et que les boutons ont été déplacés vers le coin inférieur droit :

![Boîte de dialogue après le redimensionnement.](../mfc/media/mfcdynamiclayout5.png "Boîte de dialogue après redimensionnement.")

Vous pouvez contrôler la disposition dynamique en spécifiant les détails de chaque contrôle dans l’éditeur de ressources dans l’IDE, ou vous pouvez le faire par programmation en accédant à l’objet `CMFCDynamicLayout` pour un contrôle particulier et en définissant les propriétés.

### <a name="setting-dynamic-layout-properties-in-the-resource-editor"></a>Définition des propriétés de disposition dynamique dans l'éditeur de ressources

L'éditeur de ressources vous permet de définir le comportement de disposition dynamique pour une boîte de dialogue sans avoir à écrire de code.

#### <a name="to-set-dynamic-layout-properties-in-the-resource-editor"></a>Pour définir les propriétés de disposition dynamique dans l'éditeur de ressources

1. Dans un projet MFC ouvert, ouvrez la boîte de dialogue à configurer dans l'éditeur de boîtes de dialogue.

   ![Ouvrez la boîte de dialogue dans l’éditeur de ressources.](../mfc/media/mfcdynamiclayout3.png "Ouvrez la boîte de dialogue dans l'éditeur de ressources.")

1. Sélectionnez un contrôle et, dans la fenêtre **Propriétés** (dans **affichage de classes**), définissez ses propriétés de disposition dynamique. La section **disposition dynamique** de la fenêtre **Propriétés** contient les propriétés **type de déplacement**, type de **redimensionnement**et, en fonction des valeurs sélectionnées pour ces propriétés, des propriétés spécifiques qui définissent le nombre de contrôles qui déplacent ou Modifiez la taille. Le **type de déplacement** détermine la façon dont un contrôle est déplacé lorsque la taille de la boîte de dialogue est modifiée. Le **type de dimensionnement** détermine la façon dont un contrôle est redimensionné lorsque la taille de la boîte de dialogue est modifiée. Le type de **déplacement** et le **type de dimensionnement** peuvent être **horizontaux**, **verticaux**, **les deux**ou **aucun** en fonction des dimensions que vous souhaitez modifier dynamiquement. Le type Horizontal correspond à la dimension X et le type Vertical, à la dimension Y.

1. Si vous souhaitez qu’un contrôle tel qu’un bouton soit à une taille fixe et reste en place en bas à droite, comme c’est le cas pour les boutons **OK** ou **Annuler** , définissez le **type de dimensionnement** sur **aucun**et définissez le **type de déplacement** sur **les deux**. Pour le **déplacement X** et le déplacement des valeurs **Y** sous le **Type de déplacement**, définissez 100% pour que le contrôle conserve une distance fixe à partir du coin inférieur droit.

   ![Disposition dynamique](../mfc/media/mfcdynamiclayout1.png "Disposition dynamique")

1. Supposons que vous voulez aussi créer un contrôle qui s'agrandit à mesure que la boîte de dialogue elle-même est agrandie. En règle générale, un utilisateur développe une boîte de dialogue pour développer une zone d’édition multiligne et augmenter la taille de la zone de texte, ou il développe un contrôle de liste pour afficher davantage de données. Dans ce cas, définissez le **type de dimensionnement** sur les deux et définissez le **type de déplacement** sur aucun. Ensuite, définissez les valeurs de **dimensionnement X** et de **redimensionnement Y** sur 100.

   ![Paramètres de disposition dynamique](../mfc/media/mfcdynamiclayout2.png "Paramètres de disposition dynamique")

1. Faites des essais avec d'autres valeurs qui pourraient convenir pour vos contrôles. Une boîte de dialogue avec une zone de texte d’une seule ligne peut avoir le **type de dimensionnement** **horizontal** uniquement, par exemple.

### <a name="setting-dynamic-layout-properties-programmatically"></a>Définition des propriétés de disposition dynamique par programme

La procédure précédente permet de spécifier les propriétés de disposition dynamique d'une boîte de dialogue au moment du design, mais si vous souhaitez contrôler la disposition dynamique au moment de l'exécution, définissez les propriétés de disposition dynamique par programme.

#### <a name="to-set-dynamic-layout-properties-programmatically"></a>Pour définir les propriétés de disposition dynamique par programme

1. Recherchez ou ajoutez un emplacement dans le code d'implémentation de votre classe de boîte de dialogue où vous souhaitez spécifier la disposition dynamique de la boîte de dialogue. Par exemple, vous pouvez ajouter la méthode `AdjustLayout` dans votre boîte de dialogue et l'appeler à chaque endroit où la disposition doit être modifiée. Vous pouvez l'appeler d'abord à partir du constructeur ou après avoir apporté les modifications à la boîte de dialogue.

1. Pour la boîte de dialogue, appelez [GetDynamicLayout](../mfc/reference/cwnd-class.md#getdynamiclayout), une méthode de la classe `CWnd`. `GetDynamicLayout` retourne un pointeur vers un objet `CMFCDynamicLayout` .

    ```cpp
    CMFCDynamicLayout* dynamicLayout = pDialog->GetDynamicLayout();
    ```

1. Pour le premier contrôle auquel vous souhaitez ajouter un comportement dynamique, utilisez les méthodes statiques sur la classe de disposition dynamique pour créer la structure [MoveSettings](../mfc/reference/cmfcdynamiclayout-class.md#movesettings_structure) qui encode la manière dont le contrôle doit être ajusté. Pour ce faire, vous devez d’abord choisir la méthode statique appropriée : [CMFCDynamicLayout :: MoveHorizontal](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontal), [CMFCDynamicLayout :: MoveVertical](../mfc/reference/cmfcdynamiclayout-class.md#movevertical), [CMFCDynamicLayout :: MoveNone](../mfc/reference/cmfcdynamiclayout-class.md#movenone)ou [CMFCDynamicLayout :: MoveHorizontalAndVertical ](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical). Vous passez ensuite le pourcentage du déplacement horizontal et/ou du déplacement vertical. Toutes ces méthodes statiques retournent un nouvel objet MoveSettings que vous pouvez ensuite utiliser pour spécifier le comportement de déplacement d'un contrôle.

   N'oubliez pas que la valeur 100 signifie que le contrôle sera déplacé autant que nécessaire par rapport à la taille modifiée de la boîte de dialogue. L'un des bords du contrôle restera donc à une distance fixe de la nouvelle bordure.

    ```cpp
    MoveSettings moveSettings = CMFCDynamicLayout::MoveHorizontal(100);
    ```

1. Effectuez la même opération pour le comportement de taille, qui utilise le type [SizeSettings](../mfc/reference/cmfcdynamiclayout-class.md#sizesettings_structure) . Par exemple, pour spécifier qu'un contrôle ne change pas de taille quand la boîte de dialogue est redimensionnée, utilisez le code suivant :

    ```cpp
    SizeSettings sizeSettings = CMFCDynamicLayout::SizeNone();
    ```

1. Ajoutez le contrôle au gestionnaire de présentation dynamique à l’aide de la méthode [CMFCDynamicLayout :: AddItem](../mfc/reference/cmfcdynamiclayout-class.md#additem) . Il existe deux surcharges correspondant aux différentes manières de spécifier le contrôle souhaité. L'une prend le handle de fenêtre (HWND) du contrôle et l'autre prend l'ID du contrôle.

    ```cpp
    dynamicLayout->AddItem(hWndControl,
    moveSettings,
    sizeSettings);
    ```

1. Répétez l'opération pour chaque contrôle devant être déplacé ou redimensionné.

1. Si nécessaire, peut utiliser la méthode [CMFCDynamicLayout :: HasItem](../mfc/reference/cmfcdynamiclayout-class.md#hasitem) pour déterminer si un contrôle figure déjà dans la liste des contrôles soumis à des modifications de disposition dynamique, ou la méthode [CMFCDynamicLayout :: IsEmpty](../mfc/reference/cmfcdynamiclayout-class.md#isempty) pour déterminer s’il existe des contrôles qui sont sujettes à des modifications.

1. Pour activer la disposition de la boîte de dialogue, appelez la méthode [CWnd :: EnableDynamicLayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) .

    ```cpp
    pDialog->EnableDynamicLayout(TRUE);
    ```

1. La prochaine fois que l’utilisateur redimensionne la boîte de dialogue, la méthode [CMFCDynamicLayout :: Adjust](../mfc/reference/cmfcdynamiclayout-class.md#adjust) est appelée, ce qui applique réellement les paramètres.

1. Si vous souhaitez désactiver la disposition dynamique, appelez [CWnd :: EnableDynamicLayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) avec **false** comme pour le paramètre *bEnabled* .

    ```cpp
    pDialog->EnableDynamicLayout(FALSE);
    ```

#### <a name="to-set-the-dynamic-layout-programmatically-from-a-resource-file"></a>Pour définir la disposition dynamique par programme à partir d'un fichier de ressources

1. Utilisez la méthode [CMFCDynamicLayout :: MoveHorizontalAndVertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical) pour spécifier un nom de ressource dans le fichier de script de ressources approprié (fichier. RC) qui spécifie des informations de disposition dynamique, comme dans l’exemple suivant :

    ```cpp
    dynamicLayout->LoadResource("IDD_DIALOG1");
    ```

   La ressource nommée doit faire référence à une boîte de dialogue qui contient des informations de disposition sous la forme d’une entrée **AFX_DIALOG_LAYOUT** dans le fichier de ressources, comme dans l’exemple suivant :

    ```RC
    /////////////////////////////////////////////////////////////////////////////
    //
    // AFX_DIALOG_LAYOUT
    //

    IDD_MFCAPPLICATION1_DIALOG AFX_DIALOG_LAYOUT
    BEGIN
    0x0000,
    0x6400,
    0x0028,
    0x643c,
    0x0028
    END

    IDD_DIALOG1 AFX_DIALOG_LAYOUT
    BEGIN
    0x0000,
    0x6464,
    0x0000,
    0x6464,
    0x0000,
    0x0000,
    0x6464,
    0x0000,
    0x0000

    END
    ```

## <a name="see-also"></a>Voir aussi

[CMFCDynamicLayout, classe](../mfc/reference/cmfcdynamiclayout-class.md)<br/>
[Classes de contrôle](../mfc/control-classes.md)<br/>
[Classes de boîte de dialogue](../mfc/dialog-box-classes.md)<br/>
[Éditeur de boîtes de dialogue](../windows/dialog-editor.md)<br/>
[Disposition de dialogue dynamique pour MFC dans C++ Visual 2015](https://mariusbancila.ro/blog/2015/07/27/dynamic-dialog-layout-for-mfc-in-visual-c-2015/)
