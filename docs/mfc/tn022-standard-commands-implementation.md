---
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
ms.openlocfilehash: 5c7041f40c7e30592f642d29d9d02812a9596864
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370393"
---
# <a name="tn022-standard-commands-implementation"></a>TN022 : implémentation de commandes standard

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit les implémentations de commandes standard fournies par le MFC 2.0. Lisez [d’abord la note technique 21](../mfc/tn021-command-and-message-routing.md) parce qu’elle décrit les mécanismes utilisés pour mettre en œuvre bon nombre des commandes standard.

Cette description suppose la connaissance des architectures MFC, des API et des pratiques de programmation courantes. Des API documentées ainsi que des API « de mise en œuvre » non documentées seulement sont décrites. Ce n’est pas un endroit pour commencer à apprendre sur les caractéristiques de ou comment programmer en MFC. Consultez Visual CMD pour obtenir des informations plus générales et des détails sur les API documentés.

## <a name="the-problem"></a>Le problème

MFC définit de nombreux ID de commande standard dans le fichier d’en-tête AFXRES. H. Le soutien cadre pour ces commandes varie. Comprendre où et comment les classes-cadres gèrent ces commandes vous montrera non seulement comment le cadre fonctionne à l’interne, mais fournira des informations utiles sur la façon de personnaliser les implémentations standard et de vous enseigner quelques techniques pour la mise en œuvre de vos propres gestionnaires de commande.

## <a name="contents-of-this-technical-note"></a>Contenu de cette note technique

Chaque pièce d’identité de commande est décrite en deux sections :

- Le titre: le nom symbolique de l’ID de commande (par exemple, ID_FILE_SAVE) suivi par le but de la commande (par exemple, "sauve le document actuel") séparé par un côlon.

- Un ou plusieurs paragraphes décrivant quelles classes implémenter la commande et ce que fait la mise en œuvre par défaut

La plupart des implémentations de commandes par défaut sont prébranchées dans la carte de message de la classe de base du cadre. Il existe des implémentations de commande qui nécessitent un câblage explicite dans votre classe dérivée. Ceux-ci sont décrits sous "Note". Si vous avez choisi les bonnes options dans AppWizard, ces gestionnaires par défaut seront connectés pour vous dans l’application squelette générée.

## <a name="naming-convention"></a>Conventions d’affectation de noms

Les commandes standard suivent une simple convention de nommage que nous vous recommandons d’utiliser si possible. La plupart des commandes standard sont situées dans des endroits standard dans la barre de menu d’une application. Le nom symbolique de la commande commence par "ID_" suivi du nom de menu pop-up standard, suivi par le nom de l’élément du menu. Le nom symbolique est en cas supérieur avec des pauses-mots de souligner. Pour les commandes qui n’ont pas de noms d’éléments de menu standard, un nom de commande logique est défini en commençant par «ID_» (par exemple, ID_NEXT_PANE).

Nous utilisons le préfixe "ID_" pour indiquer les commandes qui sont conçues pour être liés aux éléments de menu, boutons de barre d’outils, ou d’autres objets de commande utilisateur-interface. Les gestionnaires de commandement qui manipulent des commandes « ID_ » doivent utiliser les mécanismes ON_COMMAND et ON_UPDATE_COMMAND_UI de l’architecture de commandement du MFC.

Nous vous recommandons d’utiliser le préfixe standard "IDM_" pour les éléments de menu qui ne suivent pas l’architecture de commande et ont besoin de code spécifique au menu pour les activer et les désactiver. Bien sûr, le nombre de commandes spécifiques au menu devrait être faible puisque suivre l’architecture de commande MFC rend non seulement les gestionnaires de commande plus puissants (puisqu’ils travailleront avec des barres d’outils), mais rend le code de commande réutilisable.

## <a name="id-ranges"></a>Gammes d’identification

Veuillez consulter [la Note Technique 20](../mfc/tn020-id-naming-and-numbering-conventions.md) pour plus de détails sur l’utilisation des plages d’identification dans MFC.

Les commandes standard MFC se situent dans la gamme 0xE000 à 0xEFFF. S’il vous plaît ne vous fiez pas aux valeurs spécifiques de ces ID car ils sont sujets à changement dans les versions futures de la bibliothèque.

Votre application doit définir ses commandes dans la gamme 0x8000 à 0xDFFF.

## <a name="standard-command-ids"></a>900 D’ordre standard

Pour chaque ID de commande, il y a une chaîne rapide de ligne de message standard qui peut être trouvée dans le fichier PROMPTS. Rc. L’ID de chaîne pour cette invite de menu doit être le même que pour l’ID de commande.

