---
title: 'TN021 : Commande et le routage des messages'
ms.date: 06/28/2018
f1_keywords:
- vc.routing
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
ms.openlocfilehash: ce8aa2013c8f2f351ca1028f0d6103135ba5ecd8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294393"
---
# <a name="tn021-command-and-message-routing"></a>TN021 : Commande et le routage des messages

> [!NOTE]
>  La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit l’architecture de routage et de dispatch de commande, ainsi que les rubriques avancées dans le routage des messages de fenêtres générales.

Reportez-vous à Visual C++ pour des informations générales sur les architectures décrites ici, pour savoir en particulier la distinction entre les messages, les notifications de contrôle et les commandes Windows. Cette note suppose que vous maîtrisez les problèmes décrits dans la documentation imprimée et traite uniquement des rubriques très avancées.

## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>Fonctionnalités de routage des commandes et la distribution MFC 1.0 évoluent à MFC 2.0 Architecture

Windows a le message WM_COMMAND qui est surchargé pour envoyer des notifications des commandes de menu, des touches accélérateur et des notifications de contrôle de la boîte de dialogue.

MFC 1.0 créées sur ce petit en permettant à un gestionnaire de commandes (par exemple, « OnFileNew ») un `CWnd` appelée en réponse à une WM_COMMAND spécifique de classe dérivée. Cela est collé avec une structure de données appelée la table des messages et entraîne un mécanisme de commande très peu d’espace.

1.0 de MFC fournit également des fonctionnalités supplémentaires pour séparer les notifications de contrôle à partir des messages de commande. Commandes sont représentées par un ID de 16 bits, parfois appelé un ID de commande. Commandes démarrent normalement à partir d’un `CFrameWnd` (autrement dit, un menu, sélectionnez ou un accélérateur traduit) et sont acheminées vers diverses autres fenêtres.

MFC 1.0 utilisé le routage des commandes dans un sens limité pour l’implémentation de plusieurs documents MDI (Interface). (Une fenêtre frame MDI déléguer des commandes à sa fenêtre enfant MDI active.)

Cette fonctionnalité a été généralisée et étendue dans 2.0 MFC pour autoriser les commandes d’être gérés par un grand nombre d’objets (pas seulement les objets de fenêtre). Il fournit une plus formels et une architecture extensible pour le routage des messages et réutilise le routage de cible de commande pour gérer non seulement des commandes, mais également pour la mise à jour des objets d’interface utilisateur (par exemple, les éléments de menu et boutons de barre d’outils) afin de refléter la disponibilité actuelle d’une commande .

## <a name="command-ids"></a>ID de commande

Pour obtenir une explication de la commande de routage et le processus de liaison, consultez Visual C++. [Technical Note 20](../mfc/tn020-id-naming-and-numbering-conventions.md) contient des informations sur l’ID d’affectation de noms.

Nous utilisons le préfixe générique « ID_ » pour l’ID de commande. ID de commande sont > = 0 x 8000. La barre d’état ou de la ligne de message affiche la chaîne de description de commande s’il existe une ressource STRINGTABLE avec les mêmes ID que l’ID de commande.

Dans les ressources de votre application, une commande que peut ID apparaît dans plusieurs emplacements :

- Dans une seule ressource STRINGTABLE qui a le même ID que l’invite de ligne de message.

- Dans éventuellement plusieurs ressources de MENU qui sont joints aux éléments de menu qui appellent la même commande.

- (Avancé) dans un bouton de la boîte de dialogue pour une commande GOSUB.

Dans le code source de votre application, une commande que peut ID apparaît dans plusieurs emplacements :

- Dans votre ressource. H (ou autre fichier d’en-tête de symbole principal) pour définir l’ID de commande de spécifique à l’application.

- PEUT-être dans un tableau d’ID utilisé pour créer une barre d’outils.

- Dans un ON_COMMAND (macro).

