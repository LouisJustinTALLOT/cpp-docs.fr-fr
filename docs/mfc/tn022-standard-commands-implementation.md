---
title: 'TN022 : Implémentation de commandes Standard | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.commands
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a058a48000d36b2f270e75eeda4987750bde8a7f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443502"
---
# <a name="tn022-standard-commands-implementation"></a>TN022 : implémentation de commandes standard

> [!NOTE]
>  La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit les implémentations de commandes standard fournies par MFC 2.0. Lecture [Note technique 21](../mfc/tn021-command-and-message-routing.md) premier, car il décrit les mécanismes utilisés pour implémenter la plupart des commandes standards.

Cette description présupposent une connaissance des architectures MFC, API et pratique de programmation courante. Documenté ainsi non documentée « implémentation uniquement » API sont décrits. Cela n’est pas un point de départ en savoir plus sur les fonctionnalités d’ou comment programmer dans MFC. Reportez-vous à Visual C++ pour des informations générales et les détails de la documentation de l’API.

## <a name="the-problem"></a>Le problème

MFC définit plusieurs ID de commande standard dans le fichier d’en-tête AFXRES. H. Prise en charge du Framework pour ces commandes varie. Comprendre où et comment les classes de framework gérer ces commandes pas uniquement vous montrera comment le framework fonctionne en interne, mais fournit des informations utiles sur la façon de personnaliser les implémentations standards et à apprendre quelques techniques permettant d’implémenter vos propres gestionnaires de commandes.

## <a name="contents-of-this-technical-note"></a>Contenu de cette Note technique

Chaque ID de commande est décrite dans les deux sections :

- Le titre : le nom symbolique de l’ID de commande (par exemple, ID_FILE_SAVE) suivi de l’objectif de la commande (par exemple, « enregistre le document actif ») séparés par un signe deux-points.

- Un ou plusieurs paragraphes décrivant les classes qui implémentent la commande, et le rôle de l’implémentation par défaut

La plupart des implémentations de commande par défaut sont prewired dans la table de messages de la classe de base de l’infrastructure. Il existe quelques implémentations de commande nécessitant un câblage explicit dans votre classe dérivée. Ceux-ci sont décrits sous « Note ». Si vous avez choisi les options appropriées dans AppWizard, ces gestionnaires par défaut seront connectés dans l’application squelette générée pour vous.

## <a name="naming-convention"></a>Convention d'affectation de noms

Commandes standards suivent une convention d’affectation de noms simple qui nous vous recommandons de qu'utiliser si possible. La plupart des commandes sont situés dans des emplacements standards dans la barre de menus d’une application. Le nom symbolique de la commande commence par « ID_ » suivie du nom de menu contextuel standard, suivi du nom d’élément de menu. Le nom symbolique est en majuscules avec un trait de soulignement-césures des mots. Pour les commandes qui n’ont pas de noms d’élément de menu standard, un nom de la logique de commande est défini en commençant par « ID_ » (par exemple, ID_NEXT_PANE).

Nous utilisons le préfixe « ID_ » pour indiquer les commandes qui sont conçus pour être liées aux éléments de menu, des boutons de barre d’outils ou autres objets d’interface utilisateur de commande. Gestion des commandes de « ID_ » des gestionnaires de commandes doivent utiliser les mécanismes ON_COMMAND et ON_UPDATE_COMMAND_UI de l’architecture de commande MFC.

Nous vous recommandons de qu'utiliser le préfixe « IDM_ » standard pour les éléments de menu qui ne sont pas suivre l’architecture de la commande et avez besoin de code de menu spécifiques pour activer et désactiver les. Bien sûr le nombre spécifique des commandes de menu doit être petite dans la mesure où suivant l’architecture de la commande MFC non seulement rend la plus puissante des gestionnaires de commandes (dans la mesure où ils fonctionnent avec les barres d’outils), mais rend le code de gestionnaire de commande réutilisables.

## <a name="id-ranges"></a>Plages d’ID

Reportez-vous à [Technical Note 20](../mfc/tn020-id-naming-and-numbering-conventions.md) pour plus d’informations sur l’utilisation de plages d’ID dans MFC.

Commandes standard MFC comprise dans la plage 0xE000 à 0xEFFF. Veuillez ne comptez pas sur les valeurs spécifiques de ces ID dans la mesure où ils sont susceptibles de changer dans les futures versions de la bibliothèque.

Votre application doit définir ses commandes dans la plage 0 x 8000 à 0xDFFF.

## <a name="standard-command-ids"></a>ID de commande standard

Pour chaque ID de commande, il existe une chaîne d’invite ligne message standard qui se trouve dans les invites de fichier. RC. L’ID de chaîne de cette invite de menu doit être identique à l’ID de commande.