- ID_FILE_NEW crée un document nouveau/vide.

    > [!NOTE]
    >  Vous devez le `CWinApp`connecter à la carte de message de votre classe dérivée pour activer cette fonctionnalité.

   `CWinApp::OnFileNew`implémente cette commande différemment en fonction du nombre de modèles de documents dans l’application. S’il n’y en a qu’un seul, `CDocTemplate` `CWinApp::OnFileNew` créera un nouveau document de ce type, ainsi que la classe de cadre et de vue appropriée.

   S’il y `CDocTemplate`en `CWinApp::OnFileNew` a plus d’un, invitera l’utilisateur avec un dialogue (AFX_IDD_NEWTYPEDLG) en lui permettant de sélectionner le type de document à utiliser. Le `CDocTemplate` sélectionné est utilisé pour créer le document.

   Une personnalisation commune de ID_FILE_NEW est de fournir un choix différent et plus graphique des types de documents. Dans ce cas, vous `CMyApp::OnFileNew` pouvez implémenter votre `CWinApp::OnFileNew`propre et le placer dans votre carte de message au lieu de . Il n’est pas nécessaire d’appeler la mise en œuvre de la classe de base.

   Une autre personnalisation commune de ID_FILE_NEW est de fournir une commande distincte pour créer un document de chaque type. Dans ce cas, vous devez définir de nouvelles Œds de commande, par exemple ID_FILE_NEW_CHART et ID_FILE_NEW_SHEET.

- ID_FILE_OPEN ouvre un document existant.

    > [!NOTE]
    >  Vous devez le `CWinApp`connecter à la carte de message de votre classe dérivée pour activer cette fonctionnalité.

   `CWinApp::OnFileOpen`a une implémentation très simple d’appels `CWinApp::DoPromptFileName` suivies avec `CWinApp::OpenDocumentFile` le fichier ou le nom de voie du fichier à ouvrir. La `CWinApp` routine `DoPromptFileName` de mise en œuvre fait le dialogue standard de FileOpen et le remplit des extensions de fichiers obtenues à partir des modèles de documents actuels.

   Une personnalisation commune de ID_FILE_OPEN est de personnaliser le dialogue FileOpen ou d’ajouter des filtres de fichiers supplémentaires. La façon recommandée de personnaliser cela est de remplacer la mise en `CWinApp::OpenDocumentFile` œuvre par défaut par votre propre dialogue FileOpen, et d’appeler avec le fichier du document ou le nom du chemin. Il n’est pas nécessaire d’appeler la classe de base.

- ID_FILE_CLOSE ferme le document actuellement ouvert.

   `CDocument::OnFileClose`invite `CDocument::SaveModified` l’utilisateur à enregistrer le document s’il `OnCloseDocument`a été modifié, puis appelle . Toute la logique de fermeture, y compris `OnCloseDocument` la destruction du document, se fait dans la routine.

    > [!NOTE]
    >  ID_FILE_CLOSE agit différemment d’un message WM_CLOSE ou d’une commande système SC_CLOSE envoyée à la fenêtre du cadre des documents. La fermeture d’une fenêtre ne fermera le document que si c’est la dernière fenêtre de cadre montrant le document. Fermer le document avec ID_FILE_CLOSE fermera non seulement le document, mais fermera toutes les fenêtres du cadre montrant le document.

- ID_FILE_SAVE Enregistre le document actuel.

   La mise en œuvre utilise une routine `CDocument::DoSave` d’aide qui est utilisé pour les deux `OnFileSave` et `OnFileSaveAs`. Si vous enregistrez un document qui n’a pas été enregistré auparavant (c’est-à-dire qu’il n’a pas `OnFileSave` de nom de voie, comme dans le cas de FileNew) ou qui a été lu à partir d’un document lu uniquement, la logique agira comme la commande ID_FILE_SAVE_AS et demandera à l’utilisateur de fournir un nouveau nom de fichier. Le processus réel d’ouverture du fichier et de `OnSaveDocument`faire l’enregistrement se fait par le biais de la fonction virtuelle .

   Il y a deux raisons courantes de personnaliser ID_FILE_SAVE. Pour les documents qui n’enregistrent pas, il suffit de supprimer les éléments de menu ID_FILE_SAVE et les boutons de barre d’outils de votre interface utilisateur. Assurez-vous également que vous ne salez `CDocument::SetModifiedFlag`jamais votre document (c’est-à-dire, ne jamais appeler ) et le cadre ne fera jamais le document d’être enregistré. Pour les documents qui enregistrent à un endroit autre qu’un fichier disque, définissez une nouvelle commande pour cette opération.

   Dans le cas `COleServerDoc`d’un , ID_FILE_SAVE est utilisé à la fois pour l’enregistrement de fichiers (pour les documents normaux) et la mise à jour du fichier (pour les documents intégrés).

   Si vos données de documents sont stockées dans des fichiers `CDocument` de disque individuels, mais `CDocument::OnSaveDocument` que `OnFileSave`vous ne souhaitez pas utiliser la mise en œuvre de sérialisation par défaut, vous devez passer outre au lieu de .

