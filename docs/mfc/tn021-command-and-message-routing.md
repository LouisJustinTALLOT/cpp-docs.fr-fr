---
title: 'TN021 : Commandes et routage des messages | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.routing
dev_langs:
- C++
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a1061f4a7d4394cb84c26514795c406f78146df
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384948"
---
# <a name="tn021-command-and-message-routing"></a>TN021 : Routage des commandes et des messages
> [!NOTE]
>  La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.  
  
 Cette note décrit l’architecture de routage et la distribution de commande, ainsi que les rubriques avancées dans le routage des messages de fenêtre Général.  
  
 Veuillez font référence à Visual C++ pour des informations détaillées sur les architectures décrites ici, en particulier la distinction entre les messages, les notifications de contrôle et les commandes Windows. Cette note suppose que vous maîtrisez les problèmes décrits dans la documentation et traite uniquement des sujets très avancés.  
  
## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>Routage des commandes et la distribution MFC 1.0 fonctionnalité évolue à MFC 2.0 Architecture  
 Windows offre la **WM_COMMAND** message qui est surchargée pour fournir des notifications de commandes de menu, les touches d’accès et les notifications de contrôle de boîte de dialogue.  
  
 1.0 de MFC créées sur ce petit en permettant à un gestionnaire de commandes (par exemple, « OnFileNew ») un **CWnd** classe appel en réponse à une spécifique dérivée **WM_COMMAND**. Cela est collé avec une structure de données appelée la table des messages et entraîne un mécanisme de commande très faible.  
  
 MFC 1.0 également des fonctionnalités supplémentaires pour la séparation des notifications de contrôle à partir des messages de commande. Commandes sont représentées par un ID de 16 bits, parfois appelé un ID de commande. Commandes normalement démarrent un **CFrameWnd** (autrement dit, une sélection de menu ou un accélérateur traduit) et seront acheminés vers plusieurs autres fenêtres.  
  
 MFC 1.0 utilisé le routage des commandes dans un sens limité pour l’implémentation de plusieurs documents MDI (Interface). (Une fenêtre frame MDI déléguer des commandes à sa fenêtre enfant MDI active.)  
  
 Cette fonctionnalité a été généralisée et étendue dans MFC version 2.0 pour autoriser les commandes d’être gérés par un large éventail d’objets (pas seulement les objets de fenêtre). Il fournit une plus formels et une architecture extensible pour le routage des messages et réutilise le routage de cible de commande pour non seulement la gestion des commandes, mais également pour mettre à jour des objets d’interface utilisateur (par exemple, les éléments de menu et boutons de barre d’outils) afin de refléter la disponibilité actuelle d’une commande .  
  
## <a name="command-ids"></a>ID de commande  
 Pour obtenir une explication de la commande de routage et le processus de liaison, consultez Visual C++. [Technical Note 20](../mfc/tn020-id-naming-and-numbering-conventions.md) contient des informations sur l’ID d’affectation de noms.  
  
 Nous utilisons le préfixe générique « ID_ » pour l’ID de commande. ID de commande sont > = 0 x 8000. La barre d’état ou de la ligne de message affiche la chaîne de description de commande s’il existe une ressource STRINGTABLE avec les mêmes ID que l’ID de commande.  
  
 Dans les ressources de votre application, une commande QU'ID peut apparaît dans plusieurs emplacements :  
  
-   Dans une seule ressource STRINGTABLE ayant le même ID que l’invite de ligne de message.  
  
-   Dans éventuellement plusieurs ressources de MENU qui sont joints aux éléments de menu qui font appel à la même commande.  
  
-   (Avancé) dans un bouton de la boîte de dialogue pour une commande GOSUB.  
  
 Dans le code source de votre application, une commande QU'ID peut apparaît dans plusieurs emplacements :  
  
-   Dans votre ressource. H (ou autre fichier d’en-tête de symbole principal) pour définir l’ID de commande spécifiques à l’application.  
  
-   PEUT-être dans un tableau d’ID utilisé pour créer une barre d’outils.  
  
