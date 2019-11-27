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
ms.openlocfilehash: 9f1fa862a30a83cbda049fc63bac6c33a101587b
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305386"
---
# <a name="mfc-activex-controls-advanced-topics"></a>Contrôles ActiveX MFC : rubriques avancées

Cet article traite des sujets avancés relatifs au développement de contrôles ActiveX. Elles incluent notamment :

- [Utilisation des classes de base de données dans les contrôles ActiveX](#_core_using_database_classes_in_activex_controls)

- [Implémentation d’une propriété paramétrable](#_core_implementing_a_parameterized_property)

- [Gestion des erreurs dans votre contrôle ActiveX](#_core_handling_errors_in_your_activex_control)

- [Gestion des clés spéciales dans le contrôle](#_core_handling_special_keys_in_your_control)

- [Accès aux contrôles de boîte de dialogue qui sont invisibles au moment de l’exécution](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

##  <a name="_core_using_database_classes_in_activex_controls"></a>Utilisation des classes de base de données dans les contrôles ActiveX

Étant donné que les classes de contrôles ActiveX font partie de la bibliothèque de classes, vous pouvez appliquer les mêmes procédures et règles d’utilisation des classes de base de données dans une application MFC standard au développement de contrôles ActiveX qui utilisent les classes de base de données MFC.

Pour obtenir une vue d’ensemble générale des classes de base de données MFC, consultez [classes de base de données MFC (DAO et ODBC)](../data/mfc-database-classes-odbc-and-dao.md). L’article présente à la fois les classes ODBC MFC et les classes DAO MFC et vous donne plus de détails sur les deux.

> [!NOTE]
> DAO est pris en charge via Office 2013. DAO 3,6 est la version finale et est considéré comme obsolète. L’environnement C++ visuel et les assistants ne prennent pas en charge DAO (bien que les classes DAO soient incluses et vous puissiez toujours les utiliser). Microsoft vous recommande d’utiliser les [modèles OLE DB](../data/oledb/ole-db-programming.md) ou [ODBC et MFC](../data/odbc/odbc-and-mfc.md) pour les nouveaux projets. Vous ne devez utiliser que DAO pour gérer les applications existantes.

##  <a name="_core_implementing_a_parameterized_property"></a>Implémentation d’une propriété paramétrable

Une propriété paramétrable (parfois appelée un tableau de propriétés) est une méthode permettant d’exposer une collection homogène de valeurs sous la forme d’une propriété unique du contrôle. Par exemple, vous pouvez utiliser une propriété paramétrable pour exposer un tableau ou un dictionnaire en tant que propriété. Dans Visual Basic, une telle propriété est accessible à l’aide de la notation de tableau :

[!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]

Utilisez l’Assistant Ajout d’une propriété pour implémenter une propriété paramétrable. L’Assistant Ajout de propriété implémente la propriété en ajoutant une paire de fonctions obtenir/définir qui permettent à l’utilisateur du contrôle d’accéder à la propriété à l’aide de la notation ci-dessus ou de la manière standard.

Comme pour les méthodes et les propriétés, les propriétés paramétrées ont également une limite au nombre de paramètres autorisés. Dans le cas des propriétés paramétrées, la limite est 15 paramètres (avec un paramètre réservé pour le stockage de la valeur de la propriété).

La procédure suivante ajoute une propriété paramétrable, appelée Array, qui est accessible sous la forme d’un tableau à deux dimensions d’entiers.

#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>Pour ajouter une propriété paramétrable à l’aide de l’Assistant Ajout de propriété

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **Ajouter** , puis sur **Ajouter une propriété**.

1. Dans la zone nom de la **propriété** , tapez `Array`.

1. Dans la zone **type de propriété** , sélectionnez **short**.

1. Pour type d' **implémentation** , cliquez sur **méthodes obtenir/définir**.

1. Dans les zones **obtenir une fonction** et définir une **fonction** , tapez des noms uniques pour vos fonctions obtenir et définir ou acceptez les noms par défaut.

9. Ajoutez un paramètre, appelé *Row* (type *short*), à l’aide des contrôles de **nom de paramètre** et de **type de paramètre** .

10. Ajoutez un deuxième paramètre appelé *Column* (type *short*).

11. Cliquez sur **Terminer**.

### <a name="changes-made-by-the-add-property-wizard"></a>Modifications apportées par l’Assistant Ajout de propriété

Lorsque vous ajoutez une propriété personnalisée, l’Assistant Ajout de propriété apporte des modifications à l’en-tête de la classe du contrôle (. H) et l’implémentation (. CPP).

Les lignes suivantes sont ajoutées à la classe de contrôle. Fichier H :

[!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]

Ce code déclare deux fonctions appelées `GetArray` et `SetArray` qui permettent à l’utilisateur de demander une ligne et une colonne spécifiques lors de l’accès à la propriété.

En outre, l’Assistant Ajout de propriété ajoute les lignes suivantes au mappage de dispatch de contrôle, situé dans l’implémentation de la classe de contrôle (. CPP) :

[!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]

Enfin, les implémentations des fonctions `GetArray` et `SetArray` sont ajoutées à la fin de. Fichier CPP. Dans la plupart des cas, vous allez modifier la fonction obtenir pour retourner la valeur de la propriété. La fonction Set contient généralement le code qui doit s’exécuter avant ou après la modification de la propriété.

Pour que cette propriété soit utile, vous pouvez déclarer une variable de membre de tableau à deux dimensions dans la classe de contrôle, de type **short**, pour stocker les valeurs de la propriété paramétrable. Vous pouvez ensuite modifier la fonction d’extraction pour retourner la valeur stockée au niveau de la ligne et de la colonne appropriées, comme indiqué par les paramètres, et modifier la fonction Set pour mettre à jour la valeur référencée par les paramètres de ligne et de colonne.

##  <a name="_core_handling_errors_in_your_activex_control"></a>Gestion des erreurs dans votre contrôle ActiveX

Si des conditions d’erreur se produisent dans le contrôle, vous devrez peut-être signaler l’erreur au conteneur de contrôle. Il existe deux méthodes pour signaler les erreurs, en fonction de la situation dans laquelle l’erreur se produit. Si l’erreur se produit dans la fonction d’extraction ou de définition d’une propriété, ou au sein de l’implémentation d’une méthode OLE Automation, le contrôle doit appeler [COleControl :: ThrowError](../mfc/reference/colecontrol-class.md#throwerror), qui signale à l’utilisateur du contrôle qu’une erreur s’est produite. Si l’erreur se produit à un autre moment, le contrôle doit appeler [COleControl :: FireError (](../mfc/reference/colecontrol-class.md#fireerror), qui déclenche un événement d’erreur stock.

Pour indiquer le type d’erreur qui s’est produit, le contrôle doit passer un code d’erreur à `ThrowError` ou `FireError`. Un code d’erreur est un code d’État OLE, qui a une valeur de 32 bits. Dans la mesure du possible, choisissez un code d’erreur dans l’ensemble de codes standard défini dans le OLECTL. Fichier d’en-tête H. Le tableau suivant récapitule ces codes.

### <a name="activex-control-error-codes"></a>Codes d’erreur du contrôle ActiveX

|Error|Description|
|-----------|-----------------|
|CTL_E_ILLEGALFUNCTIONCALL|Appel de fonction non conforme|
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
|CTL_E_BADFILENAME|Nom de fichier incorrect|
|CTL_E_TOOMANYFILES|Trop de fichiers|
|CTL_E_DEVICEUNAVAILABLE|Périphérique non disponible|
|CTL_E_PERMISSIONDENIED|Autorisation refusée|
|CTL_E_DISKNOTREADY|Disque non prêt|
|CTL_E_PATHFILEACCESSERROR|Erreur d’accès au chemin d’accès/fichier|
|CTL_E_PATHNOTFOUND|Chemin d'accès introuvable|
|CTL_E_INVALIDPATTERNSTRING|Chaîne de modèle non valide|
|CTL_E_INVALIDUSEOFNULL|Utilisation non valide de NULL|
|CTL_E_INVALIDFILEFORMAT|Format de fichier non valide|
|CTL_E_INVALIDPROPERTYVALUE|Valeur de propriété non valide|
|CTL_E_INVALIDPROPERTYARRAYINDEX|Index de tableau de propriétés non valide|
|CTL_E_SETNOTSUPPORTEDATRUNTIME|Set non pris en charge au moment de l’exécution|
|CTL_E_SETNOTSUPPORTED|Set non pris en charge (propriété en lecture seule)|
|CTL_E_NEEDPROPERTYARRAYINDEX|Index de tableau de propriétés requis|
|CTL_E_SETNOTPERMITTED|Set non autorisé|
|CTL_E_GETNOTSUPPORTEDATRUNTIME|Get non pris en charge au moment de l’exécution|
|CTL_E_GETNOTSUPPORTED|Get non pris en charge (propriété en écriture seule)|
|CTL_E_PROPERTYNOTFOUND|Propriété introuvable|
|CTL_E_INVALIDCLIPBOARDFORMAT|Format de presse-papiers non valide|
|CTL_E_INVALIDPICTURE|Image non valide|
|CTL_E_PRINTERERROR|Erreur d'imprimante|
|CTL_E_CANTSAVEFILETOTEMP|Impossible d’enregistrer le fichier dans TEMP|
|CTL_E_SEARCHTEXTNOTFOUND|Texte recherché introuvable|
|CTL_E_REPLACEMENTSTOOLONG|Remplacements trop longs|

Si nécessaire, utilisez la macro CUSTOM_CTL_SCODE pour définir un code d’erreur personnalisé pour une condition qui n’est pas couverte par l’un des codes standard. Le paramètre de cette macro doit être un entier compris entre 1000 et 32767 inclus. Exemple :

[!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]

Si vous créez un contrôle ActiveX pour remplacer un contrôle VBX existant, définissez les codes d’erreur de votre contrôle ActiveX avec les mêmes valeurs numériques que celles utilisées par le contrôle VBX pour garantir la compatibilité des codes d’erreur.

##  <a name="_core_handling_special_keys_in_your_control"></a>Gestion des clés spéciales dans le contrôle

Dans certains cas, vous pouvez être amené à gérer certaines combinaisons de touches d’une manière particulière. par exemple, insérez une nouvelle ligne lorsque vous appuyez sur la touche entrée dans un contrôle zone de texte multiligne ou que vous passez d’un groupe de contrôles d’édition à un autre lorsque l’ID de la touche directionnelle est enfoncé.

Si la classe de base de votre contrôle ActiveX est `COleControl`, vous pouvez remplacer [CWnd ::P retranslatemessage](../mfc/reference/cwnd-class.md#pretranslatemessage) pour gérer les messages avant que le conteneur ne les traite. Lors de l’utilisation de cette technique, retourne toujours **true** si vous gérez le message dans votre remplacement de `PreTranslateMessage`.

L’exemple de code suivant illustre une manière possible de gérer les messages liés aux touches directionnelles.

[!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]

Pour plus d’informations sur la gestion des interfaces clavier pour un contrôle ActiveX, consultez la documentation du kit de développement logiciel (SDK) ActiveX.

##  <a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a>Accès aux contrôles de boîte de dialogue qui sont invisibles au moment de l’exécution

Vous pouvez créer des contrôles de boîte de dialogue qui n’ont pas d’interface utilisateur et qui sont invisibles au moment de l’exécution. Si vous ajoutez un contrôle ActiveX invisible au moment de l’exécution à une boîte de dialogue et que vous utilisez [CWnd :: GetDlgItem](../mfc/reference/cwnd-class.md#getdlgitem) pour accéder au contrôle, le contrôle ne fonctionnera pas correctement. Au lieu de cela, vous devez utiliser l’une des techniques suivantes pour obtenir un objet qui représente le contrôle :

- À l’aide de l’Assistant Ajout de variable membre, sélectionnez **variable de contrôle** , puis sélectionnez l’ID du contrôle. Entrez un nom de variable membre et sélectionnez la classe wrapper du contrôle comme **type de contrôle**.

     -ou-

- Déclarez une variable locale et une sous-classe en tant qu’élément de boîte de dialogue. Insérez le code qui ressemble à ce qui suit (`CMyCtrl` est la classe wrapper, IDC_MYCTRL1 est l’ID du contrôle) :

   [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)