- ID_FILE_SAVE_AS Enregistre le document actuel sous un nom de fichier différent.

   La `CDocument::OnFileSaveAs` mise en `CDocument::DoSave` œuvre `OnFileSave`utilise la même routine d’aide que . La `OnFileSaveAs` commande est traitée tout comme ID_FILE_SAVE si les documents n’avaient pas de nom de fichier avant l’enregistrement. `COleServerDoc::OnFileSaveAs`implémente la logique pour enregistrer un fichier de données de document normal ou pour enregistrer un document serveur représentant un objet OLE intégré dans une autre application comme un fichier séparé.

   Si vous personnalisez la logique de ID_FILE_SAVE, vous voudrez probablement personnaliser ID_FILE_SAVE_AS de la même manière ou le fonctionnement de "Save As" peut ne pas s’appliquer à votre document. Vous pouvez supprimer l’élément de menu de votre barre de menu si ce n’est pas nécessaire.

- ID_FILE_SAVE_COPY_AS Enregistre une copie du document actuel sous un nouveau nom.

   La `COleServerDoc::OnFileSaveCopyAs` mise en `CDocument::OnFileSaveAs`œuvre est très similaire à , sauf que l’objet de document n’est pas "attaché" au fichier sous-jacent après l’enregistrement. Autrement dit, si le document en mémoire a été "modifié" avant l’enregistrement, il est toujours "modifié". En outre, cette commande n’a aucun effet sur le nom de chemin ou le titre stocké dans le document.

- ID_FILE_UPDATE informe le conteneur pour enregistrer un document intégré.

   La `COleServerDoc::OnUpdateDocument` mise en œuvre informe simplement le conteneur que l’intégration doit être sauvée. Le conteneur appelle ensuite les API OLE appropriées afin d’enregistrer l’objet intégré.

- ID_FILE_PAGE_SETUP invoque un dialogue de configuration/mise en page spécifique à l’application.

   Actuellement, il n’y a pas de norme pour ce dialogue, et le cadre n’a pas de mise en œuvre par défaut de cette commande.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cette pièce d’identité de commande.

- ID_FILE_PRINT_SETUP Invoquez le dialogue standard Print Setup.

    > [!NOTE]
    >  Vous devez le `CWinApp`connecter à la carte de message de votre classe dérivée pour activer cette fonctionnalité.

   Cette commande invoque le dialogue de configuration d’impression standard qui permet à l’utilisateur de personnaliser l’imprimante et d’imprimer les paramètres pour au moins ce document ou tout au plus tous les documents de cette application. Vous devez utiliser le panneau de contrôle pour modifier les paramètres de l’imprimante par défaut pour l’ensemble du système.

   `CWinApp::OnFilePrintSetup`a une implémentation très simple créant un `CPrintDialog` objet et appelant la `CWinApp::DoPrintDialog` fonction de mise en œuvre. Cela définit la configuration de l’imprimante par défaut de l’application.

   Le besoin commun de personnaliser cette commande est de tenir compte des paramètres de l’imprimante par document, qui doivent être stockés avec le document lorsqu’ils sont enregistrés. Pour ce faire, vous devez ajouter `CDocument` un gestionnaire `CPrintDialog` de carte de message dans votre classe qui crée un objet, l’initialise avec les attributs d’imprimante appropriés (généralement *hDevMode* et *hDevNames*), appelez le `CPrintDialog::DoModal`, et enregistrer les paramètres d’imprimante modifiés. Pour une implémentation robuste, `CWinApp::DoPrintDialog` vous devriez envisager `CWinApp::UpdatePrinterSelection` la mise en œuvre des erreurs de détection et pour traiter les défauts raisonnables et les modifications de l’imprimante à l’échelle du système de suivi.

- ID_FILE_PRINT Impression standard du document actuel

    > [!NOTE]
    >  Vous devez le `CView`connecter à la carte de message de votre classe dérivée pour activer cette fonctionnalité.

   Cette commande imprime le document actuel, ou plus correctement, démarre le processus d’impression, qui consiste à invoquer le dialogue d’impression standard et à faire fonctionner le moteur d’impression.

   `CView::OnFilePrint`implémente cette commande et la boucle d’impression principale. Il appelle `CView::OnPreparePrinting` le virtuel à inviter de l’utilisateur avec le dialogue d’impression. Il prépare ensuite la sortie DC pour aller à l’imprimante, apporte le dialogue `StartDoc` de progression d’impression (AFX_IDD_PRINTDLG), et envoie l’évasion à l’imprimante. `CView::OnFilePrint`contient également la boucle d’impression orientée page principale. Pour chaque page, il `CView::OnPrepareDC` appelle `StartPage` le virtuel suivi `CView::OnPrint` d’une évasion et appelant le virtuel pour cette page. Une fois terminé, le virtuel `CView::OnEndPrinting` est appelé, et le dialogue de progression d’impression est fermé.

   L’architecture d’impression MFC est conçue pour accrocher de nombreuses façons différentes pour l’impression et l’impression aperçu. Vous trouverez normalement les `CView` différentes fonctions primordiales adéquates pour toutes les tâches d’impression axées sur la page. Ce n’est que dans le cas d’une application qui utilise l’imprimante pour une sortie non orientée vers la page que vous devez trouver la nécessité de remplacer la ID_FILE_PRINT implémentation.