-   Dans un **ON_COMMAND** (macro).  
  
-   Par exemple, dans un **ON_UPDATE_COMMAND_UI** (macro).  
  
 Actuellement, la seule implémentation dans MFC qui requiert l’ID de commande être > = 0 x 8000 est l’implémentation de boîtes de dialogue GOSUB/commandes.  
  
## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>Commandes GOSUB, l’Architecture de commande dans les boîtes de dialogue  
 L’architecture de commande de routage et l’activation de commandes fonctionne bien avec les fenêtres frame, les éléments de menu, des boutons de barre d’outils, les boutons de barre de boîte de dialogue, autres barres de contrôles et autres éléments d’interface utilisateur conçues pour mettre à jour sur les commandes à la demande et d’itinéraire, ou ID de contrôle pour un principal cible de la commande (en général, la fenêtre frame principale). Cette cible de commande principal peut acheminer les notifications de commande ou le contrôle à d’autres objets cibles de commande comme il convient.  
  
 Une boîte de dialogue (modale ou non) peut tirer parti de certaines des fonctionnalités de l’architecture de la commande si vous affectez l’ID de contrôle du contrôle de boîte de dialogue à l’ID de commande appropriée. Prise en charge pour les boîtes de dialogue n’est pas automatique, il se peut que vous deviez écrire du code supplémentaire.  
  
 Notez que, pour toutes ces fonctionnalités fonctionnent correctement, votre ID de commande doivent être > = 0 x 8000. Depuis de nombreuses boîtes de dialogue Impossible seront acheminés vers la même image, les commandes partagés doivent être > = 0 x 8000, alors que les IDCs non partagées dans une boîte de dialogue spécifique doivent être < = 0x7FFF.  
  
 Vous pouvez placer un bouton normal dans une boîte de dialogue modale normal avec le IDC du bouton Définir à l’ID de commande appropriée. Lorsque l’utilisateur sélectionne le bouton, le propriétaire de la boîte de dialogue (généralement la fenêtre frame principale) Obtient la commande comme n’importe quelle autre commande. Cela s’appelle une commande GOSUB, car il est généralement utilisé pour afficher une autre boîte de dialogue (un GOSUB de la première boîte de dialogue).  
  
 Vous pouvez également appeler la fonction **CWnd::UpdateDialogControls** dans votre boîte de dialogue et lui passer l’adresse de votre fenêtre frame principale. Cette fonction active ou désactive votre selon qu’ils aient des gestionnaires de commandes dans le cadre des contrôles de boîte de dialogue. Cette fonction est appelée automatiquement pour vous pour les barres de contrôle dans la boucle inactive de votre application, mais vous devez l’appeler directement pour les boîtes de dialogue normales que vous souhaitez que cette fonctionnalité.  
  
## <a name="when-onupdatecommandui-is-called"></a>Lorsque ON_UPDATE_COMMAND_UI est appelée  
 Maintenir l’état activé/activé de tous le programme éléments de menu de tout le temps peut poser un problème de ressources de calcul. Une technique courante consiste à activer/vérification des éléments de menu uniquement lorsque l’utilisateur sélectionne la fenêtre contextuelle. L’implémentation MFC 2.0 de **CFrameWnd** gère le **WM_INITMENUPOPUP** le message et utilise l’architecture de routage de commande pour déterminer les États des menus par le biais de **ON_UPDATE_COMMAND_ L’interface utilisateur** gestionnaires.  
  
 **CFrameWnd** gère également le **WM_ENTERIDLE** message pour décrire l’actuel élément du menu sélectionné sur l’état de la barre (également connu sous la ligne de message).  
  
 Structure de menu d’une application et modifié par Visual C++, est utilisé pour représenter des commandes potentielles disponibles au **WM_INITMENUPOPUP** heure. **ON_UPDATE_COMMAND_UI** gestionnaires peuvent modifier l’état ou le texte d’un menu ou pour des utilisations avancées (telles que la liste des derniers fichiers utilisés du fichier ou le menu déroulant des verbes OLE), modifiez réellement la structure de menu avant le menu est dessiné.  
  
 Le même type de **ON_UPDATE_COMMAND_UI** traitement est effectué pour les barres d’outils (et les autres barres de contrôles) lorsque l’application passe à la boucle inactive. Consultez le *Class Library Reference* et [Technical Note 31](../mfc/tn031-control-bars.md) pour plus d’informations sur les barres de contrôles.  
  