- ID_FILE_NEW crée un document nouveau ou vide.

    > [!NOTE]
    >  Vous devez vous connecter cette option pour votre `CWinApp`-dérivée de table des messages de la classe pour activer cette fonctionnalité.

     `CWinApp::OnFileNew` implémente cette commande différemment selon le nombre de modèles de document dans l’application. S’il en existe qu’un seul `CDocTemplate`, `CWinApp::OnFileNew` créera un nouveau document de ce type, ainsi que la classe frame et vue.

     S’il existe plusieurs `CDocTemplate`, `CWinApp::OnFileNew` invitera l’utilisateur avec une boîte de dialogue (AFX_IDD_NEWTYPEDLG) lui permet de sélectionner les documents de type à utiliser. Le texte sélectionné `CDocTemplate` est utilisé pour créer le document.

     Une personnalisation courantes de ID_FILE_NEW consiste à fournir un autre et plus de choix des types de document de graphique. Dans ce cas vous pouvez implémenter votre propre `CMyApp::OnFileNew` et placez-le dans votre table des messages à la place de `CWinApp::OnFileNew`. Il est inutile d’appeler l’implémentation de classe de base.

     Une autre personnalisation courantes de ID_FILE_NEW consiste à fournir une commande distincte pour la création d’un document de chaque type. Dans ce cas, vous devez définir nouveaux ID de commandes, par exemple ID_FILE_NEW_CHART et ID_FILE_NEW_SHEET.

- ID_FILE_OPEN ouvre un document existant.

    > [!NOTE]
    >  Vous devez vous connecter cette option pour votre `CWinApp`-dérivée de table des messages de la classe pour activer cette fonctionnalité.

     `CWinApp::OnFileOpen` a une implémentation très simple de l’appel `CWinApp::DoPromptFileName` suivie `CWinApp::OpenDocumentFile` avec le nom de fichier ou chemin d’accès du fichier à ouvrir. Le `CWinApp` routine d’implémentation `DoPromptFileName` permet d’afficher la boîte de dialogue FileOpen standard et la remplit avec les extensions de fichier obtenues à partir des modèles de document en cours.

     Une personnalisation courantes de ID_FILE_OPEN consiste à personnaliser la boîte de dialogue FileOpen ou ajouter des filtres de fichiers supplémentaires. La méthode recommandée pour personnaliser ce paramètre est de remplacer l’implémentation par défaut avec votre propre boîte de dialogue FileOpen et appelez `CWinApp::OpenDocumentFile` avec le nom de fichier ou chemin d’accès du document. Il est inutile d’appeler la classe de base.

- ID_FILE_CLOSE ferme le document actuellement ouvert.

     `CDocument::OnFileClose` appels `CDocument::SaveModified` pour inviter l’utilisateur à enregistrer le document si elle a été modifiée, puis appelle `OnCloseDocument`. Toute la logique de fermeture, y compris la destruction du document, l’opération s’effectue dans le `OnCloseDocument` routine.

    > [!NOTE]
    >  Actes ID_FILE_CLOSE différemment à partir d’un message WM_CLOSE ou une commande du système SC_CLOSE envoyé à la fenêtre frame de documents. Fermeture d’une fenêtre ferme le document uniquement si c’est la dernière fenêtre frame affichant le document. Fermer le document avec ID_FILE_CLOSE fermera pas uniquement le document, mais va s’arrêter toutes les fenêtres frame affichant le document.

- ID_FILE_SAVE enregistre le document actif.

     L’implémentation utilise une routine d’assistance `CDocument::DoSave` qui est utilisé pour les deux `OnFileSave` et `OnFileSaveAs`. Si vous enregistrez un document qui n’a pas été enregistré (autrement dit, il n’a pas un nom de chemin d’accès, comme dans le cas de fichier-nouveau) ou qui a été lu à partir d’un document en lecture seule, la `OnFileSave` logique agit comme le ID_FILE_SAVE_AS commande et demandez à l’utilisateur à fournir un nouveau nom de fichier . Le processus réel de l’ouverture du fichier, ainsi que l’enregistrement s’effectue via la fonction virtuelle `OnSaveDocument`.

     Il existe deux raisons principales pour personnaliser ID_FILE_SAVE. Pour les documents qui ne l’enregistrez pas, supprimez simplement les éléments de menu ID_FILE_SAVE et les boutons de barre d’outils à partir de votre interface utilisateur. Assurez-vous également que vous dirty jamais votre document (autrement dit, ne jamais appeler `CDocument::SetModifiedFlag`) et le framework ne provoque jamais l’enregistrement du document. Pour les documents qui enregistrent dans un endroit quelconque autre qu’un fichier de disque, définissez une nouvelle commande pour cette opération.

     Dans le cas d’un `COleServerDoc`, ID_FILE_SAVE est utilisé pour l’enregistrement de fichier (pour les documents normales) et de mise à jour de fichier (pour les documents incorporés).

     Si vos données de document sont stockées dans les fichiers de disque individuelles, mais vous ne souhaitez pas utiliser la valeur par défaut `CDocument` sérialiser l’implémentation, vous devez substituer `CDocument::OnSaveDocument` au lieu de `OnFileSave`.