- ID_FILE_PRINT_PREVIEW Enter print-preview mode pour le document actuel.

    > [!NOTE]
    >  Vous devez le `CView`connecter à la carte de message de votre classe dérivée pour activer cette fonctionnalité.

   `CView::OnFilePrintPreview`commence le mode d’impression en `CView::DoPrintPreview`appelant la fonction d’aide documentée . `CView::DoPrintPreview`est le moteur principal de la `OnFilePrint` boucle d’impression, tout comme le moteur principal de la boucle d’impression.

   L’opération d’aperçu d’impression peut être personnalisée de `DoPrintPreview`diverses façons en passant différents paramètres à . S’il vous plaît se référer à [La note technique 30](../mfc/tn030-customizing-printing-and-print-preview.md), qui traite de certains des détails de l’aperçu d’impression et comment le personnaliser.

- ID_FILE_MRU_FILE1... FILE16 Une gamme d’ID de commande pour la **liste**MRU fichier .

   `CWinApp::OnUpdateRecentFileMenu`est un gestionnaire d’interface utilisateur de commande de mise à jour qui est l’une des utilisations les plus avancées du mécanisme ON_UPDATE_COMMAND_UI. Dans votre ressource de menu, vous n’avez qu’à définir un seul élément de menu avec id ID_FILE_MRU_FILE1. Cet élément de menu reste initialement désactivé.

   Au fur et à mesure que la liste MRU s’allonge, d’autres éléments de menu sont ajoutés à la liste. La `CWinApp` mise en œuvre standard est par défaut à la limite standard des quatre fichiers les plus récemment utilisés. Vous pouvez modifier la `CWinApp::LoadStdProfileSettings` valeur par défaut en appelant avec une valeur plus ou moins grande. La liste MRU est stockée dans l’application . Fichier INI. La liste est chargée dans `InitInstance` la fonction `LoadStdProfileSettings`de votre application si vous appelez, et est enregistrée lorsque votre application sort. Le gestionnaire d’interface utilisateur de commande de mise à jour MRU convertira également les chemins absolus en chemins relatifs pour l’affichage sur le menu de fichier.

   `CWinApp::OnOpenRecentFile`est le gestionnaire ON_COMMAND qui effectue la commande réelle. Il obtient simplement le nom de fichier `CWinApp::OpenDocumentFile`de la liste MRU et les appels , qui fait tout le travail d’ouverture du fichier et la mise à jour de la liste MRU.

   La personnalisation de ce gestionnaire de commande n’est pas recommandée.

- ID_EDIT_CLEAR efface la sélection actuelle

   Actuellement, il n’y a pas de mise en œuvre standard pour cette commande. Vous devez mettre `CView`en œuvre cela pour chaque classe dérivée.

   `CEditView`fournit une mise en `CEdit::Clear`œuvre de cette commande à l’aide de . La commande est désactivée s’il n’y a pas de sélection en cours.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cette pièce d’identité de commande.

- ID_EDIT_CLEAR_ALL efface l’intégralité du document.

   Actuellement, il n’y a pas de mise en œuvre standard pour cette commande. Vous devez mettre `CView`en œuvre cela pour chaque classe dérivée.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cette pièce d’identité de commande. Voir l’échantillon MFC Tutorial [SCRIBBLE](../overview/visual-cpp-samples.md) par exemple implémentation.

- ID_EDIT_COPY Copie la sélection actuelle au Clipboard.

   Actuellement, il n’y a pas de mise en œuvre standard pour cette commande. Vous devez mettre `CView`en œuvre cela pour chaque classe dérivée.

   `CEditView`fournit une mise en œuvre de cette commande, qui copie `CEdit::Copy`le texte actuellement sélectionné au Clipboard comme CF_TEXT à l’aide . La commande est désactivée s’il n’y a pas de sélection en cours.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cette pièce d’identité de commande.

- ID_EDIT_CUT Coupe la sélection actuelle au Clipboard.

   Actuellement, il n’y a pas de mise en œuvre standard pour cette commande. Vous devez mettre `CView`en œuvre cela pour chaque classe dérivée.

   `CEditView`fournit une mise en œuvre de cette commande, qui coupe `CEdit::Cut`le texte actuellement sélectionné au Clipboard comme CF_TEXT à l’aide . La commande est désactivée s’il n’y a pas de sélection en cours.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cette pièce d’identité de commande.

