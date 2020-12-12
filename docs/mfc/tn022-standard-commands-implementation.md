---
description: 'En savoir plus sur : TN022 : implémentation des commandes standard'
title: 'TN022 : implémentation de commandes standard'
ms.date: 11/04/2016
f1_keywords:
- vc.commands
helpviewer_keywords:
- ID_PREV_PANE command [MFC]
- ID_APP_EXIT command [MFC]
- ID_NEXT_PANE command [MFC]
- ID_INDICATOR_REC command [MFC]
- ID_WINDOW_SPLIT command [MFC]
- ID_FILE_PRINT_PREVIEW command [MFC]
- ID_WINDOW_CASCADE command [MFC]
- ID_FILE_CLOSE command [MFC]
- ID_FILE_SAVE_COPY_AS command [MFC]
- ID_WINDOW_ARRANGE command [MFC]
- ID_EDIT_FIND command [MFC]
- ID_FILE_OPEN command [MFC]
- ID_FILE_PAGE_SETUP command [MFC]
- ID_OLE_VERB_FIRST command [MFC]
- ID_EDIT_UNDO command [MFC]
- ID_EDIT_CLEAR command [MFC]
- ID_INDICATOR_CAPS command [MFC]
- ID_HELP_INDEX command [MFC]
- commands [MFC], standard
- ID_FILE_PRINT_SETUP command [MFC]
- ID_DEFAULT_HELP command [MFC]
- ID_INDICATOR_SCRL command [MFC]
- ID_FILE_PRINT command [MFC]
- ID_INDICATOR_OVR command [MFC]
- ID_INDICATOR_KANA command [MFC]
- ID_EDIT_COPY command [MFC]
- ID_EDIT_REDO command [MFC]
- ID_EDIT_PASTE command [MFC]
- ID_OLE_INSERT_NEW command [MFC]
- ID_OLE_EDIT_LINKS command [MFC]
- ID_EDIT_PASTE_SPECIAL command [MFC]
- ID_INDICATOR_EXT command [MFC]
- ID_HELP_USING command [MFC]
- standard commands
- ID_VIEW_STATUS_BAR command [MFC]
- ID_FILE_SAVE_AS command [MFC]
- ID_EDIT_CLEAR_ALL command [MFC]
- ID_WINDOW_NEW command [MFC]
- ID_CONTEXT_HELP command [MFC]
- ID_EDIT_REPLACE command [MFC]
- ID_WINDOW_TILE_HORZ command [MFC]
- ID_APP_ABOUT command [MFC]
- TN022
- ID_VIEW_TOOLBAR command [MFC]
- ID_HELP command [MFC]
- ID_WINDOW_TILE_VERT command [MFC]
- ID_EDIT_CUT command [MFC]
- ID_FILE_UPDATE command [MFC]
- ID_EDIT_REPEAT command [MFC]
- ID_FILE_SAVE command [MFC]
- ID_EDIT_PASTE_LINK command [MFC]
- ID_EDIT_SELECT_ALL command [MFC]
- ID_FILE_NEW command [MFC]
- ID_INDICATOR_NUM command
ms.assetid: a7883b46-23f7-4870-ac3a-804aed9258b5
ms.openlocfilehash: 7c8540dcf0e41e5f6d5f00a4f22568c4df0fcdbe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215805"
---
# <a name="tn022-standard-commands-implementation"></a>TN022 : implémentation de commandes standard

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit les implémentations de commande standard fournies par MFC 2,0. Lisez la [note technique 21](../mfc/tn021-command-and-message-routing.md) en premier car elle décrit les mécanismes utilisés pour implémenter la plupart des commandes standard.

Cette description suppose la connaissance des architectures MFC, des API et des pratiques de programmation courantes. Les API documentées et non documentées « implémentation uniquement » sont décrites. Ce n’est pas un endroit où vous pouvez commencer à vous familiariser avec les fonctionnalités de ou comment programmer dans MFC. Reportez-vous à Visual C++ pour plus d’informations générales et pour plus d’informations sur les API documentées.

## <a name="the-problem"></a>Le problème

MFC définit un grand nombre d’ID de commande standard dans le fichier d’en-tête AFXRES. H. La prise en charge de l’infrastructure pour ces commandes varie. La compréhension de l’emplacement et de la façon dont les classes de Framework gèrent ces commandes vous montre non seulement comment le Framework fonctionne en interne, mais fournit des informations utiles sur la personnalisation des implémentations standard et vous apprend quelques techniques d’implémentation de vos propres gestionnaires de commandes.

## <a name="contents-of-this-technical-note"></a>Contenu de cette note technique

Chaque ID de commande est décrit dans deux sections :

- Titre : le nom symbolique de l’ID de commande (par exemple, ID_FILE_SAVE) suivi du rôle de la commande (par exemple, « enregistre le document actif »), séparé par un signe deux-points.

- Un ou plusieurs paragraphes décrivant les classes qui implémentent la commande et ce que fait l’implémentation par défaut