- ID_FILE_SAVE_AS enregistre le document actif sous un autre nom de fichier.

     Le `CDocument::OnFileSaveAs` implémentation utilise les mêmes `CDocument::DoSave` routine d’assistance comme `OnFileSave`. Le `OnFileSaveAs` commande est traitée comme ID_FILE_SAVE si les documents n’avaient aucun nom de fichier avant l’enregistrement. `COleServerDoc::OnFileSaveAs` implémente la logique pour enregistrer un fichier de données de document normal ou enregistrer un document serveur qui représente un objet OLE incorporé dans une autre application dans un fichier distinct.

     Si vous personnalisez la logique de ID_FILE_SAVE, vous voudrez probablement personnaliser ID_FILE_SAVE_AS de manière similaire, ou l’opération de « Enregistrer sous » ne peut-être pas s’appliquer à votre document. S’il n’est pas nécessaire, vous pouvez supprimer l’élément de menu à partir de votre barre de menus.

- ID_FILE_SAVE_COPY_AS enregistre une copie actif sous un nouveau nom.

     Le `COleServerDoc::OnFileSaveCopyAs` implémentation est très similaire à `CDocument::OnFileSaveAs`, sauf que l’objet de document n'est pas « attaché » dans le fichier sous-jacent après l’enregistrement. Autrement dit, si le document en mémoire a été « modifié » avant l’enregistrement, elle est toujours « modifiée ». En outre, cette commande n’a aucun effet sur le nom de chemin d’accès ou le titre stocké dans le document.

- ID_FILE_UPDATE informe le conteneur pour enregistrer un document incorporé.

     Le `COleServerDoc::OnUpdateDocument` implémentation simplement notifiies le conteneur que l’incorporation doit être enregistré. Le conteneur appelle ensuite les API OLE approprié afin d’enregistrer l’objet incorporé.

- ID_FILE_PAGE_SETUP appelle une boîte de dialogue d’installation/mise en page spécifique à l’application.

     Il n’existe actuellement aucune norme pour cette boîte de dialogue et le framework ne possède pas d’implémentation par défaut de cette commande.

     Si vous choisissez d’implémenter cette commande, nous vous recommandons de qu'utiliser cet ID de commande.

- ID_FILE_PRINT_SETUP appeler la boîte de dialogue Configuration de l’impression standard.

    > [!NOTE]
    >  Vous devez vous connecter cette option pour votre `CWinApp`-dérivée de table des messages de la classe pour activer cette fonctionnalité.

     Cette commande appelle la boîte de dialogue Paramètres d’impression standard qui permet à l’utilisateur de personnaliser l’imprimante et les paramètres d’impression pour au moins ce document ou au plus tous les documents dans cette application. Vous devez utiliser le panneau de configuration pour modifier les paramètres d’imprimante par défaut pour l’ensemble du système.

     `CWinApp::OnFilePrintSetup` a une implémentation très simple de la création un `CPrintDialog` objet et en appelant le `CWinApp::DoPrintDialog` fonction de l’implémentation. Cela définit la configuration de l’application l’imprimante par défaut.

     Le besoin fréquent de personnalisation de cette commande consiste à autoriser pour les paramètres d’imprimante par document, qui doivent être stockés avec le document lors de l’enregistrement. Pour ce faire, vous devez ajouter un gestionnaire de la table des messages dans votre `CDocument` classe qui crée un `CPrintDialog` de l’objet, l’initialise avec les attributs d’imprimante appropriés (généralement *hDevMode* et *hDevNames*), appelez le `CPrintDialog::DoModal`et enregistrer les paramètres d’imprimante modifié. Pour une implémentation robuste, vous devez examiner l’implémentation de `CWinApp::DoPrintDialog` pour la détection des erreurs et `CWinApp::UpdatePrinterSelection` pour le traitement des valeurs par défaut sensibles et le suivi des modifications de l’imprimante de l’échelle du système.

- ID_FILE_PRINT Standard impression du document actif

    > [!NOTE]
    >  Vous devez vous connecter cette option pour votre `CView`-dérivée de table des messages de la classe pour activer cette fonctionnalité.

     Cette commande imprime le document actif, ou plus exactement, démarre le processus d’impression, ce qui implique l’appel de la boîte de dialogue Imprimer standard et le moteur d’impression en cours d’exécution.

     `CView::OnFilePrint` implémente cette commande et la boucle d’impression principale. Il appelle virtuel `CView::OnPreparePrinting` à l’invite de l’utilisateur avec la boîte de dialogue Imprimer. Il prépare la sortie de contrôleur de domaine pour accéder à l’imprimante, affiche la boîte de dialogue Progression impression (AFX_IDD_PRINTDLG), puis envoie la `StartDoc` Echap pour l’imprimante. `CView::OnFilePrint` contient également la boucle d’impression orientée sur la page principale. Pour chaque page, il appelle virtuel `CView::OnPrepareDC` suivie d’un `StartPage` échappement et l’appel virtuel `CView::OnPrint` pour cette page. Lorsque vous avez terminé, le serveur virtuel `CView::OnEndPrinting` est appelée, et la boîte de dialogue de progression d’impression est fermé.

     L’architecture d’impression MFC est conçu pour connecter de différentes manières pour l’impression et Aperçu avant impression. Vous devez normalement trouver les différents `CView` fonctions substituables adéquates pour toutes les tâches d’impression orientés page. Uniquement dans le cas d’une application qui utilise l’imprimante pour la sortie orienté non page, si vous trouvez la nécessité de remplacer l’implémentation ID_FILE_PRINT.