- PEUT-être dans un ON_UPDATE_COMMAND_UI, macro.

Actuellement, la seule implémentation dans MFC qui requiert des ID de commande être > = 0 x 8000 est l’implémentation de boîtes de dialogue GOSUB/commandes.

## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>Commandes GOSUB, à l’aide d’Architecture de commande dans les boîtes de dialogue

L’architecture de la commande de routage et d’activer les commandes fonctionne bien avec les fenêtres frame, éléments de menu, des boutons de barre d’outils, les boutons de barre de boîte de dialogue, autres barres de contrôles et autres éléments d’interface utilisateur conçus pour mettre à jour sur les commandes à la demande et l’itinéraire ou ID de contrôle à un principal cible de commande (généralement la fenêtre frame principale). Cette cible de commande principal peut acheminer les notifications de commande ou le contrôle à d’autres objets de cible de commande comme il convient.

Une boîte de dialogue (modale ou non modale) permettre bénéficier de certaines des fonctionnalités de l’architecture de la commande si vous affectez l’ID de contrôle du contrôle de boîte de dialogue à l’ID de commande appropriée. Prise en charge des boîtes de dialogue n’est pas automatique, vous devrez peut-être écrire du code supplémentaire.

Notez que, pour toutes ces fonctionnalités fonctionnent correctement, votre ID de commande doit être > = 0 x 8000. Dans la mesure où les nombreuses boîtes de dialogue peut être dirigées vers la même image, commandes partagées doivent être > = 0 x 8000, alors que les IDCs non partagées dans une boîte de dialogue spécifique doivent être < = 0x7FFF.

Vous pouvez placer un bouton normal dans la boîte de dialogue modale normal avec l’IDC du bouton Définir à l’ID de commande appropriée. Lorsque l’utilisateur sélectionne le bouton, le propriétaire de la boîte de dialogue (généralement la fenêtre frame principale) Obtient la commande comme toute autre commande. Cela s’appelle une commande GOSUB, car il est généralement utilisé pour afficher une autre boîte de dialogue (un GOSUB de la première boîte de dialogue).

Vous pouvez également appeler la fonction `CWnd::UpdateDialogControls` dans votre boîte de dialogue et passez-lui l’adresse de votre fenêtre frame principale. Active ou désactive la vos contrôles de boîte de dialogue selon qu’ils aient des gestionnaires de commandes dans le cadre de cette fonction. Cette fonction est appelée automatiquement à votre place pour les barres de contrôle dans la boucle inactive de votre application, mais vous devez l’appeler directement pour des boîtes de dialogue normales que vous souhaitez avoir cette fonctionnalité.

## <a name="when-onupdatecommandui-is-called"></a>Lorsque ON_UPDATE_COMMAND_UI est appelée

Conserver l’état activé/vérifié de tous les du programme éléments de menu tout le temps peut être un problème de sollicite. Une technique courante consiste à/vérification de l’activation des éléments de menu uniquement lorsque l’utilisateur sélectionne la fenêtre contextuelle. L’implémentation MFC 2.0 de `CFrameWnd` gère le message WM_INITMENUPOPUP et utilise l’architecture de routage de commande pour déterminer les États des menus via les gestionnaires ON_UPDATE_COMMAND_UI.

`CFrameWnd` gère également le message WM_ENTERIDLE pour décrire l’élément sélectionné sur l’état de la barre (également connu sous la ligne de message) du menu en cours.

Structure du menu d’une application, modifié par Visual C++, est utilisé pour représenter les commandes potentiels disponibles au moment de WM_INITMENUPOPUP. Gestionnaires ON_UPDATE_COMMAND_UI peuvent modifier l’état ou le texte d’un menu ou pour les utilisations avancées (telles que la liste des fichiers récents du fichier ou le menu contextuel de verbes OLE), en fait modifier la structure de menu avant que le menu est dessiné.

