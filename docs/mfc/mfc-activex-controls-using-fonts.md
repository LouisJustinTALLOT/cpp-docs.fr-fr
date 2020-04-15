---
title: 'Contrôles ActiveX MFC : utilisation des polices'
ms.date: 11/19/2018
f1_keywords:
- OnFontChanged
- HeadingFont
- InternalFont
helpviewer_keywords:
- notifications [MFC], MFC ActiveX controls fonts
- OnDraw method, MFC ActiveX controls
- InternalFont method [MFC]
- SetFont method [MFC]
- OnFontChanged method [MFC]
- IPropertyNotifySink class [MFC]
- MFC ActiveX controls [MFC], fonts
- Stock Font property [MFC]
- HeadingFont property [MFC]
- GetFont method [MFC]
- SelectStockFont method [MFC]
- fonts [MFC], ActiveX controls
ms.assetid: 7c51d602-3f5a-481d-84d1-a5d8a3a71761
ms.openlocfilehash: c336ec6c29b5478655ca8f19f71378a2b446ac64
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358272"
---
# <a name="mfc-activex-controls-using-fonts"></a>Contrôles ActiveX MFC : utilisation des polices

Si votre contrôle ActiveX affiche le texte, vous pouvez permettre à l’utilisateur de contrôle de modifier l’apparence du texte en modifiant une propriété de police. Les propriétés de police sont implémentées comme des objets de police et peuvent être l’un des deux types : stock ou coutume. Les propriétés Stock Font sont des propriétés de police préimplées que vous pouvez ajouter à l’aide de l’Add Property Wizard. Les propriétés Custom Font ne sont pas préimplisées et le développeur de contrôle détermine le comportement et l’utilisation de la propriété.

Cet article aborde les thèmes suivants :