## <a name="nested-pop-up-menus"></a>Menus contextuels imbriqués  
 Si vous utilisez une structure imbriquée, vous remarquerez que la **ON_UPDATE_COMMAND_UI** gestionnaire pour le premier élément de menu dans le menu contextuel est appelé dans les deux cas.  
  
 Tout d’abord, elle est appelée pour le menu contextuel lui-même. Cela est nécessaire, car les menus contextuels n’ont pas d’ID et nous utilisons l’ID du premier élément de menu du menu contextuel pour faire référence à l’intégralité du menu contextuel. Dans ce cas, le **m_pSubMenu** variable membre de la **CCmdUI** objet sera non NULL et qu’il pointe vers le menu contextuel.  
  
 En second lieu, elle est appelée juste avant que les éléments de menu dans le menu contextuel sont à dessiner. Dans ce cas, l’ID fait référence uniquement pour le premier élément de menu et le **m_pSubMenu** variable membre de la **CCmdUI** objet seront NULL.  
  
 Cela vous permet d’activer le menu contextuel distinct à partir de ses éléments de menu, mais nécessite que vous écrivez du code prenant en charge de menu. Par exemple, dans un menu imbriqué avec la structure suivante :  
  
```  
File>  
    New> 
    Sheet (ID_NEW_SHEET)  
    Chart (ID_NEW_CHART)  
```  
  
 Les commandes ID_NEW_SHEET et ID_NEW_CHART peuvent être activées ou désactivées indépendamment. Le **nouveau** menu contextuel doit être activé si une des deux est activée.  
  
 Le Gestionnaire de commandes pour ID_NEW_SHEET (la première commande de la fenêtre contextuelle) ressemblerait à :  
  
```  
void CMyApp::OnUpdateNewSheet(CCmdUI* pCmdUI)  
{  
    if (pCmdUI->m_pSubMenu != NULL)  
 { *// enable entire pop-up for "New" sheet and chart  
    BOOL bEnable = m_bCanCreateSheet || m_bCanCreateChart;  
 *// CCmdUI::Enable is a no-op for this case,
    so we *//   must do what it would have done.  
    pCmdUI->m_pMenu->EnableMenuItem(pCmdUI->m_nIndex, 
    MF_BYPOSITION |   
 (bEnable  MF_ENABLED : (MF_DISABLED | MF_GRAYED)));

    return; 
 } *// otherwise just the New Sheet command  
    pCmdUI->Enable(m_bCanCreateSheet);

} 
```  
  
 Le Gestionnaire de commandes pour ID_NEW_CHART serait un gestionnaire de commandes de mise à jour normale et une apparence quelque chose comme :  
  
```  
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)  
{  
    pCmdUI->Enable(m_bCanCreateChart);

} 
```  
  
## <a name="oncommand-and-onbnclicked"></a>ON_COMMAND et ON_BN_CLICKED  
 Les macros de mappage de message pour **ON_COMMAND** et **ON_BN_CLICKED** sont les mêmes. Le contrôle et commande notification routage mécanisme MFC utilise uniquement l’ID de commande pour déterminer où acheminer vers. Contrôler les notifications avec le code de notification de contrôle de zéro (**BN_CLICKED**) sont interprétés comme des commandes.  
  
> [!NOTE]
>  En fait, tous les messages de notification de contrôle passent par la chaîne de gestionnaire de commandes. Par exemple, il est techniquement possible d’écrire un gestionnaire de notification de contrôle pour **EN_CHANGE** dans votre classe de document. Cela n’est pas généralement recommandé, car les applications pratiques de cette fonctionnalité sont peu nombreuses, la fonctionnalité n’est pas pris en charge par ClassWizard et utilisation de la fonctionnalité peut entraîner de code fragile.  
  