- ID_EDIT_FIND commence l’opération de recherche, soulève le dialogue de recherche sans mode.

   Actuellement, il n’y a pas de mise en œuvre standard pour cette commande. Vous devez mettre `CView`en œuvre cela pour chaque classe dérivée.

   `CEditView`fournit une mise en œuvre de `OnEditFindReplace` cette commande, qui appelle la fonction d’aide à la mise en œuvre pour utiliser et stocker les paramètres précédents de recherche / remplacer dans les variables de mise en œuvre privées. La `CFindReplaceDialog` classe est utilisée pour gérer le dialogue sans mode pour inciter l’utilisateur.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cette pièce d’identité de commande.

- ID_EDIT_PASTE insère le contenu actuel du Clipboard.

   Actuellement, il n’y a pas de mise en œuvre standard pour cette commande. Vous devez mettre `CView`en œuvre cela pour chaque classe dérivée.

   `CEditView`fournit une implémentation de cette commande, qui copie `CEdit::Paste`les données actuelles du Clipboard remplaçant le texte sélectionné à l’aide de . La commande est désactivée s’il n’y a pas **de CF_TEXT** dans le Clipboard.

   `COleClientDoc`fournit simplement un gestionnaire d’interface utilisateur de commande de mise à jour pour cette commande. Si le Clipboard ne contient pas d’élément/objet OLE intégré, la commande sera désactivée. Vous êtes responsable de l’écriture du gestionnaire de la commande réelle pour faire le coller réel. Si votre application OLE peut également coller d’autres formats, vous devez fournir votre propre gestionnaire `COleClientDoc` d’interface utilisateur de commande de commande dans votre vue ou document (c’est-à-dire quelque part avant dans le routage de la cible de commande).

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cette pièce d’identité de commande.

   Pour remplacer la mise en `COleClientItem::CanPaste`œuvre standard OLE, utilisez .

- ID_EDIT_PASTE_LINK insère un lien à partir du contenu actuel du Clipboard.

   Actuellement, il n’y a pas de mise en œuvre standard pour cette commande. Vous devez mettre `CView`en œuvre cela pour chaque classe dérivée.

   `COleDocument`fournit simplement un gestionnaire d’interface utilisateur de commande de mise à jour pour cette commande. Si le Clipboard ne contient pas d’élément/objet OLE liant, la commande sera désactivée. Vous êtes responsable de l’écriture du gestionnaire de la commande réelle pour faire le coller réel. Si votre application OLE peut également coller d’autres formats, vous devez fournir votre propre gestionnaire `COleDocument` d’interface utilisateur de commande de commande dans votre vue ou document (c’est-à-dire quelque part avant dans le routage de la cible de commande).

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cette pièce d’identité de commande.

   Pour remplacer la mise en `COleClientItem::CanPasteLink`œuvre standard OLE, utilisez .

- ID_EDIT_PASTE_SPECIAL insère le contenu actuel du Clipboard avec des options.

   Actuellement, il n’y a pas de mise en œuvre standard pour cette commande. Vous devez mettre `CView`en œuvre cela pour chaque classe dérivée. MFC ne fournit pas ce dialogue.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cette pièce d’identité de commande.

- ID_EDIT_REPEAT répète la dernière opération.

   Actuellement, il n’y a pas de mise en œuvre standard pour cette commande. Vous devez mettre `CView`en œuvre cela pour chaque classe dérivée.

   `CEditView`fournit une mise en œuvre de cette commande pour répéter la dernière opération de recherche. Les variables de implémentation privées pour la dernière trouvaille sont utilisées. La commande est désactivée si une découverte ne peut pas être tentée.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cette pièce d’identité de commande.

- ID_EDIT_REPLACE Commence l’opération de remplacement, soulève le dialogue de remplacement sans mode.

   Actuellement, il n’y a pas de mise en œuvre standard pour cette commande. Vous devez mettre `CView`en œuvre cela pour chaque classe dérivée.

   `CEditView`fournit une mise en œuvre de `OnEditFindReplace` cette commande, qui appelle la fonction d’aide à la mise en œuvre pour utiliser et stocker les paramètres précédents de recherche / remplacer dans les variables de mise en œuvre privées. La `CFindReplaceDialog` classe est utilisée pour gérer le dialogue sans mode qui invite l’utilisateur.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cette pièce d’identité de commande.

- ID_EDIT_SELECT_ALL sélectionne l’intégralité du document.

   Actuellement, il n’y a pas de mise en œuvre standard pour cette commande. Vous devez mettre `CView`en œuvre cela pour chaque classe dérivée.

   `CEditView`fournit une mise en œuvre de cette commande, qui sélectionne tout le texte du document. La commande est désactivée s’il n’y a pas de texte à sélectionner.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cette pièce d’identité de commande.

- ID_EDIT_UNDO annule la dernière opéra tion.

   Actuellement, il n’y a pas de mise en œuvre standard pour cette commande. Vous devez mettre `CView`en œuvre cela pour chaque classe dérivée.

   `CEditView`fournit une mise en `CEdit::Undo`œuvre de cette commande, en utilisant . La commande est `CEdit::CanUndo` désactivée si elle retourne FALSE.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cette pièce d’identité de commande.

