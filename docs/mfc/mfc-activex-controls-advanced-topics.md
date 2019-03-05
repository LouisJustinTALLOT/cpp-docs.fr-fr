---
title: 'Contrôles ActiveX MFC : Rubriques avancées'
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
ms.openlocfilehash: df71e2e59763644bd4aefb5d3e3afa46f82f538a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277324"
---
# <a name="mfc-activex-controls-advanced-topics"></a>Contrôles ActiveX MFC : Rubriques avancées

Cet article couvre les rubriques avancées relatifs au développement de contrôles ActiveX. Elles incluent notamment :

- [À l’aide des Classes de base de données dans les contrôles ActiveX](#_core_using_database_classes_in_activex_controls)

- [Implémentation d’une propriété paramétrable](#_core_implementing_a_parameterized_property)

- [Gestion des erreurs dans votre contrôle ActiveX](#_core_handling_errors_in_your_activex_control)

- [Gestion de touches spéciales dans le contrôle](#_core_handling_special_keys_in_your_control)

- [L’accès aux contrôles de boîte de dialogue invisibles au moment de l’exécution](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

##  <a name="_core_using_database_classes_in_activex_controls"></a> À l’aide des Classes de base de données dans les contrôles ActiveX

Étant donné que les classes de contrôles ActiveX font partie de la bibliothèque de classes, vous pouvez appliquer les mêmes procédures et les règles d’utilisation des classes de base de données dans une application MFC standard pour le développement de contrôles ActiveX qui utilisent les classes de base de données MFC.

Pour obtenir une vue d’ensemble des classes de base de données MFC, consultez [les Classes de base de données MFC (ODBC et DAO)](../data/mfc-database-classes-odbc-and-dao.md). Cet article présente les deux classes ODBC MFC et les classes de DAO MFC et vous dirige vers plus d’informations sur une.

> [!NOTE]
>  Les Assistants et l’environnement Visual C++ ne prennent pas en charge les DAO (bien que les classes DAO sont incluses et vous pouvez toujours les utiliser). Microsoft recommande d’utiliser [modèles OLE DB](../data/oledb/ole-db-programming.md) ou [ODBC et MFC](../data/odbc/odbc-and-mfc.md) pour les nouveaux projets. Vous devez uniquement utiliser DAO à la gestion des applications existantes.

##  <a name="_core_implementing_a_parameterized_property"></a> Implémentation d’une propriété paramétrable

Une propriété paramétrée (parfois appelée un tableau de propriétés) est une méthode pour exposer une collection homogène de valeurs en tant qu’une seule propriété du contrôle. Par exemple, vous pouvez utiliser une propriété paramétrée pour exposer un tableau ou un dictionnaire en tant que propriété. En Visual Basic, une telle propriété est accessible à l’aide de la notation de tableau :

[!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]

Utilisez l’Assistant Ajout de propriété pour implémenter une propriété paramétrée. L’Assistant Ajout de propriété implémente la propriété en ajoutant une paire de fonctions Get/Set qui autorise l’utilisateur du contrôle pour accéder à la propriété à l’aide de la notation ci-dessus ou de la manière standard.

Similaire aux méthodes et propriétés, des propriétés paramétrables ont également une limite au nombre de paramètres autorisés. Dans le cas des propriétés paramétrables, la limite est de 15 paramètres (avec un paramètre réservé pour stocker la valeur de propriété).

La procédure suivante ajoute une propriété paramétrée, appelée tableau, qui est accessible sous forme de tableau à deux dimensions d’entiers.

#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>Pour ajouter une propriété paramétrable à l’aide de l’Assistant Ajout de propriété

1. Chargez votre projet de contrôle.

1. Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.

1. Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.

1. Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter une propriété**.

1. Dans le **nom de la propriété** , tapez `Array`.

1. Dans le **Type de propriété** boîte, sélectionnez **court**.

1. Pour **implémentation** Type, cliquez sur **méthodes Get/Set**.

1. Dans le **fonction Get** et **fonction Set** zones, tapez un nom unique pour vos fonctions Get et Set ou acceptez les noms par défaut.

9. Ajoutez un paramètre appelé *ligne* (type *court*), en utilisant le **nom du paramètre** et **Type de paramètre** contrôles.

10. Ajoutez un deuxième paramètre appelé *colonne* (type *court*).

11. Cliquez sur **Terminer**.

### <a name="changes-made-by-the-add-property-wizard"></a>Modifications apportées par l’Assistant Ajout de propriété

Lorsque vous ajoutez une propriété personnalisée, l’Assistant Ajout de propriété apporte des modifications à l’en-tête de classe de contrôle (. (H) et l’implémentation (. Fichiers CPP).

Les lignes suivantes sont ajoutées à la classe de contrôle. Fichier de H :

[!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]

Ce code déclare deux fonctions appelées `GetArray` et `SetArray` qui permettent à l’utilisateur de demander une ligne spécifique et une colonne lorsque vous accédez à la propriété.

En outre, l’Assistant Ajout de propriété ajoute les lignes suivantes à la table de dispatch de contrôle, située dans l’implémentation de classe de contrôle (. Fichier CPP) :

[!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]

Enfin, les implémentations de la `GetArray` et `SetArray` fonctions sont ajoutées à la fin de le. Fichier CPP. Dans la plupart des cas, vous allez modifier la fonction Get pour retourner la valeur de la propriété. La fonction Set contient généralement le code à exécuter avant ou après les modifications de propriété.

Pour cette propriété peut être utile, vous pouvez déclarer une variable de membre de tableau à deux dimensions dans la classe de contrôle, de type **court**, pour stocker les valeurs de la propriété paramétrée. Vous pouvez ensuite modifier la fonction Get pour retourner la valeur stockée à la ligne et colonne correctes, comme indiqué par les paramètres et modifiez la fonction de jeu pour mettre à jour la valeur référencée par les paramètres de ligne et de colonne.

##  <a name="_core_handling_errors_in_your_activex_control"></a> Gestion des erreurs dans votre contrôle ActiveX

En cas de conditions d’erreur dans le contrôle, vous devrez peut-être signaler l’erreur pour le conteneur de contrôle. Il existe deux méthodes pour signaler les erreurs, selon la situation dans laquelle l’erreur se produit. Si l’erreur se produit au sein d’une propriété Get ou Set, fonction, ou dans l’implémentation d’une méthode OLE Automation, le contrôle doit appeler [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror), les signaux à l’utilisateur du contrôle qui a une erreur s’est produite. Si l’erreur se produit à tout moment, le contrôle doit appeler [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror), ce qui déclenche un événement d’erreur stock.

Pour indiquer le type d’erreur qui s’est produite, le contrôle doit passer un code d’erreur à `ThrowError` ou `FireError`. Un code d’erreur est un code d’état OLE, qui a une valeur 32 bits. Dans la mesure du possible, choisissez un code d’erreur à partir de l’ensemble standard de codes définis dans le OLECTL. Fichier d’en-tête H. Le tableau suivant récapitule ces codes.

### <a name="activex-control-error-codes"></a>Codes d’erreur de contrôle ActiveX

|Error|Description|
|-----------|-----------------|
|CTL_E_ILLEGALFUNCTIONCALL|Appel de fonction non conforme|
|CTL_E_OVERFLOW|Dépassement|
|CTL_E_OUTOFMEMORY|Mémoire insuffisante|
|CTL_E_DIVISIONBYZERO|Division par zéro|
|CTL_E_OUTOFSTRINGSPACE|Espace de chaîne|
|CTL_E_OUTOFSTACKSPACE|Espace de pile|
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
|CTL_E_PATHFILEACCESSERROR|Erreur dans le chemin d’accès|
|CTL_E_PATHNOTFOUND|Chemin d'accès introuvable|
|CTL_E_INVALIDPATTERNSTRING|Chaîne de modèle non valide|
|CTL_E_INVALIDUSEOFNULL|Utilisation incorrecte de NULL|
|CTL_E_INVALIDFILEFORMAT|Format de fichier non valide|
|CTL_E_INVALIDPROPERTYVALUE|Valeur de propriété non valide|
|CTL_E_INVALIDPROPERTYARRAYINDEX|Index de tableau de propriété non valide|
|CTL_E_SETNOTSUPPORTEDATRUNTIME|Set non pris en charge au moment de l’exécution|
|CTL_E_SETNOTSUPPORTED|Set non pris en charge (propriété en lecture seule)|
|CTL_E_NEEDPROPERTYARRAYINDEX|Index de tableau de propriétés requis|
|CTL_E_SETNOTPERMITTED|Set non autorisé|
|CTL_E_GETNOTSUPPORTEDATRUNTIME|Get non pris en charge au moment de l’exécution|
|CTL_E_GETNOTSUPPORTED|Get non pris en charge (propriété en écriture seule)|
|CTL_E_PROPERTYNOTFOUND|Propriété introuvable|
|CTL_E_INVALIDCLIPBOARDFORMAT|Format de Presse-papiers non valide|
|CTL_E_INVALIDPICTURE|Image non valide|
|CTL_E_PRINTERERROR|Erreur d'imprimante|
|CTL_E_CANTSAVEFILETOTEMP|Impossible d’enregistrer le fichier dans TEMP|
|CTL_E_SEARCHTEXTNOTFOUND|Texte recherché introuvable|
|CTL_E_REPLACEMENTSTOOLONG|Remplacements trop longs|

Si nécessaire, utilisez la macro CUSTOM_CTL_SCODE pour définir un code d’erreur personnalisé pour une condition qui n’est pas couverte par un des codes standard. Le paramètre de cette macro doit être un entier compris entre 1000 et 32767, inclusif. Exemple :

[!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]

Si vous créez un contrôle ActiveX pour remplacer un contrôle VBX existant, définissez les codes d’erreur de votre contrôle ActiveX avec les mêmes valeurs numériques, que le contrôle VBX utilise pour s’assurer que les codes d’erreur sont compatibles.

##  <a name="_core_handling_special_keys_in_your_control"></a> Gestion de touches spéciales dans le contrôle

Dans certains cas, vous souhaiterez gérer certaines combinaisons de touches d’une façon particulière ; par exemple, insérer une nouvelle ligne lorsque la touche entrée est enfoncée dans un texte multiligne contrôle de zone ou passer à un groupe de modification contrôle quand un directionnelles enfoncé des ID de la clé.

Si la classe de base de votre contrôle ActiveX est `COleControl`, vous pouvez remplacer [CWnd::PreTranslateMessage](../mfc/reference/cwnd-class.md#pretranslatemessage) à traiter les messages avant que le conteneur les traite. Lorsque vous utilisez cette technique, retournent toujours **TRUE** si vous gérez le message dans la substitution de `PreTranslateMessage`.

L’exemple de code suivant montre une façon possible de traiter les messages relatifs aux touches de direction.

[!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]

Pour plus d’informations sur la gestion des interfaces de clavier pour un contrôle ActiveX, consultez la documentation du SDK d’ActiveX.

##  <a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a> L’accès aux contrôles de boîte de dialogue invisibles au moment de l’exécution

Vous pouvez créer des contrôles de boîte de dialogue qui n’ont aucune interface utilisateur et invisibles au moment de l’exécution. Si vous ajoutez un invisible au moment de l’exécution contrôle ActiveX à une boîte de dialogue et l’utiliser [CWnd::GetDlgItem](../mfc/reference/cwnd-class.md#getdlgitem) pour le contrôle d’accès, le contrôle ne fonctionnera pas correctement. Au lieu de cela, vous devez utiliser une des techniques suivantes pour obtenir un objet qui représente le contrôle :

- À l’aide de l’Assistant Ajout de membre Variable, sélectionnez **contrôle Variable** , puis ID. du contrôle Entrez un nom de variable de membre et sélectionnez la classe du contrôle wrapper en tant que le **Type de contrôle**.

     ou

- Déclarez une variable locale et une sous-classe en tant que l’élément de boîte de dialogue. Insérer du code qui ressemble à celui-ci (`CMyCtrl` est la classe wrapper, IDC_MYCTRL1 est l’ID du contrôle) :

   [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)