## <a name="disabling-the-automatic-disabling-of-button-controls"></a>La désactivation de la désactivation automatique de contrôles de bouton  
 Si vous placez un contrôle de bouton sur une barre de boîte de dialogue, ou dans une boîte de dialogue où vous appelez **CWnd::UpdateDialogControls** vous-même, vous pouvez remarquer que les boutons qui n’ont pas **ON_COMMAND** ou **ON_UPDATE_COMMAND_UI** gestionnaires seront automatiquement désactivées pour vous par l’infrastructure. Dans certains cas, vous ne devrez pas avoir un gestionnaire, mais vous pouvez le bouton rester activé. Le moyen le plus simple d’effectuer cette opération consiste à ajouter un gestionnaire de commandes factice (facile avec ClassWizard) et ne rien faire qu’elle contient.  
  
## <a name="window-message-routing"></a>Routage des messages de fenêtre  
 La liste suivante décrit certaines rubriques plus avancées sur les classes MFC et le routage des messages de Windows et d’autres rubriques impact sur les. Les informations ici ne sont que brièvement décrites. Reportez-vous à la *Class Library Reference* pour plus d’informations sur les API publiques. Consultez le code source de la bibliothèque MFC pour plus d’informations sur les détails d’implémentation.  
  
 Reportez-vous à [Technical Note 17](../mfc/tn017-destroying-window-objects.md) pour plus d’informations sur le nettoyage de la fenêtre, une rubrique très importante pour tous les **CWnd**-classes dérivées.  
  
## <a name="cwnd-issues"></a>Problèmes de CWnd  
 La fonction de membre d’implémentation **CWnd::OnChildNotify** fournit une architecture puissante et extensible pour les fenêtres enfants (également appelés contrôles) raccorder ou sinon d’être informé sur les messages, les commandes et contrôle notifications qui mènent à leur parent (ou « propriétaire »). Si la fenêtre enfant (/ contrôle) est C++ **CWnd** de l’objet lui-même, la fonction virtuelle **OnChildNotify** est d’abord appelée avec les paramètres du message d’origine (autrement dit, un **MSG**structure). La fenêtre enfant peut ignorer le message, mange ou modifiez le message pour le parent (rare).  
  
 La valeur par défaut **CWnd** implémentation gère les messages suivants et utilise le **OnChildNotify** raccordement pour permettre à enfant windows (contrôles) pour le premier accès au message :  
  
- **WM_MEASUREITEM** et **WM_DRAWITEM** (de dessin automatique)  
  
- **WM_COMPAREITEM** et **WM_DELETEITEM** (de dessin automatique)  
  
- **Messages WM_HSCROLL** et **WM_VSCROLL**  
  
- **WM_CTLCOLOR**  
  
- **WM_PARENTNOTIFY**  
  
 Vous pouvez remarquer la **OnChildNotify** raccordement est utilisée pour modifier les messages owner-draw dans les messages de dessin automatique.  
  
 Outre la **OnChildNotify** raccordement, messages de défilement ont le comportement de routage. Reportez-vous ci-dessous pour plus d’informations sur les barres de défilement et des sources de **messages WM_HSCROLL** et **WM_VSCROLL** messages.  
  
## <a name="cframewnd-issues"></a>Problèmes de CFrameWnd  
 Le **CFrameWnd** classe fournit la majeure partie de l’interface utilisateur et routage des commandes mise à jour de la mise en œuvre. Cela est principalement utilisé pour la fenêtre frame principale de l’application (**CWinApp::m_pMainWnd**), mais s’applique à toutes les fenêtres frame.  
  
 La fenêtre frame principale est la fenêtre de la barre de menus et est le parent de la barre d’état ou de la ligne de message. Reportez-vous à la discussion ci-dessus sur le routage des commandes et **WM_INITMENUPOPUP.**  
  
 Le **CFrameWnd** classe assure la gestion de la vue active. Les messages suivants sont routées via la vue active :  
  
-   Tous les messages de commande (la vue active obtient le premier accès à ceux-ci).  
  
