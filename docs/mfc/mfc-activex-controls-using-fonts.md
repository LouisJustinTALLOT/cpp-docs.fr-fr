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
ms.openlocfilehash: 02c52d2544afdc9d13fc3ec67ad9eed757a3f277
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499689"
---
# <a name="mfc-activex-controls-using-fonts"></a>Contrôles ActiveX MFC : utilisation des polices

Si votre contrôle ActiveX affiche du texte, vous pouvez permettre à l’utilisateur du contrôle de modifier l’apparence du texte en modifiant une propriété font. Les propriétés de police sont implémentées en tant qu’objets de police et peuvent être de l’un des deux types suivants : stock ou personnalisé. Les propriétés de police de stock sont des propriétés de police préimplémentées que vous pouvez ajouter à l’aide de l’Assistant Ajout de propriété. Les propriétés de police personnalisées ne sont pas préimplémentées et le développeur de contrôle détermine le comportement et l’utilisation de la propriété.

Cet article aborde les thèmes suivants :

- [Utilisation de la propriété stock font](#_core_using_the_stock_font_property)

- [Utilisation des propriétés de police personnalisées dans votre contrôle](#_core_implementing_a_custom_font_property)

## <a name="using-the-stock-font-property"></a><a name="_core_using_the_stock_font_property"></a> Utilisation de la propriété stock font

Les propriétés de police de stock sont préimplémentées par la classe [COleControl](reference/colecontrol-class.md). En outre, une page de propriétés de police standard est également disponible, ce qui permet à l’utilisateur de modifier divers attributs de l’objet font, tels que son nom, sa taille et son style.

Accédez à l’objet font via les fonctions [GetFont](reference/colecontrol-class.md#getfont), [SetFont](reference/colecontrol-class.md#setfont)et [InternalGetFont](reference/colecontrol-class.md#internalgetfont) de `COleControl` . L’utilisateur du contrôle accède à l’objet de police via les `GetFont` `SetFont` fonctions et de la même manière que toute autre propriété d’extraction/définition. Lorsque l’accès à l’objet font est requis à partir d’un contrôle, utilisez la `InternalGetFont` fonction.

Comme indiqué dans [contrôles ActiveX MFC : propriétés](mfc-activex-controls-properties.md), l’ajout de propriétés stock est simple grâce à l' [Assistant Ajout de propriété](../ide/adding-a-property-visual-cpp.md#names-add-property-wizard). Vous choisissez la propriété font, et l’Assistant Ajout de propriété insère automatiquement l’entrée de la police stock dans la table de dispatch du contrôle.

#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>Pour ajouter la propriété stock font à l’aide de l’Assistant Ajout de propriété

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **Ajouter** , puis sur **Ajouter une propriété**.

   L’Assistant Ajouter une propriété s’ouvre.

1. Dans la zone nom de la **propriété** , cliquez sur **police**.

1. Cliquez sur **Terminer**.

L’Assistant Ajout de propriété ajoute la ligne suivante au mappage de dispatch du contrôle, situé dans le fichier d’implémentation de la classe du contrôle :

[!code-cpp[NVC_MFC_AxFont#1](codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]

En outre, l’Assistant Ajout de propriété ajoute la ligne suivante au contrôle. Fichier IDL :

[!code-cpp[NVC_MFC_AxFont#2](codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]

La propriété stock Caption est un exemple de propriété Text qui peut être dessinée à l’aide des informations de propriété stock font. L’ajout de la propriété stock Caption au contrôle utilise des étapes similaires à celles utilisées pour la propriété stock font.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Pour ajouter la propriété stock Caption à l’aide de l’Assistant Ajout de propriété

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **Ajouter** , puis sur **Ajouter une propriété**.

   L’Assistant Ajouter une propriété s’ouvre.

1. Dans la zone nom de la **propriété** , cliquez sur **légende**.

1. Cliquez sur **Terminer**.

L’Assistant Ajout de propriété ajoute la ligne suivante au mappage de dispatch du contrôle, situé dans le fichier d’implémentation de la classe du contrôle :

[!code-cpp[NVC_MFC_AxFont#3](codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]

## <a name="modifying-the-ondraw-function"></a><a name="_core_modifying_the_ondraw_function"></a> Modification de la fonction OnDraw

L’implémentation par défaut de `OnDraw` utilise la police système Windows pour tout le texte affiché dans le contrôle. Cela signifie que vous devez modifier le `OnDraw` code en sélectionnant l’objet de police dans le contexte de périphérique. Pour ce faire, appelez [COleControl :: SelectStockFont](reference/colecontrol-class.md#selectstockfont) et transmettez le contexte de périphérique du contrôle, comme indiqué dans l’exemple suivant :

[!code-cpp[NVC_MFC_AxFont#4](codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]

Une fois que la `OnDraw` fonction a été modifiée pour utiliser l’objet font, tout texte contenu dans le contrôle s’affiche avec les caractéristiques de la propriété stock font du contrôle.

## <a name="using-custom-font-properties-in-your-control"></a><a name="_core_using_custom_font_properties_in_your_control"></a> Utilisation des propriétés de police personnalisées dans votre contrôle

En plus de la propriété stock font, le contrôle ActiveX peut avoir des propriétés de police personnalisées. Pour ajouter une propriété de police personnalisée, vous devez :

- Utilisez l’Assistant Ajout d’une propriété pour implémenter la propriété de police personnalisée.

- [Traitement des notifications de polices](#_core_processing_font_notifications).

- [Implémentation d’une nouvelle interface de notification de police](#_core_implementing_a_new_font_notification_interface).

### <a name="implementing-a-custom-font-property"></a><a name="_core_implementing_a_custom_font_property"></a> Implémentation d’une propriété de police personnalisée

Pour implémenter une propriété de police personnalisée, vous utilisez l’Assistant Ajout de propriété pour ajouter la propriété, puis apporter des modifications au code. Les sections suivantes décrivent comment ajouter la `HeadingFont` propriété personnalisée à l’exemple de contrôle.

##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>Pour ajouter la propriété de police personnalisée à l’aide de l’Assistant Ajout de propriété

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **Ajouter** , puis sur **Ajouter une propriété**.

   L’Assistant Ajouter une propriété s’ouvre.

1. Dans la zone nom de la **propriété** , tapez un nom pour la propriété. Pour cet exemple, utilisez **HeadingFont**.

1. Pour **Type d’implémentation**, cliquez sur **Méthodes Get/Set**.

1. Dans la zone **type de propriété** , sélectionnez **IDispatch** <strong>\*</strong> comme type de la propriété.

1. Cliquez sur **Terminer**.

L’Assistant Ajout de propriété crée le code pour ajouter la `HeadingFont` propriété personnalisée à la `CSampleCtrl` classe et à l’exemple. Fichier IDL. Étant donné que `HeadingFont` est un type de propriété obtenir/définir, l’Assistant Ajout de propriété modifie la table de dispatch de la `CSampleCtrl` classe pour inclure un DISP_PROPERTY_EX_ID[DISP_PROPERTY_EX](reference/dispatch-maps.md#disp_property_ex) entrée de macro :

[!code-cpp[NVC_MFC_AxFont#5](codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]

La macro DISP_PROPERTY_EX associe le `HeadingFont` nom de la propriété à ses `CSampleCtrl` méthodes d’extraction et de définition de classe correspondantes, `GetHeadingFont` et `SetHeadingFont` . Le type de la valeur de propriété est également spécifié. dans ce cas, VT_FONT.

L’Assistant Ajout de propriété ajoute également une déclaration dans le fichier d’en-tête du contrôle (. H) pour les `GetHeadingFont` `SetHeadingFont` fonctions et et ajoute leurs modèles de fonction dans le fichier d’implémentation du contrôle (. CPP) :

[!code-cpp[NVC_MFC_AxFont#6](codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]

Enfin, l’Assistant Ajout de propriété modifie le contrôle. Fichier IDL en ajoutant une entrée pour la `HeadingFont` propriété :

[!code-cpp[NVC_MFC_AxFont#7](codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]

### <a name="modifications-to-the-control-code"></a>Modifications du code de contrôle

Maintenant que vous avez ajouté la `HeadingFont` propriété au contrôle, vous devez apporter certaines modifications aux fichiers d’en-tête et d’implémentation du contrôle pour prendre entièrement en charge la nouvelle propriété.

Dans le fichier d’en-tête de contrôle (. H), ajoutez la déclaration suivante d’une variable membre protégée :

[!code-cpp[NVC_MFC_AxFont#8](codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]

Dans le fichier d’implémentation du contrôle (. CPP), procédez comme suit :

- Initialisez *m_fontHeading* dans le constructeur de contrôle.

   [!code-cpp[NVC_MFC_AxFont#9](codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]

- Déclarez une structure FONTDESC statique contenant les attributs par défaut de la police.

   [!code-cpp[NVC_MFC_AxFont#10](codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]

- Dans la `DoPropExchange` fonction membre de contrôle, ajoutez un appel à la `PX_Font` fonction. Cela permet l’initialisation et la persistance de votre propriété de police personnalisée.

   [!code-cpp[NVC_MFC_AxFont#11](codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]

- Terminez l’implémentation de la `GetHeadingFont` fonction membre Control.

   [!code-cpp[NVC_MFC_AxFont#12](codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]

- Terminez l’implémentation de la `SetHeadingFont` fonction membre Control.

   [!code-cpp[NVC_MFC_AxFont#13](codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]

- Modifiez la `OnDraw` fonction membre Control pour définir une variable qui contiendra la police précédemment sélectionnée.

   [!code-cpp[NVC_MFC_AxFont#14](codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]

- Modifiez la `OnDraw` fonction membre de contrôle pour sélectionner la police personnalisée dans le contexte de périphérique en ajoutant la ligne suivante partout où la police doit être utilisée.

   [!code-cpp[NVC_MFC_AxFont#15](codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]

- Modifiez la `OnDraw` fonction membre de contrôle pour resélectionner la police précédente dans le contexte de périphérique en ajoutant la ligne suivante après l’utilisation de la police.

   [!code-cpp[NVC_MFC_AxFont#16](codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]

Une fois la propriété de police personnalisée implémentée, la page de propriétés de police standard doit être implémentée, ce qui permet aux utilisateurs du contrôle de modifier la police actuelle du contrôle. Pour ajouter l’ID de page de propriétés pour la page de propriétés police standard, insérez la ligne suivante après la macro BEGIN_PROPPAGEIDS :

[!code-cpp[NVC_MFC_AxFont#17](codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]

Vous devez également incrémenter d’une unité le paramètre Count de votre macro BEGIN_PROPPAGEIDS. La ligne suivante le montre :

[!code-cpp[NVC_MFC_AxFont#18](codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]

Une fois ces modifications effectuées, reconstruisez le projet entier pour incorporer les fonctionnalités supplémentaires.

### <a name="processing-font-notifications"></a><a name="_core_processing_font_notifications"></a> Traitement des notifications de polices

Dans la plupart des cas, le contrôle doit savoir quand les caractéristiques de l’objet font ont été modifiées. Chaque objet de police est en capacité de fournir des notifications lorsqu’il change en appelant une fonction membre de l' `IFontNotification` interface, implémentée par `COleControl` .

Si le contrôle utilise la propriété stock font, ses notifications sont gérées par la `OnFontChanged` fonction membre de `COleControl` . Lorsque vous ajoutez des propriétés de police personnalisées, vous pouvez leur demander d’utiliser la même implémentation. Dans l’exemple de la section précédente, cela a été accompli en passant &*m_xFontNotification* lors de l’initialisation de la variable membre *m_fontHeading* .

![Implémentation de plusieurs interfaces d'objet Font](../mfc/media/vc373q1.gif "Implémentation de plusieurs interfaces d'objet Font") <br/>
Implémentation de plusieurs interfaces d’objet de police

Les lignes pleines de la figure ci-dessus montrent que les deux objets de police utilisent la même implémentation de `IFontNotification` . Cela peut poser des problèmes si vous souhaitez distinguer la police modifiée.

Une façon de faire la distinction entre les notifications d’objet de police du contrôle consiste à créer une implémentation distincte de l' `IFontNotification` interface pour chaque objet de police dans le contrôle. Cette technique vous permet d’optimiser votre code de dessin en mettant à jour uniquement la chaîne ou les chaînes qui utilisent la police récemment modifiée. Les sections suivantes décrivent les étapes nécessaires pour implémenter des interfaces de notification distinctes pour une deuxième propriété font. La deuxième propriété font est supposée être la `HeadingFont` propriété qui a été ajoutée dans la section précédente.

### <a name="implementing-a-new-font-notification-interface"></a><a name="_core_implementing_a_new_font_notification_interface"></a> Implémentation d’une nouvelle interface de notification de police

Pour faire la distinction entre les notifications d’au moins deux polices, une nouvelle interface de notification doit être implémentée pour chaque police utilisée dans le contrôle. Les sections suivantes décrivent comment implémenter une nouvelle interface de notification de police en modifiant l’en-tête de contrôle et les fichiers d’implémentation.

### <a name="additions-to-the-header-file"></a>Ajouts au fichier d’en-tête

Dans le fichier d’en-tête de contrôle (. H), ajoutez les lignes suivantes à la déclaration de classe :

[!code-cpp[NVC_MFC_AxFont#19](codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]

Cela crée une implémentation de l' `IPropertyNotifySink` interface appelée `HeadingFontNotify` . Cette nouvelle interface contient une méthode appelée `OnChanged` .

### <a name="additions-to-the-implementation-file"></a>Ajouts au fichier d’implémentation

Dans le code qui initialise la police d’en-tête (dans le constructeur de contrôle), remplacez &*m_xFontNotification* par &*m_xHeadingFontNotify*. Ensuite, ajoutez le code suivant :

[!code-cpp[NVC_MFC_AxFont#20](codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]

Les `AddRef` `Release` méthodes et de l' `IPropertyNotifySink` interface assurent le suivi du nombre de références pour l’objet de contrôle ActiveX. Lorsque le contrôle obtient l’accès au pointeur d’interface, le contrôle appelle `AddRef` pour incrémenter le décompte de références. Lorsque le contrôle est terminé avec le pointeur, il appelle `Release` , à peu près de la même façon qu’il `GlobalFree` peut être appelé pour libérer un bloc de mémoire global. Lorsque le nombre de références pour cette interface atteint zéro, l’implémentation de l’interface peut être libérée. Dans cet exemple, la `QueryInterface` fonction retourne un pointeur vers une `IPropertyNotifySink` interface sur un objet particulier. Cette fonction permet à un contrôle ActiveX d’interroger un objet afin de déterminer les interfaces qu’il prend en charge.

Une fois ces modifications apportées à votre projet, régénérez le projet et utilisez le conteneur de test pour tester l’interface. Pour plus d’informations sur la façon d’accéder au conteneur de test, consultez la page [Test des propriétés et des événements avec le conteneur de test](testing-properties-and-events-with-test-container.md) .

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)<br/>
[Contrôles ActiveX MFC : utilisation d’images dans un contrôle ActiveX](mfc-activex-controls-using-pictures-in-an-activex-control.md)<br/>
[Contrôles ActiveX MFC : utilisation des pages de propriétés stock](mfc-activex-controls-using-stock-property-pages.md)