La plupart des implémentations de commandes par défaut sont précâblées dans la table des messages de la classe de base de l’infrastructure. Certaines implémentations de commande nécessitent un câblage explicite dans votre classe dérivée. Celles-ci sont décrites dans « Remarque ». Si vous avez choisi les options appropriées dans AppWizard, ces gestionnaires par défaut sont connectés pour vous dans l’application squelette générée.

## <a name="naming-convention"></a>Conventions d’affectation de noms

Les commandes standard suivent une convention d’affectation de noms simple que nous vous recommandons d’utiliser si possible. La plupart des commandes standard se trouvent dans emplacements standard dans la barre de menus d’une application. Le nom symbolique de la commande commence par « ID_ » suivi du nom du menu contextuel standard, suivi du nom de l’élément de menu. Le nom symbolique est en majuscules avec des césures de soulignement. Pour les commandes qui n’ont pas de noms d’élément de menu standard, un nom de commande logique est défini à partir de « ID_ » (par exemple, ID_NEXT_PANE).

Nous utilisons le préfixe « ID_ » pour indiquer les commandes qui sont conçues pour être liées à des éléments de menu, des boutons de barre d’outils ou d’autres objets d’interface utilisateur de commande. Les gestionnaires de commandes gérant les commandes « ID_ » doivent utiliser les mécanismes de ON_COMMAND et de ON_UPDATE_COMMAND_UI de l’architecture de commande MFC.

Nous vous recommandons d’utiliser le préfixe « IDM_ » standard pour les éléments de menu qui ne suivent pas l’architecture de commande et qui nécessitent du code propre au menu pour les activer et les désactiver. Bien entendu, le nombre de commandes spécifiques au menu doit être faible, car l’architecture de la commande MFC rend non seulement les gestionnaires de commandes plus puissants (puisqu’ils fonctionnent avec les barres d’outils), mais rend le code du gestionnaire de commandes réutilisable.

## <a name="id-ranges"></a>Plages d’ID

Reportez-vous à la [note technique 20](../mfc/tn020-id-naming-and-numbering-conventions.md) pour plus d’informations sur l’utilisation des plages d’ID dans MFC.

Les commandes standard MFC sont comprises dans la plage 0xE000 à 0xEFFF. Ne vous fiez pas aux valeurs spécifiques de ces ID, car elles sont susceptibles d’être modifiées dans les versions ultérieures de la bibliothèque.

Votre application doit définir ses commandes dans la plage 0x8000 sur 0xDFFF.

## <a name="standard-command-ids"></a>ID de commande standard

Pour chaque ID de commande, une chaîne de message standard de ligne de message est disponible dans les invites de fichier. Release. L’ID de chaîne de cette invite de menu doit être identique à celui de l’ID de commande.

- ID_FILE_NEW crée un document nouveau ou vide.

    > [!NOTE]
    >  Vous devez le connecter à la `CWinApp` table des messages de votre classe dérivée de pour activer cette fonctionnalité.

   `CWinApp::OnFileNew` implémente cette commande différemment en fonction du nombre de modèles de document dans l’application. S’il n’y en a qu’un `CDocTemplate` , `CWinApp::OnFileNew` crée un nouveau document de ce type, ainsi que la classe de frame et de vue appropriée.

   S’il en existe plus d’un `CDocTemplate` , `CWinApp::OnFileNew` invite l’utilisateur à entrer une boîte de dialogue (AFX_IDD_NEWTYPEDLG) pour lui permettre de sélectionner le type de document à utiliser. Le sélectionné `CDocTemplate` est utilisé pour créer le document.

   Une personnalisation courante de ID_FILE_NEW consiste à fournir un choix de types de documents différent et plus graphique. Dans ce cas, vous pouvez implémenter votre propre `CMyApp::OnFileNew` et le placer dans votre table des messages au lieu de `CWinApp::OnFileNew` . Il n’est pas nécessaire d’appeler l’implémentation de la classe de base.

   Une autre personnalisation courante de ID_FILE_NEW consiste à fournir une commande distincte pour créer un document de chaque type. Dans ce cas, vous devez définir de nouveaux ID de commande, par exemple ID_FILE_NEW_CHART et ID_FILE_NEW_SHEET.

- ID_FILE_OPEN ouvre un document existant.

    > [!NOTE]
    >  Vous devez le connecter à la `CWinApp` table des messages de votre classe dérivée de pour activer cette fonctionnalité.

   `CWinApp::OnFileOpen` a une implémentation très simple de l’appel de `CWinApp::DoPromptFileName` suivi de `CWinApp::OpenDocumentFile` avec le nom de fichier ou de chemin d’accès du fichier à ouvrir. La `CWinApp` routine `DoPromptFileName` d’implémentation affiche la boîte de dialogue FileOpen standard et la remplit avec les extensions de fichier obtenues à partir des modèles de document actuels.

   Une personnalisation courante de ID_FILE_OPEN consiste à personnaliser la boîte de dialogue FileOpen ou à ajouter des filtres de fichiers supplémentaires. La méthode recommandée pour personnaliser cela consiste à remplacer l’implémentation par défaut par votre propre boîte de dialogue FileOpen et à appeler `CWinApp::OpenDocumentFile` avec le nom de fichier ou de chemin d’accès du document. Il n’est pas nécessaire d’appeler la classe de base.