- **Messages WM_HSCROLL** et **WM_VSCROLL** (voir ci-dessous) de barres de défilement de messages à partir de frère.  
  
- **WM_ACTIVATE** (et **WM_MDIACTIVATE** pour MDI) obtenir transformée en appels à la fonction virtuelle **CView::OnActivateView**.  
  
## <a name="cmdiframewndcmdichildwnd-issues"></a>Problèmes de CMDIFrameWnd/CMDIChildWnd  
 Les deux classes de fenêtre frame MDI dérivent **CFrameWnd** et par conséquent sont toutes deux activées pour le même type de routage des commandes et la mise à jour de l’interface utilisateur fourni dans **CFrameWnd**. Dans une application MDI classique, seule la fenêtre frame principale (autrement dit, le **CMDIFrameWnd** objet) contient la barre de menus et la barre d’état et par conséquent, est la principale source de l’implémentation de routage de commande.  
  
 Le modèle de routage général est que la fenêtre enfant MDI active obtient le premier accès aux commandes. La valeur par défaut **PreTranslateMessage** fonctions gèrent les tables d’accélérateurs pour les deux fenêtres MDI enfants (premier) et le frame MDI (seconde), ainsi que les accélérateurs de commande du système standards MDI normalement gérés par  **TranslateMDISysAccel** (dernière).  
  
## <a name="scroll-bar-issues"></a>Problèmes de la barre de défilement  
 Lors du traitement de message de défilement (**messages WM_HSCROLL**/**OnHScroll** et/ou **WM_VSCROLL**/**OnVScroll**), vous devez essayer d’écrire le code du gestionnaire afin qu’il ne s’appuie pas sur d'où provenance le message de barre de défilement. Il s’agit pas uniquement un problème Windows général, étant donné que les messages de défilement peuvent provenir de défilement true ou à partir de contrôles de barre **WS_HSCROLL**/**WS_VSCROLL** barres qui ne sont pas des contrôles de barre de défilement de défilement.  
  
 MFC s’étend à autoriser pour les contrôles de barre de défilement enfants ou frères de la fenêtre en cours de défilement (en fait, la relation parent/enfant entre la barre de défilement et de la fenêtre en cours de défilement peut être rien). Cela est particulièrement important pour les barres de défilement partagé avec les fenêtres fractionnées. Reportez-vous à [Technical Note 29](../mfc/tn029-splitter-windows.md) pour plus d’informations sur l’implémentation de **CSplitterWnd** incluant davantage d’informations sur partagé des problèmes de barre de défilement.  
  
 Sur une note rapide, il y a deux **CWnd** où les styles de barre de défilement spécifiées à la création de classes dérivées sont interceptées et pas passés à Windows. Lorsqu’il est passé à une routine de création, **WS_HSCROLL** et **WS_VSCROLL** peut être défini indépendamment, mais après la création ne peut pas être modifiée. Bien entendu, vous devez tester pas directement ou définir les bits de style WS_SCROLL de la fenêtre qu’ils ont créés.  
  
 Pour **CMDIFrameWnd** les styles de barre de défilement vous passez dans **créer** ou **LoadFrame** sont utilisées pour créer le MDICLIENT. Si vous souhaitez avoir une zone MDICLIENT avec défilement (tels que le Gestionnaire de programmes Windows) veillez à définir à la fois la barre de défilement styles (**WS_HSCROLL** &#124; **WS_VSCROLL**) pour le style utilisé pour créer le **CMDIFrameWnd**.  
  
 Pour **CSplitterWnd** les styles de barre de défilement s’appliquent aux barres de défilement de partagée spéciale pour les régions de séparateur. Pour les fenêtres fractionnées statiques, vous allez normalement pas définir un style de barre de défilement. Pour les fenêtres fractionnées dynamiques, vous devez généralement la style défini pour la direction que vous allez fractionner, autrement dit, la barre de défilement **WS_HSCROLL** si vous pouvez répartir des lignes, **WS_VSCROLL** si vous pouvez fractionner des colonnes.  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