- ID_EDIT_REDO refait la dernière opéra tion.

   Actuellement, il n’y a pas de mise en œuvre standard pour cette commande. Vous devez mettre `CView`en œuvre cela pour chaque classe dérivée.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cette pièce d’identité de commande.

- ID_WINDOW_NEW ouvre une autre fenêtre sur le document actif.

   `CMDIFrameWnd::OnWindowNew`implémente cette fonctionnalité puissante en utilisant le modèle de document du document actuel pour créer un autre cadre contenant une autre vue du document actuel.

   Comme la plupart des commandes de menu fenêtre d’interface documentaire multiple (MDI), la commande est désactivée s’il n’y a pas de fenêtre active pour enfants MDI.

   La personnalisation de ce gestionnaire de commande n’est pas recommandée. Si vous souhaitez fournir une commande qui crée des vues supplémentaires ou des fenêtres de cadre, vous serez probablement mieux d’inventer votre propre commande. Vous pouvez cloner `CMDIFrameWnd::OnWindowNew` le code et le modifier au cadre spécifique et afficher les classes de votre goût.

- ID_WINDOW_ARRANGE organise des icônes au bas d’une fenêtre MDI.

   `CMDIFrameWnd`met en œuvre cette commande MDI standard dans une fonction `OnMDIWindowCmd`d’aide à la mise en œuvre . Cette aide cartes des cartes id de commande aux messages MDI Windows et peut donc partager beaucoup de code.

   Comme la plupart des commandes de menu MDI Window, la commande est désactivée s’il n’y a pas de fenêtre d’enfant MDI active.

   La personnalisation de ce gestionnaire de commande n’est pas recommandée.

- ID_WINDOW_CASCADE fenêtres Cascades afin qu’elles se chevauchent.

   `CMDIFrameWnd`met en œuvre cette commande MDI standard dans une fonction `OnMDIWindowCmd`d’aide à la mise en œuvre . Cette aide cartes des cartes id de commande aux messages MDI Windows et peut donc partager beaucoup de code.

   Comme la plupart des commandes de menu MDI Window, la commande est désactivée s’il n’y a pas de fenêtre d’enfant MDI active.

   La personnalisation de ce gestionnaire de commande n’est pas recommandée.

- ID_WINDOW_TILE_HORZ les fenêtres de tuiles horizontalement.

   Cette commande est `CMDIFrameWnd` implémentée comme ID_WINDOW_CASCADE, à l’exception d’un autre message MDI Windows est utilisé pour l’opération.

   Vous devez choisir l’orientation de tuiles par défaut pour votre application. Vous pouvez le faire en changeant l’ID pour l’élément de menu fenêtre "Tile" à ID_WINDOW_TILE_HORZ ou ID_WINDOW_TILE_VERT.

- ID_WINDOW_TILE_VERT les fenêtres de tuiles verticalement.

   Cette commande est `CMDIFrameWnd` implémentée comme ID_WINDOW_CASCADE, à l’exception d’un autre message MDI Windows est utilisé pour l’opération.

   Vous devez choisir l’orientation de tuiles par défaut pour votre application. Vous pouvez le faire en changeant l’ID pour l’élément de menu fenêtre "Tile" à ID_WINDOW_TILE_HORZ ou ID_WINDOW_TILE_VERT.

- ID_WINDOW_SPLIT interface clavier à splitter.

   `CView`gère cette commande `CSplitterWnd` pour la mise en œuvre. Si la vue fait partie d’une fenêtre de splitter, cette commande déléguera à la fonction `CSplitterWnd::DoKeyboardSplit`de mise en œuvre . Cela placera le splitter dans un mode qui permettra aux utilisateurs du clavier de diviser ou de débrancher une fenêtre de splitter.

   Cette commande est désactivée si la vue n’est pas dans un diviseur.

   La personnalisation de ce gestionnaire de commande n’est pas recommandée.

- ID_APP_ABOUT invoque la boîte de dialogue.

   Il n’y a pas de mise en œuvre standard pour la case About d’une application. L’application créée par défaut AppWizard créera une classe de dialogue personnalisée pour votre application et l’utilisera comme votre encadré About. AppWizard écrira également le gestionnaire de commande trivial qui gère cette commande et invoque le dialogue.

   Vous implémenterez presque toujours cette commande.

- ID_APP_EXIT Quitter l’application.

   `CWinApp::OnAppExit`gère cette commande en envoyant un message WM_CLOSE à la fenêtre principale de l’application. L’arrêt standard de l’application (incitation pour les fichiers `CFrameWnd` sales et ainsi de suite) est géré par la mise en œuvre.

   La personnalisation de ce gestionnaire de commande n’est pas recommandée. La prépondérer `CWinApp::SaveAllModified` ou la `CFrameWnd` logique de fermeture est recommandée.

   Si vous choisissez d’implémenter cette commande, nous vous recommandons d’utiliser cette pièce d’identité de commande.