- ID_FILE_CLOSE ferme le document actuellement ouvert.

   `CDocument::OnFileClose` appelle `CDocument::SaveModified` pour inviter l’utilisateur à enregistrer le document s’il a été modifié, puis appelle `OnCloseDocument` . Toute la logique de fermeture, y compris la destruction du document, s’effectue dans la `OnCloseDocument` routine.

    > [!NOTE]
    >  ID_FILE_CLOSE agit différemment d’un message WM_CLOSE ou d’une commande système SC_CLOSE envoyée à la fenêtre frame de documents. La fermeture d’une fenêtre ferme le document uniquement s’il s’agit de la dernière fenêtre frame qui affiche le document. La fermeture du document avec ID_FILE_CLOSE ne ferme pas uniquement le document, mais ferme toutes les fenêtres frame qui affichent le document.

- ID_FILE_SAVE enregistre le document actif.

   L’implémentation utilise une routine d’assistance `CDocument::DoSave` qui est utilisée à la fois pour `OnFileSave` et `OnFileSaveAs` . Si vous enregistrez un document qui n’a pas encore été enregistré (autrement dit, s’il n’a pas de nom de chemin d’accès, comme dans le cas de FileNew) ou qui a été lu à partir d’un document en lecture seule, la `OnFileSave` logique agira comme la commande ID_FILE_SAVE_AS et demandera à l’utilisateur de fournir un nouveau nom de fichier. Le processus d’ouverture du fichier et d’enregistrement est effectué via la fonction virtuelle `OnSaveDocument` .

   Il existe deux raisons courantes de personnaliser ID_FILE_SAVE. Pour les documents qui ne sont pas enregistrés, supprimez simplement les ID_FILE_SAVE les éléments de menu et les boutons de la barre d’outils de votre interface utilisateur. Assurez-vous également que vous n’avez jamais modifié votre document (autrement dit, ne jamais appeler `CDocument::SetModifiedFlag` ) et que le Framework n’entraînera jamais l’enregistrement du document. Pour les documents qui s’enregistrent à un autre endroit que sur un fichier disque, définissez une nouvelle commande pour cette opération.

   Dans le cas d’un `COleServerDoc` , ID_FILE_SAVE est utilisé à la fois pour l’enregistrement des fichiers (pour les documents normaux) et pour la mise à jour des fichiers (pour les documents incorporés).

   Si vos données de document sont stockées dans des fichiers de disque individuels, mais que vous ne souhaitez pas utiliser l’implémentation de sérialisation par défaut `CDocument` , vous devez substituer `CDocument::OnSaveDocument` au lieu de `OnFileSave` .

- ID_FILE_SAVE_AS enregistre le document actif sous un nom de fichier différent.

   L' `CDocument::OnFileSaveAs` implémentation utilise la même `CDocument::DoSave` routine d’assistance que `OnFileSave` . La `OnFileSaveAs` commande est gérée de la même façon que ID_FILE_SAVE si les documents ne comportaient pas de nom de fichier avant l’enregistrement. `COleServerDoc::OnFileSaveAs` implémente la logique pour enregistrer un fichier de données de document normal ou pour enregistrer un document serveur qui représente un objet OLE incorporé dans une autre application sous la forme d’un fichier distinct.

   Si vous personnalisez la logique d’ID_FILE_SAVE, vous souhaiterez probablement personnaliser ID_FILE_SAVE_AS de la même manière ou l’opération « Enregistrer sous » peut ne pas s’appliquer à votre document. Vous pouvez supprimer l’élément de menu de la barre de menus si ce n’est pas nécessaire.

- ID_FILE_SAVE_COPY_AS enregistre une copie du document actif sous un nouveau nom.

   L' `COleServerDoc::OnFileSaveCopyAs` implémentation est très similaire à `CDocument::OnFileSaveAs` , à ceci près que l’objet document n’est pas « attaché » au fichier sous-jacent après l’enregistrement. Autrement dit, si le document en mémoire a été « modifié » avant l’enregistrement, il est toujours « modifié ». En outre, cette commande n’a aucun effet sur le nom ou le titre du chemin d’accès stocké dans le document.

- ID_FILE_UPDATE notifie le conteneur d’enregistrer un document incorporé.

   L' `COleServerDoc::OnUpdateDocument` implémentation indique simplement au conteneur que l’incorporation doit être enregistrée. Le conteneur appelle ensuite les API OLE appropriées pour enregistrer l’objet incorporé.

- ID_FILE_PAGE_SETUP appelle une boîte de dialogue de mise en page/mise en page spécifique à l’application.

   Actuellement, il n’existe pas de norme pour cette boîte de dialogue, et l’infrastructure n’a pas d’implémentation par défaut de cette commande.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cet ID de commande.