- ID_FILE_PRINT_PREVIEW entrer en mode Aperçu avant impression pour le document actif.

    > [!NOTE]
    >  Vous devez vous connecter cette option pour votre `CView`-dérivée de table des messages de la classe pour activer cette fonctionnalité.

     `CView::OnFilePrintPreview` démarre le mode Aperçu avant impression en appelant la fonction d’assistance documenté `CView::DoPrintPreview`. `CView::DoPrintPreview` est le moteur principal de la boucle d’aperçu avant impression, tout comme `OnFilePrint` est le principal moteur pour la boucle d’impression.

     L’opération d’aperçu avant impression peut être personnalisée de plusieurs façons, en passant des paramètres différents pour `DoPrintPreview`. Reportez-vous à [technique Remarque 30](../mfc/tn030-customizing-printing-and-print-preview.md), qui décrit certains détails de l’aperçu avant impression et comment le personnaliser.

- ID_FILE_MRU_FILE1... FILE16 Une plage d’ID de commande pour les types de fichier du fichier **liste**.

     `CWinApp::OnUpdateRecentFileMenu` est un gestionnaire d’interface utilisateur de commande de mise à jour qui est l’une des utilisations plus avancées du mécanisme ON_UPDATE_COMMAND_UI. Dans votre ressource de menu, vous devez uniquement définir un élément de menu unique avec l’ID ID_FILE_MRU_FILE1. Cet élément de menu reste désactivé initialement.

     En tant que la liste des fichiers récents liste s’allonge, menu plus d’éléments sont ajoutés à la liste. La norme `CWinApp` implémentation par défaut est la limite standard des quatre fichiers récemment utilisés. Vous pouvez modifier la valeur par défaut en appelant `CWinApp::LoadStdProfileSettings` avec une valeur supérieure ou inférieure. La liste des derniers fichiers utilisés est stockée dans l’application. Fichier INI. La liste est chargée dans votre application `InitInstance` fonctionner si vous appelez `LoadStdProfileSettings`et est enregistré lorsque vous quittez l’application. Le Gestionnaire de l’interface utilisateur de commandes de mise à jour des derniers fichiers utilisés convertit également les chemins d’accès absolus aux chemins d’accès relatifs pour l’affichage dans le menu fichier.

     `CWinApp::OnOpenRecentFile` est le gestionnaire ON_COMMAND qui exécute la commande. Il obtient simplement le nom de fichier à partir de la liste des fichiers récents et les appels `CWinApp::OpenDocumentFile`, qui fait tout le travail de l’ouverture du fichier et la mise à jour la liste des derniers fichiers utilisés.

     Personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_EDIT_CLEAR efface la sélection actuelle

     Actuellement, il n’existe aucune implémentation standard de cette commande. Vous devez implémenter cela pour chaque `CView`-classe dérivée.

     `CEditView` Fournit une implémentation de cette commande à l’aide `CEdit::Clear`. La commande est désactivée si aucune sélection n’est en cours.

     Si vous choisissez d’implémenter cette commande, nous vous recommandons de qu'utiliser cet ID de commande.

- ID_EDIT_CLEAR_ALL efface la totalité du document.

     Actuellement, il n’existe aucune implémentation standard de cette commande. Vous devez implémenter cela pour chaque `CView`-classe dérivée.

     Si vous choisissez d’implémenter cette commande, nous vous recommandons de qu'utiliser cet ID de commande. Consultez l’exemple MFC didacticiel [SCRIBBLE](../visual-cpp-samples.md) pour un exemple d’implémentation.

- ID_EDIT_COPY copie la sélection actuelle dans le Presse-papiers.

     Actuellement, il n’existe aucune implémentation standard de cette commande. Vous devez implémenter cela pour chaque `CView`-classe dérivée.

     `CEditView` Fournit une implémentation de cette commande, qui copie le texte actuellement sélectionné dans le Presse-papiers en tant qu’à l’aide de CF_TEXT `CEdit::Copy`. La commande est désactivée si aucune sélection n’est en cours.

     Si vous choisissez d’implémenter cette commande, nous vous recommandons de qu'utiliser cet ID de commande.

- ID_EDIT_CUT coupe la sélection actuelle dans le Presse-papiers.

     Actuellement, il n’existe aucune implémentation standard de cette commande. Vous devez implémenter cela pour chaque `CView`-classe dérivée.

     `CEditView` Fournit une implémentation de cette commande, qui coupe le texte actuellement sélectionné dans le Presse-papiers en tant qu’à l’aide de CF_TEXT `CEdit::Cut`. La commande est désactivée si aucune sélection n’est en cours.

     Si vous choisissez d’implémenter cette commande, nous vous recommandons de qu'utiliser cet ID de commande.