- [Utilisation de la propriété Stock Font](#_core_using_the_stock_font_property)

- [Utilisation de propriétés de police personnalisées dans votre contrôle](#_core_implementing_a_custom_font_property)

## <a name="using-the-stock-font-property"></a><a name="_core_using_the_stock_font_property"></a>Utilisation de la propriété Stock Font

Stock Font propriétés sont préimpliste par la classe [COleControl](../mfc/reference/colecontrol-class.md). En outre, une page de propriété Font standard est également disponible, permettant à l’utilisateur de modifier divers attributs de l’objet de police, tels que son nom, sa taille et son style.

Accédez à l’objet de police par le [GetFont](../mfc/reference/colecontrol-class.md#getfont), `COleControl` [SetFont](../mfc/reference/colecontrol-class.md#setfont), et [InternalGetFont](../mfc/reference/colecontrol-class.md#internalgetfont) fonctions de . L’utilisateur de contrôle accédera `GetFont` `SetFont` à l’objet de police via l’objet et fonctionne de la même manière que n’importe quelle autre propriété Get/Set. Lorsque l’accès à l’objet de police `InternalGetFont` est nécessaire à partir d’un contrôle, utilisez la fonction.

Comme discuté dans [MFC ActiveX Controls: Properties](../mfc/mfc-activex-controls-properties.md), l’ajout de propriétés stock est facile avec le [Assistant De propriété Add](../ide/names-add-property-wizard.md). Vous choisissez la propriété Font, et l’Add Property Wizard insère automatiquement l’entrée de la fonte de stock dans la carte de répartition du contrôle.

#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>Pour ajouter la propriété De font d’actions à l’aide de l’Assistant De propriété Add

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. À partir du menu raccourci, cliquez sur **Ajouter** et cliquez ensuite **ajouter la propriété**.

   Cela ouvre le Assistant De propriété Add.

1. Dans la case **Nom de propriété,** cliquez sur **Font**.

1. Cliquez sur **Terminer**.

L’Assistant De propriété Add ajoute la ligne suivante à la carte de répartition du contrôle, située dans le fichier de mise en œuvre de la classe de contrôle :

[!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]

En outre, l’Add Property Wizard ajoute la ligne suivante au contrôle . Fichier IDL:

[!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]

La propriété caption stock est un exemple d’une propriété de texte qui peut être tirée en utilisant les informations de propriété de font de stock. L’ajout de la propriété de caption de stock au contrôle utilise des étapes similaires à celles utilisées pour la propriété De font d’actions.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Pour ajouter la propriété de légende de stock utilisant le Magicien de propriété d’ajouter

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. À partir du menu raccourci, cliquez sur **Ajouter** et cliquez ensuite **ajouter la propriété**.

   Cela ouvre le Assistant De propriété Add.

1. Dans la boîte **nom de propriété,** cliquez sur **caption**.

1. Cliquez sur **Terminer**.

L’Assistant De propriété Add ajoute la ligne suivante à la carte de répartition du contrôle, située dans le fichier de mise en œuvre de la classe de contrôle :

[!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]

## <a name="modifying-the-ondraw-function"></a><a name="_core_modifying_the_ondraw_function"></a>Modification de la fonction OnDraw

La mise `OnDraw` en œuvre par défaut de utilise la police du système Windows pour tout le texte affiché dans le contrôle. Cela signifie que vous `OnDraw` devez modifier le code en sélectionnant l’objet de police dans le contexte de l’appareil. Pour ce faire, appelez [COleControl : SelectStockFont](../mfc/reference/colecontrol-class.md#selectstockfont) et passez le contexte de l’appareil de contrôle, comme le montre l’exemple suivant :

[!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]

Une `OnDraw` fois que la fonction a été modifiée pour utiliser l’objet de police, tout texte dans le contrôle est affiché avec des caractéristiques de la propriété de la commande de fonte de stock.

## <a name="using-custom-font-properties-in-your-control"></a><a name="_core_using_custom_font_properties_in_your_control"></a>Utilisation de propriétés de police personnalisées dans votre contrôle

En plus de la propriété Stock Font, le contrôle ActiveX peut avoir des propriétés Font personnalisées. Pour ajouter une propriété de police personnalisée, vous devez :

- Utilisez l’Assistant De propriété Add pour implémenter la propriété Font personnalisée.

- [Traitement des notifications de police](#_core_processing_font_notifications).

- [Mise en œuvre d’une nouvelle interface de notification de police](#_core_implementing_a_new_font_notification_interface).

### <a name="implementing-a-custom-font-property"></a><a name="_core_implementing_a_custom_font_property"></a>Mise en œuvre d’une propriété Custom Font

Pour implémenter une propriété De police personnalisée, vous utilisez l’Assistant De propriété Add pour ajouter la propriété et ensuite apporter quelques modifications au code. Les sections suivantes décrivent comment `HeadingFont` ajouter la propriété personnalisée au contrôle de l’échantillon.

##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>Pour ajouter la propriété Custom Font à l’aide de l’Add Property Wizard

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. À partir du menu raccourci, cliquez sur **Ajouter** et cliquez ensuite **ajouter la propriété**.

   Cela ouvre le Assistant De propriété Add.

1. Dans la boîte **nom de propriété,** tapez un nom pour la propriété. Pour cet exemple, utilisez **HeadingFont**.

1. Pour **Type d’implémentation**, cliquez sur **Méthodes Get/Set**.

1. Dans la boîte **de type de propriété,** sélectionnez **IDispatch** <strong>\*</strong> pour le type de propriété.

1. Cliquez sur **Terminer**.

L’Assistant De propriété Add `HeadingFont` crée le `CSampleCtrl` code pour ajouter la propriété personnalisée à la classe et à l’SAMPLE. Fichier IDL. Parce `HeadingFont` qu’il s’agit d’un type `CSampleCtrl` de propriété Get/Set, l’Assistant De propriété Add modifie la carte de répartition de la classe pour inclure une DISP_PROPERTY_EX_ID[DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex) entrée macro :

[!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]

Le macro DISP_PROPERTY_EX associe `HeadingFont` le nom `CSampleCtrl` de propriété à `GetHeadingFont` ses `SetHeadingFont`méthodes get and Set de classe correspondante, et . Le type de valeur de la propriété est également spécifié; dans ce cas, VT_FONT.

L’Assistant De propriété Add ajoute également une déclaration dans le fichier d’en-tête de contrôle (. H) pour `GetHeadingFont` `SetHeadingFont` les fonctions et les fonctions et ajoute leurs modèles de fonction dans le fichier de mise en œuvre de contrôle (. RPC:

[!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]

Enfin, l’Add Property Wizard modifie le contrôle . Fichier IDL en ajoutant `HeadingFont` une entrée pour la propriété:

[!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]

### <a name="modifications-to-the-control-code"></a>Modifications apportées au Code de contrôle

Maintenant que vous `HeadingFont` avez ajouté la propriété au contrôle, vous devez apporter quelques modifications à l’en-tête de contrôle et les fichiers de mise en œuvre pour prendre pleinement en charge la nouvelle propriété.

Dans le fichier d’en-tête de contrôle (. H), ajouter la déclaration suivante d’une variable de membre protégé :

[!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]

Dans le fichier de mise en œuvre de contrôle (. RPC), faites ce qui suit :

- Initialiser *m_fontHeading* dans le constructeur de contrôle.

   [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]

- Déclarez une structure STATIQUE DE FONTDESC contenant des attributs par défaut de la police.

   [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]

- Dans la `DoPropExchange` fonction de membre de `PX_Font` contrôle, ajoutez un appel à la fonction. Cela fournit l’initialisation et la persistance pour votre propriété Font personnalisée.

   [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]

- Terminer la mise `GetHeadingFont` en œuvre de la fonction de membre de contrôle.

   [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]

- Terminer la mise `SetHeadingFont` en œuvre de la fonction de membre de contrôle.

   [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]

- Modifier la `OnDraw` fonction de membre de contrôle pour définir une variable pour tenir la police précédemment sélectionnée.

   [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]

- Modifier la `OnDraw` fonction de membre de contrôle pour sélectionner la police personnalisée dans le contexte de l’appareil en ajoutant la ligne suivante où la police doit être utilisée.

   [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]

- Modifier la `OnDraw` fonction de membre de contrôle pour sélectionner la police précédente dans le contexte de l’appareil en ajoutant la ligne suivante après l’utilisation de la police.

   [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]

Une fois la propriété Custom Font implémentée, la page standard de propriété De Font doit être implémentée, permettant aux utilisateurs de contrôle de modifier la police actuelle du contrôle. Pour ajouter l’ID de la page de propriété pour la page standard de propriété De Font, insérez la ligne suivante après la macro BEGIN_PROPPAGEIDS :

[!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]

Vous devez également incrémenter le paramètre de comptage de votre BEGIN_PROPPAGEIDS macro par un. La ligne suivante le montre :

[!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]

Une fois ces changements apportés, reconstruisez l’ensemble du projet afin d’intégrer les fonctionnalités supplémentaires.

### <a name="processing-font-notifications"></a><a name="_core_processing_font_notifications"></a>Traitement des notifications de police

Dans la plupart des cas, le contrôle doit savoir quand les caractéristiques de l’objet de police ont été modifiées. Chaque objet de police est capable de fournir des notifications lorsqu’il change en appelant une fonction membre de l’interface, `IFontNotification` implémentée par `COleControl`.

Si le contrôle utilise la propriété De fonte `OnFontChanged` de stock, ses notifications sont traitées par la fonction membre de `COleControl`. Lorsque vous ajoutez des propriétés de police personnalisées, vous pouvez les faire utiliser la même implémentation. Dans l’exemple de la section précédente, cela a été fait en passant &*m_xFontNotification* lors de l’initialisation de la variable *m_fontHeading* membre.

![Implémentation de plusieurs interfaces d'objet Font](../mfc/media/vc373q1.gif "Implémentation de plusieurs interfaces d'objet Font") <br/>
Mise en œuvre de multiples interfaces d’objets Font

Les lignes solides dans la figure ci-dessus montrent `IFontNotification`que les deux objets de police utilisent la même implémentation de . Cela pourrait causer des problèmes si vous vouliez distinguer quelle police a changé.

Une façon de distinguer les notifications d’objet de police `IFontNotification` du contrôle est de créer une implémentation séparée de l’interface pour chaque objet de police dans le contrôle. Cette technique vous permet d’optimiser votre code de dessin en ne mettant à jour que la chaîne, ou les cordes, qui utilisent la police récemment modifiée. Les sections suivantes démontrent les étapes nécessaires pour implémenter des interfaces de notification séparées pour une deuxième propriété De Font. La deuxième propriété de police `HeadingFont` est supposée être la propriété qui a été ajoutée dans la section précédente.

### <a name="implementing-a-new-font-notification-interface"></a><a name="_core_implementing_a_new_font_notification_interface"></a>Mise en œuvre d’une nouvelle interface de notification De police

Pour distinguer les notifications de deux polices ou plus, une nouvelle interface de notification doit être implémentée pour chaque police utilisée dans le contrôle. Les sections suivantes décrivent comment implémenter une nouvelle interface de notification de police en modifiant l’en-tête de contrôle et les fichiers de implémentation.

### <a name="additions-to-the-header-file"></a>Ajouts au fichier d’en-tête

Dans le fichier d’en-tête de contrôle (. H), ajouter les lignes suivantes à la déclaration de classe :

[!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]

Cela crée une `IPropertyNotifySink` implémentation de l’interface appelée `HeadingFontNotify`. Cette nouvelle interface contient `OnChanged`une méthode appelée .

### <a name="additions-to-the-implementation-file"></a>Ajouts au dossier de mise en œuvre

Dans le code qui initialise la police de tête (dans le constructeur de contrôle), changer &*m_xFontNotification* pour &*m_xHeadingFontNotify*. Ensuite, ajoutez le code suivant :

[!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]

Les `AddRef` `Release` méthodes et `IPropertyNotifySink` les méthodes de l’interface gardent une trace du nombre de références pour l’objet de commande ActiveX. Lorsque le contrôle obtient l’accès au `AddRef` pointeur d’interface, le contrôle appelle à incrémenter le nombre de références. Lorsque le contrôle est terminé avec `Release`le pointeur, `GlobalFree` il appelle , de la même manière qui pourrait être appelé à libérer un bloc de mémoire globale. Lorsque le nombre de références pour cette interface passe à zéro, l’implémentation de l’interface peut être libérée. Dans cet exemple, la `QueryInterface` fonction `IPropertyNotifySink` renvoie un pointeur à une interface sur un objet particulier. Cette fonction permet à un contrôle ActiveX de poser des questions à un objet pour déterminer quelles interfaces il prend en charge.

Une fois ces modifications apportées à votre projet, reconstruisez le projet et utilisez Test Container pour tester l’interface. Pour plus d’informations sur la façon d’accéder au conteneur de test, consultez la page [Test des propriétés et des événements avec le conteneur de test](../mfc/testing-properties-and-events-with-test-container.md) .

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : utilisation d’images dans un contrôle ActiveX](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)<br/>
[Contrôles ActiveX MFC : utilisation des pages de propriétés stock](../mfc/mfc-activex-controls-using-stock-property-pages.md)
