---
title: Disposition dynamique
ms.date: 11/19/2018
ms.assetid: 8598cfb2-c8d4-4f5a-bf2b-59dc4653e042
ms.openlocfilehash: 396aad5b33a00021ddb5c1143c1d15c130e97eaa
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175686"
---
# <a name="dynamic-layout"></a>Disposition dynamique

Avec MFC dans Visual Studio 2015, vous pouvez créer des boîtes de dialogue que l’utilisateur peut redimensionner, et vous pouvez contrôler la façon que la disposition s’ajuste aux changements de taille. Par exemple, vous pouvez ancrer des boutons au bas d'une boîte de dialogue sur le bord inférieur afin qu'ils restent toujours affichés à cet endroit. Vous pouvez également créer des contrôles, tels que des zones de liste, des zones d'édition et des champs de texte, qui s'agrandissent quand l'utilisateur agrandit la boîte de dialogue.

## <a name="specifying-dynamic-layout-settings-for-an-mfc-dialog-box"></a>Spécification des paramètres de disposition dynamique pour une boîte de dialogue MFC

Quand l'utilisateur redimensionne une boîte de dialogue, les contrôles qui y figurent peuvent être redimensionnés ou déplacés dans les directions X et Y. Le changement de la taille ou de l'emplacement d'un contrôle quand l'utilisateur redimensionne une boîte de dialogue est appelé disposition dynamique. Par exemple, voici une boîte de dialogue initiale, avant un redimensionnement :

![Boîte de dialogue avant redimensionnement. ](../mfc/media/mfcdynamiclayout4.png "Boîte de dialogue avant redimensionnement.")

Après le redimensionnement de la boîte de dialogue, nous voyons que la zone de liste a été agrandie pour afficher davantage d'éléments et que les boutons ont été déplacés vers le coin inférieur droit :

![Boîte de dialogue après redimensionnement. ](../mfc/media/mfcdynamiclayout5.png "Boîte de dialogue après redimensionnement.")

Vous pouvez contrôler la disposition dynamique en spécifiant les détails de chaque contrôle dans l’éditeur de ressources dans l’IDE, ou vous pouvez effectuer par programme en accédant à la `CMFCDynamicLayout` de l’objet d’un contrôle particulier et définition des propriétés.

### <a name="setting-dynamic-layout-properties-in-the-resource-editor"></a>Définition des propriétés de disposition dynamique dans l'éditeur de ressources

L'éditeur de ressources vous permet de définir le comportement de disposition dynamique pour une boîte de dialogue sans avoir à écrire de code.

#### <a name="to-set-dynamic-layout-properties-in-the-resource-editor"></a>Pour définir les propriétés de disposition dynamique dans l'éditeur de ressources

1. Dans un projet MFC ouvert, ouvrez la boîte de dialogue à configurer dans l'éditeur de boîtes de dialogue.

   ![Ouvrez la boîte de dialogue dans l’éditeur de ressources. ](../mfc/media/mfcdynamiclayout3.png "Ouvrir la boîte de dialogue dans l’éditeur de ressources.")

1. Sélectionnez un contrôle et, dans la fenêtre Propriétés, définissez ses propriétés de disposition dynamique. Le **disposition dynamique** section dans la fenêtre Propriétés contient les propriétés **Type de déplacement**, **Type de redimensionnement**et, en fonction des valeurs sélectionnées pour ces propriétés, les propriétés spécifiques qui définissent la quantité de contrôles déplacement ou modifier la taille. **Type de déplacement** détermine la façon dont un contrôle est déplacé que la taille de la boîte de dialogue est modifiée ; **Type de redimensionnement** détermine comment un contrôle est redimensionné que la taille de la boîte de dialogue est modifiée. **Type de déplacement** et **Type de redimensionnement** peut être **Horizontal**, **Vertical**, **à la fois**, ou **aucun**selon les dimensions que vous souhaitez changer de manière dynamique. Le type Horizontal correspond à la dimension X et le type Vertical, à la dimension Y.

1. Si vous souhaitez un contrôle tel qu’un bouton à une taille fixe et restent en place en bas à droite, comme cela est courant pour les **OK** ou **Annuler** boutons, définissez la **Type de redimensionnement** à  **Aucun**et définissez le **Type de déplacement** à **les deux**. Pour le **déplacement X** et **déplacement Y** valeurs sous **Type de déplacement**, définir 100 % pour que le contrôle de rester une distance fixe à partir de la partie inférieure droite.

   ![Disposition dynamique](../mfc/media/mfcdynamiclayout1.png "disposition dynamique")

1. Supposons que vous voulez aussi créer un contrôle qui se développe à mesure que la boîte de dialogue elle-même est développée. En règle générale, un utilisateur développe une boîte de dialogue pour développer une zone d’édition multiligne et augmenter la taille de la zone de texte, ou il développe un contrôle de liste pour afficher davantage de données. Dans ce cas, définissez le **Type de redimensionnement** pour les deux et définissez le **Type de déplacement** sur none. Ensuite, définissez le **redimensionnement X** et **redimensionnement Y** valeurs à 100.

   ![Paramètres de disposition dynamique](../mfc/media/mfcdynamiclayout2.png "paramètres de disposition dynamique")

1. Faites des essais avec d'autres valeurs qui pourraient convenir pour vos contrôles. Une boîte de dialogue avec une seule ligne d’une zone de texte peut avoir le **Type de redimensionnement** définie sur **Horizontal** uniquement, par exemple.

### <a name="setting-dynamic-layout-properties-programmatically"></a>Définition des propriétés de disposition dynamique par programme

La procédure précédente permet de spécifier les propriétés de disposition dynamique d'une boîte de dialogue au moment du design, mais si vous souhaitez contrôler la disposition dynamique au moment de l'exécution, définissez les propriétés de disposition dynamique par programme.