Le même type de traitement de ON_UPDATE_COMMAND_UI est effectué pour les barres d’outils (et les autres barres de contrôles) lorsque l’application passe sa boucle inactive. Consultez le *Class Library Reference* et [Technical Note 31](../mfc/tn031-control-bars.md) pour plus d’informations sur les barres de contrôles.

## <a name="nested-pop-up-menus"></a>Menus contextuels imbriquées

Si vous utilisez une structure imbriquée, vous remarquerez que le gestionnaire ON_UPDATE_COMMAND_UI pour le premier élément de menu dans le menu contextuel est appelé dans les deux cas.

Tout d’abord, elle est appelée pour le menu contextuel lui-même. Cela est nécessaire, car les menus contextuels n’ont pas d’ID et nous utilisons l’ID du premier élément de menu du menu contextuel pour faire référence à l’intégralité du menu contextuel. Dans ce cas, le *m_pSubMenu* variable membre de la `CCmdUI` objet sera non NULL et qu’il pointe vers le menu contextuel.

Deuxièmement, il est appelé juste avant que les éléments de menu dans le menu contextuel sont le point d’être dessiné. Dans ce cas, l’ID fait référence uniquement pour le premier élément de menu et le *m_pSubMenu* variable membre de la `CCmdUI` objet seront NULL.

Cela vous permet d’activer le menu contextuel distinct à partir de ses éléments de menu, mais nécessite que vous écrivez du code prenant en charge de menu. Par exemple, dans un menu imbriqué avec la structure suivante :

```Output
File>
    New>
    Sheet (ID_NEW_SHEET)
    Chart (ID_NEW_CHART)
```

Les commandes ID_NEW_SHEET et ID_NEW_CHART peuvent être activées ou désactivées indépendamment. Le **New** menu contextuel doit être activée si une des deux est activée.

Le Gestionnaire de commandes pour ID_NEW_SHEET (la première commande dans la fenêtre contextuelle) ressemblent à :

```cpp
void CMyApp::OnUpdateNewSheet(CCmdUI* pCmdUI)
{
    if (pCmdUI->m_pSubMenu != NULL)
    {
        // enable entire pop-up for "New" sheet and chart
        BOOL bEnable = m_bCanCreateSheet || m_bCanCreateChart;
        // CCmdUI::Enable is a no-op for this case, so we
        // must do what it would have done.
        pCmdUI->m_pMenu->EnableMenuItem(pCmdUI->m_nIndex,
            MF_BYPOSITION |
            (bEnable  MF_ENABLED : (MF_DISABLED | MF_GRAYED)));

        return;
    }
    // otherwise just the New Sheet command
    pCmdUI->Enable(m_bCanCreateSheet);
}
```

Le Gestionnaire de commandes pour ID_NEW_CHART serait un gestionnaire de commandes de mise à jour normale et une apparence quelque chose comme :

```cpp
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)
{
    pCmdUI->Enable(m_bCanCreateChart);
}
```

## <a name="oncommand-and-onbnclicked"></a>ON_COMMAND et ON_BN_CLICKED

Les macros de mappage de message pour **ON_COMMAND** et **ON_BN_CLICKED** sont les mêmes. La commande et contrôle notification routage mécanisme MFC utilise uniquement l’ID de commande pour décider où acheminer vers. Contrôler les notifications envoyées avec le code de notification de contrôle de zéro (**BN_CLICKED**) sont interprétés comme des commandes.

> [!NOTE]
> En fait, tous les messages de notification de contrôle passent par la chaîne de gestionnaire de commandes. Par exemple, il est techniquement possible d’écrire un gestionnaire de notification de contrôle pour **EN_CHANGE** dans votre classe de document. Cela n’est pas généralement recommandé, car les applications pratiques de cette fonctionnalité sont peu nombreuses, la fonctionnalité n’est pas pris en charge par ClassWizard, et utilisation de la fonctionnalité peut produire un code fragile.