- ID_FILE_PRINT_SETUP appeler la boîte de dialogue Configuration de l’impression standard.

    > [!NOTE]
    >  Vous devez le connecter à la `CWinApp` table des messages de votre classe dérivée de pour activer cette fonctionnalité.

   Cette commande appelle la boîte de dialogue de configuration de l’impression standard qui permet à l’utilisateur de personnaliser l’imprimante et les paramètres d’impression pour au moins ce document ou tous les documents de cette application. Vous devez utiliser le panneau de configuration pour modifier les paramètres par défaut de l’imprimante pour l’ensemble du système.

   `CWinApp::OnFilePrintSetup` a une implémentation très simple qui crée un `CPrintDialog` objet et appelle la `CWinApp::DoPrintDialog` fonction d’implémentation. Cela définit la configuration de l’imprimante par défaut de l’application.

   La personnalisation de cette commande est souvent nécessaire pour autoriser les paramètres d’imprimante par document, qui doivent être stockés avec le document lors de son enregistrement. Pour ce faire, vous devez ajouter un gestionnaire de table des messages dans votre `CDocument` classe qui crée un `CPrintDialog` objet, l’initialise avec les attributs d’imprimante appropriés (généralement *hDevMode* et *hDevNames*), appeler le `CPrintDialog::DoModal` et enregistrer les paramètres d’imprimante modifiés. Pour une implémentation fiable, vous devez examiner l’implémentation de `CWinApp::DoPrintDialog` pour la détection des erreurs et le traitement des `CWinApp::UpdatePrinterSelection` valeurs par défaut sensibles et le suivi des modifications apportées à l’imprimante au niveau du système.

- ID_FILE_PRINT l’impression standard du document actif

    > [!NOTE]
    >  Vous devez le connecter à la `CView` table des messages de votre classe dérivée de pour activer cette fonctionnalité.

   Cette commande imprime le document actif, ou plus correctement, démarre le processus d’impression, ce qui implique l’appel de la boîte de dialogue d’impression standard et l’exécution du moteur d’impression.

   `CView::OnFilePrint` implémente cette commande et la boucle d’impression principale. Il appelle l' `CView::OnPreparePrinting` invite de commandes virtuelle à l’utilisateur avec la boîte de dialogue Imprimer. Il prépare ensuite le DC de sortie pour accéder à l’imprimante, affiche la boîte de dialogue de progression de l’impression (AFX_IDD_PRINTDLG) et envoie l' `StartDoc` échappement à l’imprimante. `CView::OnFilePrint` contient également la boucle d’impression orientée page principale. Pour chaque page, il appelle le virtuel `CView::OnPrepareDC` suivi d’une `StartPage` séquence d’échappement et appelle le virtuel `CView::OnPrint` pour cette page. Une fois l’opération terminée, la `CView::OnEndPrinting` méthode virtuelle est appelée et la boîte de dialogue de progression de l’impression est fermée.

   L’architecture d’impression MFC est conçue pour s’associer à de nombreuses façons différentes pour l’impression et l’aperçu avant impression. Normalement, vous trouverez les différentes `CView` fonctions substituables appropriées pour toutes les tâches d’impression orientée page. Dans le cas d’une application qui utilise l’imprimante pour une sortie non orientée page, si vous avez besoin de remplacer l’implémentation ID_FILE_PRINT.

- ID_FILE_PRINT_PREVIEW passer en mode aperçu avant impression pour le document actif.

    > [!NOTE]
    >  Vous devez le connecter à la `CView` table des messages de votre classe dérivée de pour activer cette fonctionnalité.

   `CView::OnFilePrintPreview` démarre le mode aperçu avant impression en appelant la fonction d’assistance documentée `CView::DoPrintPreview` . `CView::DoPrintPreview` est le moteur principal de la boucle d’aperçu avant impression, tout comme `OnFilePrint` le moteur principal de la boucle d’impression.

   L’opération d’aperçu avant impression peut être personnalisée de diverses façons en passant des paramètres différents à `DoPrintPreview` . Reportez-vous à la [note technique 30](../mfc/tn030-customizing-printing-and-print-preview.md), qui décrit certains détails de l’aperçu avant impression et comment le personnaliser.

- ID_FILE_MRU_FILE1... FILE16 une plage d’ID de commandes pour la **liste** des fichiers récents.

   `CWinApp::OnUpdateRecentFileMenu` est un gestionnaire d’interface utilisateur de commande de mise à jour qui est l’une des utilisations plus avancées du mécanisme de ON_UPDATE_COMMAND_UI. Dans votre ressource de menu, vous ne devez définir qu’un seul élément de menu avec l’ID ID_FILE_MRU_FILE1. Cet élément de menu reste initialement désactivé.

   À mesure que la liste MRU augmente, davantage d’éléments de menu sont ajoutés à la liste. La `CWinApp` valeur par défaut de l’implémentation standard est la limite standard des quatre derniers fichiers utilisés. Vous pouvez modifier la valeur par défaut en appelant `CWinApp::LoadStdProfileSettings` avec une valeur plus grande ou plus petite. La liste MRU est stockée dans l’application. Fichier INI. La liste est chargée dans la fonction de votre application `InitInstance` si vous appelez `LoadStdProfileSettings` , et si elle est enregistrée au moment de la fermeture de votre application. Le gestionnaire d’interface utilisateur de la commande de mise à jour MRU convertit également les chemins absolus en chemins relatifs pour l’affichage dans le menu fichier.

   `CWinApp::OnOpenRecentFile` est le gestionnaire de ON_COMMAND qui exécute la commande réelle. Il obtient simplement le nom de fichier à partir de la liste MRU et appelle `CWinApp::OpenDocumentFile` , ce qui fait tout le travail d’ouvrir le fichier et de mettre à jour la liste des fichiers récents.

   La personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_EDIT_CLEAR efface la sélection actuelle

   Il n’existe actuellement aucune implémentation standard pour cette commande. Vous devez implémenter cela pour chaque `CView` classe dérivée de.

   `CEditView` fournit une implémentation de cette commande à l’aide de `CEdit::Clear` . La commande est désactivée s’il n’y a aucune sélection actuelle.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cet ID de commande.