- ID_EDIT_FIND commence l’opération de recherche, permet d’afficher la boîte de dialogue non modale find.

     Actuellement, il n’existe aucune implémentation standard de cette commande. Vous devez implémenter cela pour chaque `CView`-classe dérivée.

     `CEditView` Fournit une implémentation de cette commande, qui appelle la fonction d’assistance de mise en œuvre `OnEditFindReplace` à utiliser et stocker les paramètres précédents de rechercher/remplacer dans les variables de l’implémentation privée. Le `CFindReplaceDialog` classe est utilisée pour gérer la boîte de dialogue non modale pour inviter l’utilisateur.

     Si vous choisissez d’implémenter cette commande, nous vous recommandons de qu'utiliser cet ID de commande.

- ID_EDIT_PASTE insère le contenu actuel du Presse-papiers.

     Actuellement, il n’existe aucune implémentation standard de cette commande. Vous devez implémenter cela pour chaque `CView`-classe dérivée.

     `CEditView` Fournit une implémentation de cette commande, qui copie les données du Presse-papiers en cours, en remplaçant le texte sélectionné à l’aide `CEdit::Paste`. La commande est désactivée s’il existe aucune **CF_TEXT** dans le Presse-papiers.

     `COleClientDoc` fournit simplement un gestionnaire de l’interface utilisateur de commande de mise à jour pour cette commande. Si le Presse-papiers ne contient pas un élément OLE intégrable/objet, la commande sera désactivée. Vous êtes chargé d’écrire le gestionnaire pour la commande effectuer le collage réels. Si votre application OLE peut également coller les autres formats, vous devez fournir votre propre gestionnaire d’interface utilisateur de commande mise à jour dans votre document ou de vue (autrement dit, avant de quelque part `COleClientDoc` dans le routage de cible de commande).

     Si vous choisissez d’implémenter cette commande, nous vous recommandons de qu'utiliser cet ID de commande.

     Pour remplacer l’implémentation OLE standard, utilisez `COleClientItem::CanPaste`.

- ID_EDIT_PASTE_LINK insère un lien à partir du contenu du Presse-papiers en cours.

     Actuellement, il n’existe aucune implémentation standard de cette commande. Vous devez implémenter cela pour chaque `CView`-classe dérivée.

     `COleDocument` fournit simplement un gestionnaire de l’interface utilisateur de commande de mise à jour pour cette commande. Si le Presse-papiers ne contient pas d’élément/objet OLE pouvant être lié, la commande sera désactivée. Vous êtes chargé d’écrire le gestionnaire pour la commande effectuer le collage réels. Si votre application OLE peut également coller les autres formats, vous devez fournir votre propre gestionnaire d’interface utilisateur de commande mise à jour dans votre document ou de vue (autrement dit, avant de quelque part `COleDocument` dans le routage de cible de commande).

     Si vous choisissez d’implémenter cette commande, nous vous recommandons de qu'utiliser cet ID de commande.

     Pour remplacer l’implémentation OLE standard, utilisez `COleClientItem::CanPasteLink`.

- ID_EDIT_PASTE_SPECIAL insère le contenu actuel du Presse-papiers avec les options.

     Actuellement, il n’existe aucune implémentation standard de cette commande. Vous devez implémenter cela pour chaque `CView`-classe dérivée. MFC ne fournit pas de cette boîte de dialogue.

     Si vous choisissez d’implémenter cette commande, nous vous recommandons de qu'utiliser cet ID de commande.

- ID_EDIT_REPEAT répète la dernière opération.

     Actuellement, il n’existe aucune implémentation standard de cette commande. Vous devez implémenter cela pour chaque `CView`-classe dérivée.

     `CEditView` Fournit une implémentation de cette commande pour répéter la dernière opération de recherche. Les variables d’implémentation privée pour la dernière recherche sont utilisées. La commande est désactivée si une recherche ne peut pas être tentée.

     Si vous choisissez d’implémenter cette commande, nous vous recommandons de qu'utiliser cet ID de commande.

- ID_EDIT_REPLACE commence l’opération de remplacement, permet d’afficher la boîte de dialogue non modale à remplacer.

     Actuellement, il n’existe aucune implémentation standard de cette commande. Vous devez implémenter cela pour chaque `CView`-classe dérivée.

     `CEditView` Fournit une implémentation de cette commande, qui appelle la fonction d’assistance de mise en œuvre `OnEditFindReplace` à utiliser et stocker les paramètres précédents de rechercher/remplacer dans les variables de l’implémentation privée. Le `CFindReplaceDialog` classe est utilisée pour gérer la boîte de dialogue non modale qui invite l’utilisateur.

     Si vous choisissez d’implémenter cette commande, nous vous recommandons de qu'utiliser cet ID de commande.