## <a name="disabling-the-automatic-disabling-of-button-controls"></a>La désactivation de la désactivation automatique de contrôles de bouton

Si vous placez un contrôle de bouton sur une barre de boîte de dialogue, ou dans une boîte de dialogue à l’aide de where que vous appelez **CWnd::UpdateDialogControls** vous-même, vous remarquerez que les boutons qui n’ont pas **ON_COMMAND** ou **ON_UPDATE_COMMAND_UI** gestionnaires seront automatiquement désactivés pour vous par l’infrastructure. Dans certains cas, vous ne devrez pas avoir un gestionnaire, mais vous pouvez le bouton reste activée. Le moyen le plus simple pour y parvenir consiste à ajouter un gestionnaire de commandes factice (facile à réaliser avec ClassWizard) et ne font rien qu’il contient.

## <a name="window-message-routing"></a>Routage des messages de fenêtre

La section suivante décrit certaines des rubriques plus avancées sur les classes MFC et le routage des messages Windows et autres sujets impact sur les. Les informations ici ne sont que brièvement décrites. Reportez-vous à la *Class Library Reference* pour plus d’informations sur les API publiques. Consultez le code source de la bibliothèque MFC pour plus d’informations sur les détails d’implémentation.

Reportez-vous à [technique Remarque 17](../mfc/tn017-destroying-window-objects.md) pour plus d’informations sur le nettoyage de la fenêtre, un sujet très important pour tous les **CWnd**-classes dérivées.

## <a name="cwnd-issues"></a>Problèmes de CWnd

La fonction de membre d’implémentation **CWnd::OnChildNotify** fournit une architecture puissante et extensible pour les fenêtres enfants (également appelés contrôles) raccorder ou sinon d’être informé des messages, les commandes et contrôle notifications qui mènent à son parent (ou « propriétaire »). Si la fenêtre enfant (contrôle /) est un C++ **CWnd** de l’objet lui-même, la fonction virtuelle **OnChildNotify** est appelée en premier avec les paramètres du message d’origine (autrement dit, un **MSG**structure). La fenêtre enfant peut ignorer le message, il manger ou modifier le message pour le parent (rare).

La valeur par défaut **CWnd** implémentation gère les messages suivants et utilise le **OnChildNotify** raccordement de permettre aux enfants windows (contrôles) pour le premier accès, le message :

- **WM_MEASUREITEM** et **WM_DRAWITEM** (de dessin automatique)

- **WM_COMPAREITEM** et **WM_DELETEITEM** (de dessin automatique)

- **Messages WM_HSCROLL** et **WM_VSCROLL**

- **WM_CTLCOLOR**

- **WM_PARENTNOTIFY**

Vous remarquerez le **OnChildNotify** raccordement est utilisée pour modifier les messages owner-draw en messages de dessin automatique.

Outre le **OnChildNotify** ont des messages de défilement raccordement, comportement le routage. Consultez les informations ci-dessous pour plus d’informations sur les barres de défilement et les sources de **messages WM_HSCROLL** et **WM_VSCROLL** messages.

## <a name="cframewnd-issues"></a>Problèmes de CFrameWnd

Le **CFrameWnd** classe fournit la majeure partie de l’interface d’utilisateur et de routage des commandes mise en œuvre de la mise à jour. Cela est principalement utilisé pour la fenêtre frame principale de l’application (**CWinApp::m_pMainWnd**), mais s’applique à toutes les fenêtres frame.

La fenêtre frame principale est la fenêtre avec la barre de menus et est le parent de la barre d’état ou de la ligne de message. Reportez-vous à la discussion ci-dessus sur le routage des commandes et **WM_INITMENUPOPUP.**

Le **CFrameWnd** classe fournit la gestion de la vue active. Les messages suivants sont routées via la vue active :

- Tous les messages de commande (la vue active obtient le premier d’y accéder).