- ID_EDIT_CLEAR_ALL efface la totalité du document.

   Il n’existe actuellement aucune implémentation standard pour cette commande. Vous devez implémenter cela pour chaque `CView` classe dérivée de.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cet ID de commande. Pour obtenir un exemple d’implémentation, consultez le didacticiel MFC exemple [Scribble](../overview/visual-cpp-samples.md) .

- ID_EDIT_COPY copie la sélection actuelle dans le presse-papiers.

   Il n’existe actuellement aucune implémentation standard pour cette commande. Vous devez implémenter cela pour chaque `CView` classe dérivée de.

   `CEditView` fournit une implémentation de cette commande, qui copie le texte actuellement sélectionné dans le presse-papiers en tant que CF_TEXT à l’aide de `CEdit::Copy` . La commande est désactivée s’il n’y a aucune sélection actuelle.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cet ID de commande.

- ID_EDIT_CUT Coupe la sélection actuelle dans le presse-papiers.

   Il n’existe actuellement aucune implémentation standard pour cette commande. Vous devez implémenter cela pour chaque `CView` classe dérivée de.

   `CEditView` fournit une implémentation de cette commande, qui coupe le texte actuellement sélectionné dans le presse-papiers en tant que CF_TEXT à l’aide de `CEdit::Cut` . La commande est désactivée s’il n’y a aucune sélection actuelle.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cet ID de commande.

- ID_EDIT_FIND commence l’opération de recherche, affiche la boîte de dialogue Rechercher non modale.

   Il n’existe actuellement aucune implémentation standard pour cette commande. Vous devez implémenter cela pour chaque `CView` classe dérivée de.

   `CEditView` fournit une implémentation de cette commande, qui appelle la fonction d’assistance d’implémentation `OnEditFindReplace` pour utiliser et stocker les paramètres Find/Replace précédents dans les variables d’implémentation privées. La `CFindReplaceDialog` classe est utilisée pour gérer la boîte de dialogue non modale pour inviter l’utilisateur.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cet ID de commande.

- ID_EDIT_PASTE insère le contenu actuel du presse-papiers.

   Il n’existe actuellement aucune implémentation standard pour cette commande. Vous devez implémenter cela pour chaque `CView` classe dérivée de.

   `CEditView` fournit une implémentation de cette commande, qui copie les données du presse-papiers actuelles en remplaçant le texte sélectionné à l’aide de `CEdit::Paste` . La commande est désactivée s’il n’existe aucun **CF_TEXT** dans le presse-papiers.

   `COleClientDoc` fournit simplement un gestionnaire d’interface utilisateur de commande de mise à jour pour cette commande. Si le presse-papiers ne contient pas d’élément/objet OLE incorporable, la commande est désactivée. Vous êtes chargé d’écrire le gestionnaire pour la commande réelle afin d’effectuer le collage réel. Si votre application OLE peut également coller d’autres formats, vous devez fournir votre propre gestionnaire d’interface utilisateur de commande de mise à jour dans votre vue ou document (autrement dit, quelque part `COleClientDoc` dans le routage cible de la commande).

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cet ID de commande.

   Pour remplacer l’implémentation OLE standard, utilisez `COleClientItem::CanPaste` .

- ID_EDIT_PASTE_LINK insère un lien à partir du contenu actuel du presse-papiers.

   Il n’existe actuellement aucune implémentation standard pour cette commande. Vous devez implémenter cela pour chaque `CView` classe dérivée de.

   `COleDocument` fournit simplement un gestionnaire d’interface utilisateur de commande de mise à jour pour cette commande. Si le presse-papiers ne contient pas d’élément/objet OLE qui peut être lié, la commande est désactivée. Vous êtes chargé d’écrire le gestionnaire pour la commande réelle afin d’effectuer le collage réel. Si votre application OLE peut également coller d’autres formats, vous devez fournir votre propre gestionnaire d’interface utilisateur de commande de mise à jour dans votre vue ou document (autrement dit, quelque part `COleDocument` dans le routage cible de la commande).

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cet ID de commande.

   Pour remplacer l’implémentation OLE standard, utilisez `COleClientItem::CanPasteLink` .

- ID_EDIT_PASTE_SPECIAL insère le contenu actuel du presse-papiers avec les options.

   Il n’existe actuellement aucune implémentation standard pour cette commande. Vous devez implémenter cela pour chaque `CView` classe dérivée de. MFC ne fournit pas cette boîte de dialogue.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cet ID de commande.

