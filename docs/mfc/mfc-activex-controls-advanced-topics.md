---
title: 'Contrôles ActiveX MFC : rubriques avancées'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- MFC ActiveX controls [MFC], accessing invisible dialog controls
- MFC ActiveX controls [MFC], advanced topics
- FireError method [MFC]
- MFC ActiveX controls [MFC], database classes
- MFC ActiveX controls [MFC], special keys
- PreTranslateMessage method [MFC]
- MFC ActiveX controls [MFC], parameterized property
- ThrowError method [MFC]
ms.assetid: e9e34abb-8e2d-461e-bb9c-a1aec5dcecbd
ms.openlocfilehash: c5e3be3915a0707f8df17d3c9ebe2eb0e4f623b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364638"
---
# <a name="mfc-activex-controls-advanced-topics"></a>Contrôles ActiveX MFC : rubriques avancées

Cet article couvre des sujets avancés liés au développement de contrôles ActiveX. notamment :

- [Utilisation des classes de base de données dans les contrôles ActiveX](#_core_using_database_classes_in_activex_controls)

- [Mise en œuvre d’une propriété paramétrée](#_core_implementing_a_parameterized_property)

- [Fautes de manipulation dans votre contrôle ActiveX](#_core_handling_errors_in_your_activex_control)

- [Manipulation des clés spéciales dans le contrôle](#_core_handling_special_keys_in_your_control)

- [Accès aux contrôles de dialogue invisibles à l’heure de la course](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne devrait pas être utilisée pour de nouveaux développements. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, voir [ActiveX Controls](activex-controls.md).

## <a name="using-database-classes-in-activex-controls"></a><a name="_core_using_database_classes_in_activex_controls"></a>Utilisation des classes de base de données dans les contrôles ActiveX

Étant donné que les classes de contrôle ActiveX font partie de la bibliothèque de classe, vous pouvez appliquer les mêmes procédures et règles pour l’utilisation des classes de base de données dans une application MFC standard pour développer des contrôles ActiveX qui utilisent les classes de base de données MFC.

Pour un aperçu général des classes de base de données MFC, voir [catégories de bases de données MFC (DAO et ODBC)](../data/mfc-database-classes-odbc-and-dao.md). L’article présente à la fois les classes MFC ODBC et les classes MFC DAO et vous dirige vers plus de détails sur l’un ou l’autre.

> [!NOTE]
> DAO est soutenu par Office 2013. DAO 3.6 est la version finale, et il est considéré comme obsolète. L’environnement visuel et les assistants ne prennent pas en charge DAO (bien que les classes DAO soient incluses et que vous puissiez toujours les utiliser). Microsoft vous recommande d’utiliser [OLE DB Templates](../data/oledb/ole-db-programming.md) ou [ODBC et MFC](../data/odbc/odbc-and-mfc.md) pour de nouveaux projets. Vous ne devez utiliser DAO que pour maintenir les applications existantes.

## <a name="implementing-a-parameterized-property"></a><a name="_core_implementing_a_parameterized_property"></a>Mise en œuvre d’une propriété paramétrée

Une propriété paramétrée (parfois appelée un tableau de propriété) est une méthode pour exposer une collection homogène de valeurs comme une seule propriété du contrôle. Par exemple, vous pouvez utiliser une propriété paramétrée pour exposer un tableau ou un dictionnaire comme une propriété. Dans Visual Basic, une telle propriété est accessible à l’aide de la notation de tableau :

[!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]

Utilisez l’Assistant De propriété Add pour implémenter une propriété paramétrée. L’Add Property Wizard implémente la propriété en ajoutant une paire de fonctions Get/Set qui permettent à l’utilisateur de contrôle d’accéder à la propriété en utilisant la notation ci-dessus ou de la manière standard.

Semblable aux méthodes et aux propriétés, les propriétés paramétrisées ont également une limite au nombre de paramètres autorisés. Dans le cas des propriétés paramétrées, la limite est de 15 paramètres (avec un paramètre réservé au stockage de la valeur de la propriété).

La procédure suivante ajoute une propriété paramétrée, appelée Array, qui peut être consultée comme un tableau bidimensionnel d’intégreurs.

#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>Pour ajouter une propriété paramétrée à l’aide de l’Assistant De la Propriété Add

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. À partir du menu raccourci, cliquez sur **Ajouter** et cliquez ensuite **ajouter la propriété**.

1. Dans la boîte de `Array`nom de **propriété,** type .

1. Dans la boîte **de type de propriété,** sélectionnez **court**.

1. Pour le type **d’implémentation,** cliquez sur **Get/Set Methods**.

1. Dans les boîtes **Get Function** et **Set Function,** tapez des noms uniques pour vos fonctions Get and Set ou acceptez les noms par défaut.

1. Ajoutez un paramètre, appelé *ligne* (type *court*), à l’aide des contrôles **de type Nom paramètre** et **Paramètre.**

1. Ajouter un deuxième paramètre appelé *colonne* (type *court*).

1. Cliquez sur **Terminer**.

### <a name="changes-made-by-the-add-property-wizard"></a>Modifications apportées par l’Assistant De la Propriété Add

Lorsque vous ajoutez une propriété personnalisée, l’Add Property Wizard apporte des modifications à l’en-tête de la classe de contrôle (. H) et la mise en œuvre (. dossiers du RPC).

Les lignes suivantes sont ajoutées à la classe de contrôle . Fichier H:

[!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]

Ce code déclare deux `GetArray` fonctions appelées et `SetArray` qui permettent à l’utilisateur de demander une ligne et une colonne spécifiques lors de l’accès à la propriété.

En outre, l’Add Property Wizard ajoute les lignes suivantes à la carte de répartition des commandes, située dans la mise en œuvre de la classe de contrôle (. Dossier du RPC :

[!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]

Enfin, les implémentations et `GetArray` `SetArray` les fonctions sont ajoutées à la fin de la . Dossier du RPC. Dans la plupart des cas, vous modifierez la fonction Get pour retourner la valeur de la propriété. La fonction Set contiendra généralement du code qui doit s’exécuter, avant ou après les modifications de la propriété.

Pour que cette propriété soit utile, vous pourriez déclarer une variable de membre de tableau bidimensionnelle dans la classe de contrôle, de type **court,** pour stocker des valeurs pour la propriété paramétrée. Vous pouvez ensuite modifier la fonction Get pour retourner la valeur stockée à la ligne et à la colonne appropriées, comme indiqué par les paramètres, et modifier la fonction Set pour mettre à jour la valeur référencée par les paramètres de la ligne et de la colonne.

## <a name="handling-errors-in-your-activex-control"></a><a name="_core_handling_errors_in_your_activex_control"></a>Fautes de manipulation dans votre contrôle ActiveX

Si des conditions d’erreur se produisent dans le contrôle, vous devrez peut-être signaler l’erreur au conteneur de contrôle. Il existe deux méthodes pour signaler les erreurs, selon la situation dans laquelle l’erreur se produit. Si l’erreur se produit dans la fonction Get or Set d’une propriété, ou dans la mise en œuvre d’une méthode d’automatisation OLE, le contrôle doit appeler [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror), qui signale à l’utilisateur de contrôle qu’une erreur s’est produite. Si l’erreur se produit à tout autre moment, le contrôle doit appeler [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror), qui déclenche un événement d’erreur de stock.

Pour indiquer le type d’erreur qui s’est produite, le contrôle doit passer un code d’erreur à `ThrowError` ou `FireError`. Un code d’erreur est un code de statut OLE, qui a une valeur 32 bits. Dans la mesure du possible, choisissez un code d’erreur parmi l’ensemble standard de codes définis dans l’OLECTL. Fichier d’en-tête H. Le tableau suivant résume ces codes.

### <a name="activex-control-error-codes"></a>Codes d’erreur de contrôle ActiveX

|Error|Description|
|-----------|-----------------|
|CTL_E_ILLEGALFUNCTIONCALL|Appel de fonction illégale|
|CTL_E_OVERFLOW|Dépassement|
|CTL_E_OUTOFMEMORY|Mémoire insuffisante|
|CTL_E_DIVISIONBYZERO|Division par zéro|
|CTL_E_OUTOFSTRINGSPACE|Espace de chaîne insuffisant|
|CTL_E_OUTOFSTACKSPACE|Espace de pile insuffisant|
|CTL_E_BADFILENAMEORNUMBER|Nom ou numéro de fichier incorrect|
|CTL_E_FILENOTFOUND|Fichier introuvable|
|CTL_E_BADFILEMODE|Mode de fichier incorrect|
|CTL_E_FILEALREADYOPEN|Le fichier est déjà ouvert.|
|CTL_E_DEVICEIOERROR|Erreur d'E/S de périphérique|
|CTL_E_FILEALREADYEXISTS|Le fichier existe déjà|
|CTL_E_BADRECORDLENGTH|Longueur d'enregistrement incorrecte|
|CTL_E_DISKFULL|Disque plein|
|CTL_E_BADRECORDNUMBER|Numéro d'enregistrement incorrect|
|CTL_E_BADFILENAME|Mauvais nom de fichier|
|CTL_E_TOOMANYFILES|Trop de fichiers|
|CTL_E_DEVICEUNAVAILABLE|Périphérique non disponible|
|CTL_E_PERMISSIONDENIED|Autorisation refusée|
|CTL_E_DISKNOTREADY|Disque non prêt|
|CTL_E_PATHFILEACCESSERROR|Erreur d’accès au chemin/fichier|
|CTL_E_PATHNOTFOUND|Chemin d'accès introuvable|
|CTL_E_INVALIDPATTERNSTRING|Chaîne de modèle non valide|
|CTL_E_INVALIDUSEOFNULL|Utilisation invalide de NULL|
|CTL_E_INVALIDFILEFORMAT|Format de fichier invalide|
|CTL_E_INVALIDPROPERTYVALUE|Valeur de propriété invalide|
|CTL_E_INVALIDPROPERTYARRAYINDEX|Indice de tableau de propriété invalide|
|CTL_E_SETNOTSUPPORTEDATRUNTIME|Set non pris en charge au moment de l’exécution|
|CTL_E_SETNOTSUPPORTED|Set non pris en charge (propriété en lecture seule)|
|CTL_E_NEEDPROPERTYARRAYINDEX|Index de tableau de propriétés requis|
|CTL_E_SETNOTPERMITTED|Set non autorisé|
|CTL_E_GETNOTSUPPORTEDATRUNTIME|Get non pris en charge au moment de l’exécution|
|CTL_E_GETNOTSUPPORTED|Get non pris en charge (propriété en écriture seule)|
|CTL_E_PROPERTYNOTFOUND|Propriété introuvable|
|CTL_E_INVALIDCLIPBOARDFORMAT|Format de presse-papiers invalide|
|CTL_E_INVALIDPICTURE|Image invalide|
|CTL_E_PRINTERERROR|Erreur d'imprimante|
|CTL_E_CANTSAVEFILETOTEMP|Impossible d’enregistrer le fichier à TEMP|
|CTL_E_SEARCHTEXTNOTFOUND|Texte recherché introuvable|
|CTL_E_REPLACEMENTSTOOLONG|Remplacements trop longs|

Si nécessaire, utilisez la macro CUSTOM_CTL_SCODE pour définir un code d’erreur personnalisé pour une condition qui n’est pas couverte par l’un des codes standard. Le paramètre de cette macro devrait être un intégrant entre 1000 et 32767, inclusivement. Par exemple :

[!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]

Si vous créez un contrôle ActiveX pour remplacer un contrôle VBX existant, définissez vos codes d’erreur de contrôle ActiveX avec les mêmes valeurs numériques que le contrôle VBX utilise pour vous assurer que les codes d’erreur sont compatibles.

## <a name="handling-special-keys-in-the-control"></a><a name="_core_handling_special_keys_in_your_control"></a>Manipulation des clés spéciales dans le contrôle

Dans certains cas, vous voudrez peut-être gérer certaines combinaisons de frappes d’une manière spéciale; par exemple, insérez une nouvelle ligne lorsque la clé ENTER est pressée dans un contrôle de boîte de texte multilindite ou déplacez-vous entre un groupe de commandes de modification lorsqu’une pièce d’identité directionnelle pressée.

Si la classe de base `COleControl`de votre contrôle ActiveX est, vous pouvez remplacer [CWnd::PreTranslateMessage](../mfc/reference/cwnd-class.md#pretranslatemessage) pour gérer les messages avant que le conteneur les traite. Lors de l’utilisation **TRUE** de cette technique, toujours retourner `PreTranslateMessage`VRAI si vous manipulez le message dans votre remplacement de .

L’exemple de code suivant montre un moyen possible de traiter tous les messages liés aux clés directionnelles.

[!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]

Pour plus d’informations sur la manipulation des interfaces clavier pour un contrôle ActiveX, consultez la documentation ActiveX SDK.

## <a name="accessing-dialog-controls-that-are-invisible-at-run-time"></a><a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a>Accès aux contrôles de dialogue invisibles à l’heure de la course

Vous pouvez créer des contrôles de dialogue qui n’ont pas d’interface utilisateur et sont invisibles au moment de l’exécution. Si vous ajoutez un contrôle invisible au moment de l’exécution ActiveX à une boîte de dialogue et utilisez [CWnd::GetDlgItem](../mfc/reference/cwnd-class.md#getdlgitem) pour accéder au contrôle, le contrôle ne fonctionnera pas correctement. Au lieu de cela, vous devriez utiliser l’une des techniques suivantes pour obtenir un objet qui représente le contrôle:

- À l’aide de l’assistant variable Add Member, sélectionnez **La variable de contrôle** et sélectionnez ensuite l’ID du contrôle. Entrez un nom variable de membre et sélectionnez la classe d’emballage du contrôle comme type **de contrôle**.

     -ou-

- Déclarez une variable et une sous-classe locales comme élément de dialogue. Insérer le code`CMyCtrl` qui ressemble à ce qui suit (est la classe d’emballage, IDC_MYCTRL1 est l’ID du contrôle):

   [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)