- **Messages WM_HSCROLL** et **WM_VSCROLL** (voir ci-dessous) de barres de défilement de messages à partir de frère.

- **WM_ACTIVATE** (et **WM_MDIACTIVATE** pour MDI) obtenir transformé en appels à la fonction virtuelle **CView::OnActivateView**.

## <a name="cmdiframewndcmdichildwnd-issues"></a>Problèmes de CMDIFrameWnd/CMDIChildWnd

Les deux classes de fenêtre frame MDI dérivent **CFrameWnd** et par conséquent sont toutes deux activées pour le même type de routage des commandes et la mise à jour de l’interface utilisateur fourni dans **CFrameWnd**. Dans une application MDI typique, seule la fenêtre frame principale (autrement dit, le **CMDIFrameWnd** objet) contient la barre de menus et la barre d’état et par conséquent, est la principale source de l’implémentation de routage de commande.

Le schéma de routage général est que la fenêtre MDI enfant active obtient le premier accès aux commandes. La valeur par défaut **PreTranslateMessage** fonctions gèrent les tables d’accélérateurs pour les deux fenêtres MDI enfants (premier) et le frame MDI (deuxième), ainsi que les accélérateurs de commande du système standards MDI normalement gérés par  **TranslateMDISysAccel** (dernière).

## <a name="scroll-bar-issues"></a>Problèmes de la barre de défilement

Lors du traitement de message de défilement (**messages WM_HSCROLL**/**OnHScroll** et/ou **WM_VSCROLL**/**OnVScroll**), vous devez essayer d’écrire le code du gestionnaire afin qu’il ne repose pas sur d'où provenance le message de barre de défilement. Il s’agit pas uniquement un problème Windows général, dans la mesure où les messages de défilement peuvent provenir de défilement true contrôles de barre ou à partir de **WS_HSCROLL**/**WS_VSCROLL** barres qui ne sont pas des contrôles de barre de défilement de défilement.

MFC s’étend à autoriser pour les contrôles de barre de défilement enfants ou frères de la fenêtre en cours de défilement (en fait, la relation parent/enfant entre la barre de défilement et de la fenêtre en cours de défilement peut être quoi que ce soit). Cela est particulièrement important pour les barres de défilement partagé avec les fenêtres fractionnées. Reportez-vous à [Technical Note 29](../mfc/tn029-splitter-windows.md) pour plus d’informations sur l’implémentation de **CSplitterWnd** y compris des informations sur partagé des problèmes de barre de défilement.

Sur une note rapide, il existe deux **CWnd** des classes dérivées où les styles de barre de défilement spécifiées à créer les temps sont interceptées et pas passés à Windows. Quand il est passé à une routine de la création, **WS_HSCROLL** et **WS_VSCROLL** peut être défini indépendamment, mais une fois que la création ne peut pas être modifiée. Bien sûr, vous ne devez pas directement tester ou définir les bits de style WS_SCROLL de la fenêtre qu’ils ont créés.

Pour **CMDIFrameWnd** les styles de barre de défilement vous passez à **créer** ou **LoadFrame** sont utilisées pour créer le MDICLIENT. Si vous souhaitez avoir une zone MDICLIENT avec défilement (tels que le Windows responsable de programme) veillez à définir à la fois de barre de défilement styles (**WS_HSCROLL** &#124; **WS_VSCROLL**) pour le style utilisé pour créer le **CMDIFrameWnd**.

Pour **CSplitterWnd** les styles de barre de défilement s’appliquent aux barres de défilement de partagé spéciale pour les régions de séparateur. Pour les fenêtres fractionnées statiques, vous allez normalement pas définir un style de barre de défilement. Pour les fenêtres fractionnées dynamiques, vous devez généralement la barre de style défini pour la direction que vous allez fractionner, autrement dit, de défilement **WS_HSCROLL** si vous pouvez de répartir des lignes, **WS_VSCROLL** si vous pouvez fractionner des colonnes.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