- ID_EDIT_REPEAT répète la dernière opération.

   Il n’existe actuellement aucune implémentation standard pour cette commande. Vous devez implémenter cela pour chaque `CView` classe dérivée de.

   `CEditView` fournit une implémentation de cette commande pour répéter la dernière opération de recherche. Les variables d’implémentation privées de la dernière recherche sont utilisées. La commande est désactivée si aucune tentative de recherche n’est possible.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cet ID de commande.

- ID_EDIT_REPLACE commence l’opération de remplacement, affiche la boîte de dialogue de remplacement non modal.

   Il n’existe actuellement aucune implémentation standard pour cette commande. Vous devez implémenter cela pour chaque `CView` classe dérivée de.

   `CEditView` fournit une implémentation de cette commande, qui appelle la fonction d’assistance d’implémentation `OnEditFindReplace` pour utiliser et stocker les paramètres Find/Replace précédents dans les variables d’implémentation privées. La `CFindReplaceDialog` classe est utilisée pour gérer la boîte de dialogue non modale qui invite l’utilisateur.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cet ID de commande.

- ID_EDIT_SELECT_ALL sélectionne tout le document.

   Il n’existe actuellement aucune implémentation standard pour cette commande. Vous devez implémenter cela pour chaque `CView` classe dérivée de.

   `CEditView` fournit une implémentation de cette commande, qui sélectionne tout le texte dans le document. La commande est désactivée s’il n’y a pas de texte à sélectionner.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cet ID de commande.

- ID_EDIT_UNDO annule la dernière opération.

   Il n’existe actuellement aucune implémentation standard pour cette commande. Vous devez implémenter cela pour chaque `CView` classe dérivée de.

   `CEditView` fournit une implémentation de cette commande, à l’aide de `CEdit::Undo` . La commande est désactivée si `CEdit::CanUndo` retourne false.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cet ID de commande.

- ID_EDIT_REDO refait la dernière opération.

   Il n’existe actuellement aucune implémentation standard pour cette commande. Vous devez implémenter cela pour chaque `CView` classe dérivée de.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cet ID de commande.

- ID_WINDOW_NEW ouvre une autre fenêtre sur le document actif.

   `CMDIFrameWnd::OnWindowNew` implémente cette fonctionnalité puissante en utilisant le modèle de document du document actif pour créer un autre Frame contenant une autre vue du document actif.

   À l’instar des commandes de menu de la fenêtre MDI (multiple document interface), la commande est désactivée s’il n’existe aucune fenêtre enfant MDI active.

   La personnalisation de ce gestionnaire de commandes n’est pas recommandée. Si vous souhaitez fournir une commande qui crée des vues ou des fenêtres Frame supplémentaires, il est probablement préférable d’inventer votre propre commande. Vous pouvez cloner le code à partir de `CMDIFrameWnd::OnWindowNew` et le modifier dans le frame et les classes d’affichage spécifiques de votre choix.

- ID_WINDOW_ARRANGE organise les icônes en bas d’une fenêtre MDI.

   `CMDIFrameWnd` implémente cette commande MDI standard dans une fonction d’assistance d’implémentation `OnMDIWindowCmd` . Cette application d’assistance mappe les ID de commande aux messages Windows MDI et peut donc partager un grand nombre de code.

   Comme la plupart des commandes de menu de fenêtre MDI, la commande est désactivée s’il n’existe aucune fenêtre enfant MDI active.

   La personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_WINDOW_CASCADE les fenêtres en cascade afin qu’elles se chevauchent.

   `CMDIFrameWnd` implémente cette commande MDI standard dans une fonction d’assistance d’implémentation `OnMDIWindowCmd` . Cette application d’assistance mappe les ID de commande aux messages Windows MDI et peut donc partager un grand nombre de code.

   Comme la plupart des commandes de menu de fenêtre MDI, la commande est désactivée s’il n’existe aucune fenêtre enfant MDI active.

   La personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_WINDOW_TILE_HORZ les fenêtres vignettes horizontalement.

   Cette commande est implémentée de `CMDIFrameWnd` la même façon que ID_WINDOW_CASCADE, à l’exception d’un autre message Windows MDI qui est utilisé pour l’opération.

   Vous devez choisir l’orientation de mosaïque par défaut pour votre application. Pour ce faire, vous pouvez modifier l’ID de l’élément de menu « vignette » de la fenêtre en ID_WINDOW_TILE_HORZ ou ID_WINDOW_TILE_VERT.

- ID_WINDOW_TILE_VERT les mosaïques verticalement.

   Cette commande est implémentée de `CMDIFrameWnd` la même façon que ID_WINDOW_CASCADE, à l’exception d’un autre message Windows MDI qui est utilisé pour l’opération.

   Vous devez choisir l’orientation de mosaïque par défaut pour votre application. Pour ce faire, vous pouvez modifier l’ID de l’élément de menu « vignette » de la fenêtre en ID_WINDOW_TILE_HORZ ou ID_WINDOW_TILE_VERT.