- ID_HELP_INDEX Listes Aider les sujets de . Fichier HLP.

    > [!NOTE]
    >  Vous devez le `CWinApp`connecter à la carte de message de votre classe dérivée pour activer cette fonctionnalité.

   `CWinApp::OnHelpIndex`gère cette commande en `CWinApp::WinHelp`appelant trivialement .

   La personnalisation de ce gestionnaire de commande n’est pas recommandée.

- ID_HELP_USING affiche de l’aide sur la façon d’utiliser l’aide.

    > [!NOTE]
    >  Vous devez le `CWinApp`connecter à la carte de message de votre classe dérivée pour activer cette fonctionnalité.

   `CWinApp::OnHelpUsing`gère cette commande en `CWinApp::WinHelp`appelant trivialement .

   La personnalisation de ce gestionnaire de commande n’est pas recommandée.

- ID_CONTEXT_HELP entre en mode aide SHIFT-F1.

    > [!NOTE]
    >  Vous devez le `CWinApp`connecter à la carte de message de votre classe dérivée pour activer cette fonctionnalité.

   `CWinApp::OnContextHelp`gère cette commande en définissant le curseur du mode d’aide, en entrant dans une boucle modale et en attendant que l’utilisateur sélectionne une fenêtre pour obtenir de l’aide. Veuillez consulter [la note technique 28](../mfc/tn028-context-sensitive-help-support.md) pour plus de détails sur la mise en œuvre de MFC Help.

   La personnalisation de ce gestionnaire de commande n’est pas recommandée.

- ID_HELP donne de l’aide sur le contexte actuel

    > [!NOTE]
    >  Vous devez le `CWinApp`connecter à la carte de message de votre classe dérivée pour activer cette fonctionnalité.

   `CWinApp::OnHelp`gère cette commande en obtenant le bon contexte d’aide pour le contexte d’application actuel. Cela gère l’aide F1 simple, aider sur les boîtes de messages et ainsi de suite. Veuillez consulter [la note technique 28](../mfc/tn028-context-sensitive-help-support.md) pour plus de détails sur la mise en œuvre de l’aide MFC.

   La personnalisation de ce gestionnaire de commande n’est pas recommandée.

- ID_DEFAULT_HELP Affiche l’aide par défaut pour le contexte

    > [!NOTE]
    >  Vous devez le `CWinApp`connecter à la carte de message de votre classe dérivée pour activer cette fonctionnalité.

   Cette commande est généralement `CWinApp::OnHelpIndex`cartographiée pour .

   Un gestionnaire de commande différent peut être fourni si une distinction entre l’aide par défaut et l’index d’aide est souhaitée.

- ID_NEXT_PANE va à la prochaine vitre

   `CView`gère cette commande `CSplitterWnd` pour la mise en œuvre. Si la vue fait partie d’une fenêtre de splitter, cette commande déléguera à la fonction `CSplitterWnd::OnNextPaneCmd`de mise en œuvre . Cela déplacera la vue active à la prochaine vitre dans le diviseur.

   Cette commande est désactivée si la vue n’est pas dans un diviseur ou il n’y a pas de prochain volet à aller.

   La personnalisation de ce gestionnaire de commande n’est pas recommandée.

- ID_PREV_PANE passe à la vitre précédente

   `CView`gère cette commande `CSplitterWnd` pour la mise en œuvre. Si la vue fait partie d’une fenêtre de splitter, cette commande déléguera à la fonction `CSplitterWnd::OnNextPaneCmd`de mise en œuvre . Cela déplacera la vue active à la vitre précédente dans le diviseur.

   Cette commande est désactivée si la vue n’est pas dans un diviseur ou il n’y a pas de volet précédent à aller.

   La personnalisation de ce gestionnaire de commande n’est pas recommandée.

- ID_OLE_INSERT_NEW insère un nouvel objet OLE

   Actuellement, il n’y a pas de mise en œuvre standard pour cette commande. Vous devez implémenter ceci pour votre `CView`classe dérivée pour insérer un nouvel élément/objet OLE à la sélection actuelle.

   Toutes les applications client OLE doivent implémenter cette commande. AppWizard, avec l’option OLE, créera une mise en œuvre squelette de votre classe de `OnInsertObject` vue que vous devrez remplir.

   Voir l’exemple de l’échantillon [OCLIENT](../overview/visual-cpp-samples.md) du MFC OLE pour une mise en œuvre complète de cette commande.

- ID_OLE_EDIT_LINKS modifie les liens OLE

   `COleDocument`gère cette commande en utilisant la mise en œuvre fournie par MFC du dialogue standard des liens OLE. La mise en œuvre de `COleLinksDialog` ce dialogue est accessible par l’intermédiaire de la classe. Si le document actuel ne contient aucun lien, la commande est désactivée.

   La personnalisation de ce gestionnaire de commande n’est pas recommandée.