- ID_EDIT_SELECT_ALL sélectionne l’intégralité du document.

     Actuellement, il n’existe aucune implémentation standard de cette commande. Vous devez implémenter cela pour chaque `CView`-classe dérivée.

     `CEditView` Fournit une implémentation de cette commande, qui sélectionne tout le texte dans le document. La commande est désactivée s’il n’existe aucun texte à sélectionner.

     Si vous choisissez d’implémenter cette commande, nous vous recommandons de qu'utiliser cet ID de commande.

- ID_EDIT_UNDO annule la dernière opération.

     Actuellement, il n’existe aucune implémentation standard de cette commande. Vous devez implémenter cela pour chaque `CView`-classe dérivée.

     `CEditView` Fournit une implémentation de cette commande, à l’aide de `CEdit::Undo`. La commande est désactivée si `CEdit::CanUndo` retourne FALSE.

     Si vous choisissez d’implémenter cette commande, nous vous recommandons de qu'utiliser cet ID de commande.

- ID_EDIT_REDO rétablit la dernière opération.

     Actuellement, il n’existe aucune implémentation standard de cette commande. Vous devez implémenter cela pour chaque `CView`-classe dérivée.

     Si vous choisissez d’implémenter cette commande, nous vous recommandons de qu'utiliser cet ID de commande.

- ID_WINDOW_NEW ouvre une autre fenêtre dans le document actif.

     `CMDIFrameWnd::OnWindowNew` implémente cette fonctionnalité puissante en utilisant le modèle de document du document actif pour créer un autre frame contenant une autre vue du document actif.

     Comme la plupart des plusieurs documents MDI (interface) commandes du menu Fenêtre, la commande est désactivée s’il n’existe aucune fenêtre MDI enfant active.

     Personnalisation de ce gestionnaire de commandes n’est pas recommandée. Si vous souhaitez fournir une commande qui crée des vues supplémentaires ou des fenêtres frame, vous serez probablement préférable d’inventer vos propres commandes. Vous pouvez cloner le code à partir de `CMDIFrameWnd::OnWindowNew` et modifiez-le pour les frame et affichage des classes spécifiques de votre choix.

- ID_WINDOW_ARRANGE réorganise les icônes au bas d’une fenêtre MDI.

     `CMDIFrameWnd` implémente cette commande MDI standard dans une fonction d’assistance de mise en œuvre `OnMDIWindowCmd`. Ce programme d’assistance mappe des ID de commande pour les messages MDI Windows et peut par conséquent partagent une grande quantité de code.

     Comme la plupart des commandes de menu Fenêtre MDI, la commande est désactivée s’il n’existe aucune fenêtre MDI enfant active.

     Personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- Windows ID_WINDOW_CASCADE Cascades afin qu’elles se chevauchent.

     `CMDIFrameWnd` implémente cette commande MDI standard dans une fonction d’assistance de mise en œuvre `OnMDIWindowCmd`. Ce programme d’assistance mappe des ID de commande pour les messages MDI Windows et peut par conséquent partagent une grande quantité de code.

     Comme la plupart des commandes de menu Fenêtre MDI, la commande est désactivée s’il n’existe aucune fenêtre MDI enfant active.

     Personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- Windows de vignettes de ID_WINDOW_TILE_HORZ horizontalement.

     Cette commande est implémentée dans `CMDIFrameWnd` comme ID_WINDOW_CASCADE, sauf un autre message MDI Windows est utilisé pour l’opération.

     Vous devez choisir l’orientation de mosaïque par défaut pour votre application. Pour cela, en modifiant l’ID de l’élément de menu Fenêtre « Vignette » à ID_WINDOW_TILE_HORZ ou ID_WINDOW_TILE_VERT.

- Windows de vignettes de ID_WINDOW_TILE_VERT verticalement.

     Cette commande est implémentée dans `CMDIFrameWnd` comme ID_WINDOW_CASCADE, sauf un autre message MDI Windows est utilisé pour l’opération.

     Vous devez choisir l’orientation de mosaïque par défaut pour votre application. Pour cela, en modifiant l’ID de l’élément de menu Fenêtre « Vignette » à ID_WINDOW_TILE_HORZ ou ID_WINDOW_TILE_VERT.

- Interface ID_WINDOW_SPLIT clavier à séparateur.

     `CView` gère cette commande pour le `CSplitterWnd` implémentation. Si la vue fait partie d’une fenêtre fractionnée, cette commande délègue à la fonction de mise en œuvre `CSplitterWnd::DoKeyboardSplit`. Cela place le séparateur dans un mode qui permettra aux utilisateurs de clavier fractionner ou une fenêtre fractionnée d’annuler le fractionnement.

     Cette commande est désactivée si la vue n’est pas un séparateur.

     Personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_APP_ABOUT appelle la boîte de dialogue About.

     Il n’existe aucune implémentation standard de la boîte à propos d’une application. L’application créée par AppWizard de par défaut crée une classe de boîte de dialogue personnalisée pour votre application et utilisez-le comme votre boîte à propos. AppWizard écrira également le Gestionnaire de commandes de base qui gère cette commande et appelle la boîte de dialogue.

     Vous implémenterez presque toujours cette commande.