- ID_WINDOW_SPLIT interface clavier à fractionner.

   `CView` gère cette commande pour l' `CSplitterWnd` implémentation de. Si la vue fait partie d’une fenêtre fractionnée, cette commande délègue à la fonction d’implémentation `CSplitterWnd::DoKeyboardSplit` . Cette opération place le séparateur dans un mode qui permet aux utilisateurs du clavier de fractionner ou de défractionner une fenêtre fractionnée.

   Cette commande est désactivée si la vue ne se trouve pas dans un séparateur.

   La personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_APP_ABOUT appelle la boîte de dialogue à propos de.

   Il n’existe pas d’implémentation standard pour la zone à propos d’une application. L’application créée par défaut par AppWizard crée une classe de dialogue personnalisée pour votre application et l’utilise comme zone à propos de. AppWizard écrira également le gestionnaire de commandes trivial qui gère cette commande et appelle la boîte de dialogue.

   Vous allez presque toujours implémenter cette commande.

- ID_APP_EXIT quitter l’application.

   `CWinApp::OnAppExit` gère cette commande en envoyant un message WM_CLOSE à la fenêtre principale de l’application. L’arrêt standard de l’application (demande de fichiers incorrects, etc.) est géré par l' `CFrameWnd` implémentation.

   La personnalisation de ce gestionnaire de commandes n’est pas recommandée. `CWinApp::SaveAllModified`Il est recommandé de remplacer ou la `CFrameWnd` logique de fermeture.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cet ID de commande.

- ID_HELP_INDEX répertorie les rubriques d’aide de. Fichier HLP.

    > [!NOTE]
    >  Vous devez le connecter à la `CWinApp` table des messages de votre classe dérivée de pour activer cette fonctionnalité.

   `CWinApp::OnHelpIndex` gère cette commande en appelant de façon triviale `CWinApp::WinHelp` .

   La personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_HELP_USING affiche de l’aide sur l’utilisation de l’aide.

    > [!NOTE]
    >  Vous devez le connecter à la `CWinApp` table des messages de votre classe dérivée de pour activer cette fonctionnalité.

   `CWinApp::OnHelpUsing` gère cette commande en appelant de façon triviale `CWinApp::WinHelp` .

   La personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_CONTEXT_HELP passe en mode d’aide SHIFT-F1.

    > [!NOTE]
    >  Vous devez le connecter à la `CWinApp` table des messages de votre classe dérivée de pour activer cette fonctionnalité.

   `CWinApp::OnContextHelp` gère cette commande en définissant le curseur de mode d’aide, en entrant une boucle modale et en attendant que l’utilisateur sélectionne une fenêtre pour obtenir de l’aide. Reportez-vous à la [note technique 28](../mfc/tn028-context-sensitive-help-support.md) pour plus d’informations sur l’implémentation de l’aide MFC.

   La personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_HELP fournit de l’aide sur le contexte actuel

    > [!NOTE]
    >  Vous devez le connecter à la `CWinApp` table des messages de votre classe dérivée de pour activer cette fonctionnalité.

   `CWinApp::OnHelp` gère cette commande en obtenant le contexte d’aide approprié pour le contexte d’application actuel. Cela gère l’aide F1 simple, l’aide sur les boîtes de message, etc. Reportez-vous à la [note technique 28](../mfc/tn028-context-sensitive-help-support.md) pour plus d’informations sur l’implémentation de l’aide MFC.

   La personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_DEFAULT_HELP affiche l’aide par défaut pour le contexte

    > [!NOTE]
    >  Vous devez le connecter à la `CWinApp` table des messages de votre classe dérivée de pour activer cette fonctionnalité.

   Cette commande est généralement mappée à `CWinApp::OnHelpIndex` .

   Un gestionnaire de commandes différent peut être fourni si une distinction est nécessaire entre l’aide par défaut et l’index de l’aide.

- ID_NEXT_PANE accède au volet suivant

   `CView` gère cette commande pour l' `CSplitterWnd` implémentation de. Si la vue fait partie d’une fenêtre fractionnée, cette commande délègue à la fonction d’implémentation `CSplitterWnd::OnNextPaneCmd` . La vue active est alors déplacée vers le volet suivant du séparateur.

   Cette commande est désactivée si l’affichage n’est pas dans un séparateur ou s’il n’existe aucun volet suivant pour accéder à.

   La personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_PREV_PANE accède au volet précédent

   `CView` gère cette commande pour l' `CSplitterWnd` implémentation de. Si la vue fait partie d’une fenêtre fractionnée, cette commande délègue à la fonction d’implémentation `CSplitterWnd::OnNextPaneCmd` . La vue active est alors déplacée vers le volet précédent du séparateur.

   Cette commande est désactivée si l’affichage n’est pas dans un séparateur ou s’il n’existe aucun volet précédent à atteindre.

   La personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_OLE_INSERT_NEW insère un nouvel objet OLE

   Il n’existe actuellement aucune implémentation standard pour cette commande. Vous devez implémenter cela pour votre `CView` classe dérivée de pour insérer un nouvel élément/objet OLE au niveau de la sélection actuelle.

   Toutes les applications clientes OLE doivent implémenter cette commande. AppWizard, avec l’option OLE, créera une implémentation squelette de `OnInsertObject` dans votre classe d’affichage que vous devrez effectuer.

   Pour une implémentation complète de cette commande, consultez l’exemple MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) .