- ID_OLE_VERB_FIRST... LAST Une gamme d’identification pour les verbes OLE

   `COleDocument`utilise cette gamme d’ID de commande pour les verbes pris en charge par l’élément/objet OLE actuellement sélectionné. Il doit s’agir d’une plage puisqu’un type d’article/objet OLE donné peut prendre en charge des verbes zéro ou plus personnalisés. Dans le menu de votre application, vous devriez avoir un élément de menu avec l’ID de ID_OLE_VERB_FIRST. Lorsque le programme est exécuté, le menu sera mis à jour avec la description appropriée du verbe du menu (ou un menu pop-up avec de nombreux verbes). La gestion du menu OLE `AfxOleSetEditMenu`est gérée par , fait dans le gestionnaire d’interface utilisateur de commande de mise à jour pour cette commande.

   Il n’y a pas de gestionnaires de commande explicites pour le traitement de chacune de l’ID de commande dans cette plage. `COleDocument::OnCmdMsg`est remplacé pour piéger toutes les pièces d’ID de commande dans cette gamme, les `COleClientItem::DoVerb`transformer en nombres verbes à base zéro, et lancer le serveur pour ce verbe (en utilisant ).

   La personnalisation ou toute autre utilisation de cette plage d’identification de commande n’est pas recommandée.

- ID_VIEW_TOOLBAR toggles la barre d’outils sur et en dehors

   `CFrameWnd`gère cette commande et le gestionnaire d’interface utilisateur de commande de mise à jour pour basculer l’état visible de la barre d’outils. La barre d’outils doit être une fenêtre enfant du cadre avec l’identification de fenêtre d’enfant de AFX_IDW_TOOLBAR. Le gestionnaire de commande bascule en fait la visibilité de la fenêtre de la barre d’outils. `CFrameWnd::RecalcLayout`est utilisé pour redessiner la fenêtre de cadre avec la barre d’outils dans son nouvel état. Le gestionnaire d’interface utilisateur de commande de mise à jour vérifie l’élément de menu lorsque la barre d’outils est visible.

   La personnalisation de ce gestionnaire de commande n’est pas recommandée. Si vous souhaitez ajouter des barres d’outils supplémentaires, vous voudrez cloner et modifier le gestionnaire de commande et le gestionnaire d’interface utilisateur de commande de mise à jour pour cette commande.

- ID_VIEW_STATUS_BAR toggles la barre d’état sur et en dehors

   Cette commande est `CFrameWnd` implémentée comme ID_VIEW_TOOLBAR, à l’exception d’une autre carte d’identité pour enfants (AFX_IDW_STATUS_BAR) est utilisée.

## <a name="update-only-command-handlers"></a>Mise à jour-Seulement Command Handlers

Plusieurs Œd de commande standard sont utilisés comme indicateurs dans les barres d’état. Ceux-ci utilisent le même mécanisme de manutention de l’interface utilisateur de commande de mise à jour pour afficher leur état visuel actuel pendant le temps d’inactivité de l’application. Comme ils ne peuvent pas être sélectionnés par l’utilisateur (c’est-à-dire, vous ne pouvez pas pousser un volet de barre de statut), alors il n’est pas logique d’avoir un gestionnaire de ON_COMMAND pour ces identifiants de commande.

- ID_INDICATOR_CAPS : indicateur de verrouillage cap.

- ID_INDICATOR_NUM : indicateur de verrouillage NUM.

- ID_INDICATOR_SCRL : indicateur de verrouillage SCRL.

- ID_INDICATOR_KANA : indicateur de verrouillage KANA (applicable uniquement aux systèmes japonais).

Tous les trois sont `CFrameWnd::OnUpdateKeyIndicator`mis en œuvre dans , un aide d’implémentation qui utilise l’ID de commande pour cartographier la clé virtuelle appropriée. Une implémentation commune permet ou désactive (pour `CCmdUI` les vitres de statut désactivées - pas de texte) l’objet selon que la clé virtuelle appropriée est actuellement verrouillée.

La personnalisation de ce gestionnaire de commande n’est pas recommandée.

- ID_INDICATOR_EXT : INDICATEUR de sélection EXTended.

- ID_INDICATOR_OVR : indicateur OVeRstrike.

- ID_INDICATOR_REC : INDICATEUR RECording.

À l’heure actuelle, il n’existe pas de mise en œuvre standard pour ces indicateurs.

Si vous choisissez de mettre en œuvre ces indicateurs, nous vous recommandons d’utiliser ces UDI d’indicateur et de maintenir la commande des indicateurs dans votre barre d’état (c’est-à-dire dans cet ordre : EXT, CAP, NUM, SCRL, OVR, REC).

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