- ID_APP_EXIT quitter l’application.

     `CWinApp::OnAppExit` gère cette commande en envoyant un message WM_CLOSE à la fenêtre principale de l’application. La norme en cours d’arrêt de l’application (invite pour les fichiers modifiés et ainsi de suite) est gérée par le `CFrameWnd` implémentation.

     Personnalisation de ce gestionnaire de commandes n’est pas recommandée. Substitution de `CWinApp::SaveAllModified` ou `CFrameWnd` est recommandée de la logique de fermeture.

     Si vous choisissez d’implémenter cette commande, nous vous recommandons de qu'utiliser cet ID de commande.

- ID_HELP_INDEX répertorie aide à partir de. Fichier HLP.

    > [!NOTE]
    >  Vous devez vous connecter cette option pour votre `CWinApp`-dérivée de table des messages de la classe pour activer cette fonctionnalité.

     `CWinApp::OnHelpIndex` gère cette commande en appelant de façon triviale `CWinApp::WinHelp`.

     Personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_HELP_USING affiche l’aide sur la façon d’utiliser l’aide.

    > [!NOTE]
    >  Vous devez vous connecter cette option pour votre `CWinApp`-dérivée de table des messages de la classe pour activer cette fonctionnalité.

     `CWinApp::OnHelpUsing` gère cette commande en appelant de façon triviale `CWinApp::WinHelp`.

     Personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- Mode d’aide ID_CONTEXT_HELP passe MAJ-F1.

    > [!NOTE]
    >  Vous devez vous connecter cette option pour votre `CWinApp`-dérivée de table des messages de la classe pour activer cette fonctionnalité.

     `CWinApp::OnContextHelp` gère cette commande en définissant le curseur de mode d’aide, en entrant une boucle modale d’et en attente de l’utilisateur de sélectionner une fenêtre pour obtenir de l’aide. Reportez-vous à [Note technique 28](../mfc/tn028-context-sensitive-help-support.md) pour plus d’informations sur l’implémentation de l’aide de MFC.

     Personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_HELP offre une aide sur le contexte actuel

    > [!NOTE]
    >  Vous devez vous connecter cette option pour votre `CWinApp`-dérivée de table des messages de la classe pour activer cette fonctionnalité.

     `CWinApp::OnHelp` gère cette commande en obtenant le contexte d’aide adéquate pour le contexte d’application actuel. Cela gère la touche F1 simple, aide sur les boîtes de message et ainsi de suite. Reportez-vous à [Note technique 28](../mfc/tn028-context-sensitive-help-support.md) pour plus d’informations sur la bibliothèque MFC aident à l’implémentation.

     Personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_DEFAULT_HELP affiche l’aide de valeur par défaut pour le contexte

    > [!NOTE]
    >  Vous devez vous connecter cette option pour votre `CWinApp`-dérivée de table des messages de la classe pour activer cette fonctionnalité.

     Cette commande est généralement mappée à `CWinApp::OnHelpIndex`.

     Un gestionnaire de commandes différent peut être fourni si vous le souhaitez une distinction entre aide par défaut et l’index d’aide.

- ID_NEXT_PANE accède au volet suivant

     `CView` gère cette commande pour le `CSplitterWnd` implémentation. Si la vue fait partie d’une fenêtre fractionnée, cette commande délègue à la fonction de mise en œuvre `CSplitterWnd::OnNextPaneCmd`. Cela déplacera la vue active dans le volet suivant de l’outil de fractionnement.

     Cette commande est désactivée si la vue n’est pas un séparateur ou il n’existe aucun volet suivant pour accéder à.

     Personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_PREV_PANE accède à volet précédent

     `CView` gère cette commande pour le `CSplitterWnd` implémentation. Si la vue fait partie d’une fenêtre fractionnée, cette commande délègue à la fonction de mise en œuvre `CSplitterWnd::OnNextPaneCmd`. Cela déplacera la vue active vers le volet précédent dans l’outil de fractionnement.

     Cette commande est désactivée si la vue n’est pas un séparateur ou il n’existe aucun volet précédent pour accéder à.

     Personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_OLE_INSERT_NEW insère un nouvel objet OLE

     Actuellement, il n’existe aucune implémentation standard de cette commande. Vous devez implémenter cela pour votre `CView`-dérivée de classe pour insérer un nouvel élément/objet OLE à la sélection actuelle.

     Toutes les applications clientes OLE doivent implémenter cette commande. AppWizard, avec l’option OLE, créera une implémentation squelette de `OnInsertObject` dans votre classe d’affichage d’avoir à effectuer.

     Consultez l’exemple OLE MFC [OCLIENT](../visual-cpp-samples.md) exemple pour une implémentation complète de cette commande.