#### <a name="to-set-dynamic-layout-properties-programmatically"></a>Pour définir les propriétés de disposition dynamique par programme

1. Recherchez ou ajoutez un emplacement dans le code d'implémentation de votre classe de boîte de dialogue où vous souhaitez spécifier la disposition dynamique de la boîte de dialogue. Par exemple, vous pouvez ajouter la méthode `AdjustLayout` dans votre boîte de dialogue et l'appeler à chaque endroit où la disposition doit être modifiée. Vous pouvez l'appeler d'abord à partir du constructeur ou après avoir apporté les modifications à la boîte de dialogue.

1. Pour la boîte de dialogue, appelez [GetDynamicLayout](../mfc/reference/cwnd-class.md#getdynamiclayout), une méthode de la `CWnd` classe. `GetDynamicLayout` retourne un pointeur vers un objet `CMFCDynamicLayout` .

    ```cpp
    CMFCDynamicLayout* dynamicLayout = pDialog->GetDynamicLayout();
    ```

1. Pour le premier contrôle auquel vous souhaitez ajouter le comportement dynamique, utilisez les méthodes statiques sur la classe de disposition dynamique pour créer le [MoveSettings](../mfc/reference/cmfcdynamiclayout-class.md#movesettings_structure) structure qui encode la manière que le contrôle doit être ajusté. Pour ce faire, premier choix de la méthode statique appropriée : [CMFCDynamicLayout::MoveHorizontal](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontal), [CMFCDynamicLayout::MoveVertical](../mfc/reference/cmfcdynamiclayout-class.md#movevertical), [CMFCDynamicLayout::MoveNone](../mfc/reference/cmfcdynamiclayout-class.md#movenone), ou [CMFCDynamicLayout::MoveHorizontalAndVertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical). Vous passez ensuite le pourcentage du déplacement horizontal et/ou du déplacement vertical. Toutes ces méthodes statiques retournent un nouvel objet MoveSettings que vous pouvez ensuite utiliser pour spécifier le comportement de déplacement d'un contrôle.

   N'oubliez pas que la valeur 100 signifie que le contrôle sera déplacé autant que nécessaire par rapport à la taille modifiée de la boîte de dialogue. L'un des bords du contrôle restera donc à une distance fixe de la nouvelle bordure.

    ```cpp
    MoveSettings moveSettings = CMFCDynamicLayout::MoveHorizontal(100);
    ```

1. Faire la même chose pour le comportement de taille, qui utilise le [SizeSettings](../mfc/reference/cmfcdynamiclayout-class.md#sizesettings_structure) type. Par exemple, pour spécifier qu'un contrôle ne change pas de taille quand la boîte de dialogue est redimensionnée, utilisez le code suivant :

    ```cpp
    SizeSettings sizeSettings = CMFCDynamicLayout::SizeNone();
    ```

1. Ajouter le contrôle au Gestionnaire de disposition dynamique à l’aide de la [CMFCDynamicLayout::AddItem](../mfc/reference/cmfcdynamiclayout-class.md#additem) (méthode). Il existe deux surcharges correspondant aux différentes manières de spécifier le contrôle souhaité. L'une prend le handle de fenêtre (HWND) du contrôle et l'autre prend l'ID du contrôle.

    ```cpp
    dynamicLayout->AddItem(hWndControl,
    moveSettings,
    sizeSettings);
    ```

1. Répétez l'opération pour chaque contrôle devant être déplacé ou redimensionné.

1. Si nécessaire, utilisez le [CMFCDynamicLayout::HasItem](../mfc/reference/cmfcdynamiclayout-class.md#hasitem) méthode pour déterminer si un contrôle est déjà dans la liste des contrôles soumis aux modifications de disposition dynamique, ou le [CMFCDynamicLayout::IsEmpty](../mfc/reference/cmfcdynamiclayout-class.md#isempty) méthode pour déterminer s’il existe des contrôles qui sont soumis à des modifications.

1. Pour activer la mise en page de boîte de dialogue, appelez le [CWnd::EnableDynamicLayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) (méthode).

    ```cpp
    pDialog->EnableDynamicLayout(TRUE);
    ```

1. La prochaine fois que l’utilisateur redimensionne la boîte de dialogue, le [CMFCDynamicLayout::Adjust](../mfc/reference/cmfcdynamiclayout-class.md#adjust) méthode est appelée, et les paramètres.

1. Si vous souhaitez désactiver la disposition dynamique, appelez [CWnd::EnableDynamicLayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) avec **FALSE** que pour le *case d’option bActivé* paramètre.

    ```cpp
    pDialog->EnableDynamicLayout(FALSE);
    ```

#### <a name="to-set-the-dynamic-layout-programmatically-from-a-resource-file"></a>Pour définir la disposition dynamique par programme à partir d'un fichier de ressources

1. Utilisez le [CMFCDynamicLayout::MoveHorizontalAndVertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical) méthode pour spécifier un nom de ressource dans le fichier de script de ressources correspondant (fichier .rc) qui spécifie les informations de disposition dynamique, comme dans l’exemple suivant :

    ```cpp
    dynamicLayout->LoadResource("IDD_DIALOG1");
    ```

   La ressource nommée doit faire référence à une boîte de dialogue qui contient des informations de mise en page sous la forme d’un **AFX_DIALOG_LAYOUT** entrée dans le fichier de ressources, comme dans l’exemple suivant :

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
[Mise en page de boîte de dialogue dynamique de MFC dans Visual C++ 2015](https://mariusbancila.ro/blog/2015/07/27/dynamic-dialog-layout-for-mfc-in-visual-c-2015/)