- ID_OLE_EDIT_LINKS modifie les liaisons OLE

   `COleDocument` gère cette commande à l’aide de l’implémentation fournie par MFC de la boîte de dialogue liaisons OLE standard. L’implémentation de cette boîte de dialogue est accessible via la `COleLinksDialog` classe. Si le document actif ne contient aucun lien, la commande est désactivée.

   La personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_OLE_VERB_FIRST... DERNIÈRE plage d’ID pour les verbes OLE

   `COleDocument` utilise cette plage d’ID de commande pour les verbes pris en charge par l’élément/objet OLE actuellement sélectionné. Il doit s’agir d’une plage dans la mesure où un type d’élément/objet OLE donné peut prendre en charge zéro, un ou plusieurs verbes personnalisés. Dans le menu de votre application, vous devez avoir un élément de menu avec l’ID de ID_OLE_VERB_FIRST. Lorsque le programme est exécuté, le menu est mis à jour avec la description du verbe de menu appropriée (ou le menu contextuel avec de nombreux verbes). La gestion du menu OLE est gérée par `AfxOleSetEditMenu` , dans le gestionnaire d’interface utilisateur de commande de mise à jour pour cette commande.

   Il n’existe aucun gestionnaire de commandes explicite pour gérer chaque ID de commande dans cette plage. `COleDocument::OnCmdMsg` est substitué pour intercepter tous les ID de commande de cette plage, les convertir en numéros de verbe de base zéro, et lancer le serveur pour ce verbe (à l’aide de `COleClientItem::DoVerb` ).

   La personnalisation ou une autre utilisation de cette plage d’ID de commande n’est pas recommandée.

- ID_VIEW_TOOLBAR active ou désactive la barre d’outils

   `CFrameWnd` gère cette commande et le gestionnaire d’interface utilisateur Update-Command pour basculer l’état visible de la barre d’outils. La barre d’outils doit être une fenêtre enfant du frame avec l’ID de fenêtre enfant AFX_IDW_TOOLBAR. Le gestionnaire de commandes bascule en fait la visibilité de la fenêtre de la barre d’outils. `CFrameWnd::RecalcLayout` est utilisé pour redessiner la fenêtre frame avec la barre d’outils dans son nouvel État. Le gestionnaire d’interface utilisateur Update-Command vérifie l’élément de menu lorsque la barre d’outils est visible.

   La personnalisation de ce gestionnaire de commandes n’est pas recommandée. Si vous souhaitez ajouter des barres d’outils supplémentaires, vous souhaiterez peut-être cloner et modifier le gestionnaire de commandes et le gestionnaire d’interface utilisateur de mise à jour de commande pour cette commande.

- ID_VIEW_STATUS_BAR active ou désactive la barre d’État

   Cette commande est implémentée de la `CFrameWnd` même façon que ID_VIEW_TOOLBAR, à l’exception d’un ID de fenêtre enfant (AFX_IDW_STATUS_BAR) différent.

## <a name="update-only-command-handlers"></a>Gestionnaires de commandes Update-Only

Plusieurs ID de commande standard sont utilisés en tant qu’indicateurs dans les barres d’État. Ils utilisent le même mécanisme de gestion d’interface utilisateur de mise à jour de commande pour afficher leur état visuel actuel pendant le temps d’inactivité de l’application. Étant donné qu’ils ne peuvent pas être sélectionnés par l’utilisateur (autrement dit, vous ne pouvez pas envoyer un volet de barre d’État), il n’est pas judicieux d’avoir un gestionnaire de ON_COMMAND pour ces ID de commande.

- ID_INDICATOR_CAPS : indicateur de verrouillage d’extrémité.

- ID_INDICATOR_NUM : indicateur Verr. NUM.

- ID_INDICATOR_SCRL : indicateur de verrouillage défil.

- ID_INDICATOR_KANA : indicateur de verrouillage KANA (applicable uniquement aux systèmes japonais).

Les trois sont implémentées dans `CFrameWnd::OnUpdateKeyIndicator` , une application d’assistance d’implémentation qui utilise l’ID de commande pour mapper à la clé virtuelle appropriée. Une implémentation courante active ou désactive (pour les volets d’État Disabled = no Text) l' `CCmdUI` objet selon que la clé virtuelle appropriée est actuellement verrouillée ou non.

La personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_INDICATOR_EXT : indicateur Select étendu.

- ID_INDICATOR_OVR : indicateur de Refrappe.

- ID_INDICATOR_REC : indicateur d’enregistrement.

Il n’existe actuellement aucune implémentation standard pour ces indicateurs.

Si vous choisissez d’implémenter ces indicateurs, nous vous recommandons d’utiliser ces ID d’indicateur et de conserver l’ordre des indicateurs dans votre barre d’État (c’est-à-dire, dans cet ordre : EXT, CAP, NUM, défil, RFP, REC).

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