- ID_OLE_EDIT_LINKS modifie les liaisons OLE

     `COleDocument` gère cette commande à l’aide de l’implémentation fournie par MFC et de la boîte de dialogue de liens OLE standard. L’implémentation de cette boîte de dialogue est accessible via la `COleLinksDialog` classe. Si le document actif ne contient pas tous les liens, la commande est désactivée.

     Personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_OLE_VERB_FIRST... DERNIÈRE plage un ID pour les verbes OLE

     `COleDocument` utilise cette plage d’ID de commande pour les verbes pris en charge par l’élément/objet OLE actuellement sélectionné. Cela doit être une plage dans la mesure où un type d’élément ou un objet OLE donné peut prendre en charge de zéro ou plusieurs verbes personnalisés. Dans le menu de votre application, vous devez disposer d’un élément de menu avec l’ID de ID_OLE_VERB_FIRST. Lorsque le programme est exécuté, le menu sera mis à jour avec la description du verbe menu approprié (ou le menu contextuel avec le nombre de verbes). La gestion du menu OLE est gérée par `AfxOleSetEditMenu`, terminé dans le Gestionnaire de l’interface utilisateur de commande de mise à jour pour cette commande.

     Aucun gestionnaire n’est explicite de commandes pour gérer chacun de l’ID de commande dans cette plage. `COleDocument::OnCmdMsg` est remplacée pour intercepter tous les ID de commande dans cette plage, de les transformer en nombres de verbe de base zéro et de lancer le serveur pour ce verbe (à l’aide de `COleClientItem::DoVerb`).

     Personnalisation ou autre utilisation de cette plage d’ID de commande n’est pas recommandée.

- ID_VIEW_TOOLBAR Active ou désactive la barre d’outils et désactiver

     `CFrameWnd` gère cette commande et le Gestionnaire de l’interface utilisateur de commande de mise à jour pour basculer l’état visible de la barre d’outils. La barre d’outils doit être une fenêtre enfant du frame de fenêtre enfant ID de AFX_IDW_TOOLBAR. Le Gestionnaire de commandes fait en fait bascule la visibilité de la fenêtre de la barre d’outils. `CFrameWnd::RecalcLayout` permet de redessiner la fenêtre frame avec la barre d’outils dans son nouvel état. Le Gestionnaire de l’interface utilisateur de commande de mise à jour vérifie l’élément de menu lorsque la barre d’outils est visible.

     Personnalisation de ce gestionnaire de commandes n’est pas recommandée. Si vous souhaitez ajouter des barres d’outils supplémentaires, vous devez cloner et modifier le Gestionnaire de commandes et le Gestionnaire de l’interface utilisateur de commande de mise à jour pour cette commande.

- ID_VIEW_STATUS_BAR Active ou désactive la barre d’état et désactiver

     Cette commande est implémentée dans `CFrameWnd` comme ID_VIEW_TOOLBAR, à l’exception d’une fenêtre enfant différents ID (AFX_IDW_STATUS_BAR) est utilisé.

## <a name="update-only-command-handlers"></a>Gestionnaires de commandes de mise à jour uniquement

Plusieurs ID de commande standard sont utilisés comme indicateurs dans les barres d’état. Ces utilisent le même l’interface utilisateur de commande de mise à jour de mécanisme de gestion pour afficher leur état visuel en cours pendant l’inactivité de l’application. Dans la mesure où ils ne peuvent pas être sélectionnés par l’utilisateur (autrement dit, vous ne pouvez pas envoyer d’un volet de barre d’état), puis il est inutile d’avoir un gestionnaire ON_COMMAND pour ces ID de commande.

- ID_INDICATOR_CAPS : Indicateur de verrou CAP.

- ID_INDICATOR_NUM : Indicateur de verrou (pavé numérique).

- ID_INDICATOR_SCRL : Indicateur de verrou défil.

- ID_INDICATOR_KANA : Indicateur de verrou KANA (applicable uniquement aux systèmes japonais).

Ces trois sont implémentées dans `CFrameWnd::OnUpdateKeyIndicator`, une application d’assistance de mise en œuvre qui utilise l’ID de commande pour mapper à la touche virtuelle appropriée. Une implémentation commune Active ou désactive (pour les volets de l’état désactivés ne = aucun texte) le `CCmdUI` objet selon si la touche virtuelle appropriée est actuellement verrouillée.

Personnalisation de ce gestionnaire de commandes n’est pas recommandée.

- ID_INDICATOR_EXT : Étendu sélectionner un indicateur.

- ID_INDICATOR_OVR : Indicateur de mode Refrappe.

- ID_INDICATOR_REC : Indicateur d’enregistrement.

Actuellement, il n’existe aucune implémentation standard de ces indicateurs.

Si vous choisissez d’implémenter ces indicateurs, nous vous recommandons d’utiliser ces ID d’indicateur et de maintenir l’ordre des indicateurs dans votre barre d’état (autrement dit, dans cet ordre : EXT, extrémité, NUM, défil, RFP, REC).

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

