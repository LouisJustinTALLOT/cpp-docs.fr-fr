---
title: 'TN021 : Routage des commandes et des messages'
ms.date: 06/28/2018
f1_keywords:
- vc.routing
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
ms.openlocfilehash: bdd405bda5c0af9e04a50eee4ef5738f3a53259e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370408"
---
# <a name="tn021-command-and-message-routing"></a>TN021 : Routage des commandes et des messages

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit l’architecture de routage et d’expédition de commande ainsi que des sujets avancés dans le routage général de message de fenêtre.

Veuillez consulter Visual CMD pour obtenir des détails généraux sur les architectures décrites ici, en particulier la distinction entre les messages Windows, les notifications de contrôle et les commandes. Cette note suppose que vous êtes très familier avec les questions décrites dans la documentation imprimée et ne traite que de sujets très avancés.

## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>Commande Routing et Dispatch MFC 1.0 Fonctionnalité évolue à MFC 2.0 Architecture

Windows a le message WM_COMMAND qui est surchargé pour fournir des notifications de commandes de menu, clés d’accélérateur et notifications de contrôle de dialogue.

MFC 1.0 s’est un peu appuyé sur cela en permettant à un `CWnd` gestionnaire de commande (par exemple, "OnFileNew") dans une classe dérivée d’être appelé en réponse à un WM_COMMAND spécifique. Ceci est collé avec une structure de données appelée la carte de message, et se traduit par un mécanisme de commande très efficace dans l’espace.

MFC 1.0 a également fourni des fonctionnalités supplémentaires pour séparer les notifications de contrôle des messages de commande. Les commandes sont représentées par une pièce d’identité 16 bits, parfois connue sous le nom d’ID de commandement. Les commandes commencent normalement `CFrameWnd` à partir d’un (c’est-à-dire une sélection de menu ou un accélérateur traduit) et sont acheminées vers une variété d’autres fenêtres.

MFC 1.0 a utilisé le routage de commande dans un sens limité pour la mise en œuvre de l’interface documentaire multiple (MDI). (Un délégué de fenêtre de cadre MDI commande à sa fenêtre active MDI Enfant.)

Cette fonctionnalité a été généralisée et étendue dans MFC 2.0 pour permettre aux commandes d’être manipulées par une plus large gamme d’objets (pas seulement des objets de fenêtre). Il fournit une architecture plus formelle et plus extensible pour l’acheminement des messages et réutilise le routage cible de commande non seulement pour la manipulation des commandes, mais aussi pour la mise à jour des objets d’interface utilisateur (comme les éléments de menu et les boutons de barre d’outils) pour refléter la disponibilité actuelle d’une commande.

## <a name="command-ids"></a>ID de commande

Consultez Visual CMD pour obtenir une explication du processus de routage et de liaison de commande. [Note technique 20](../mfc/tn020-id-naming-and-numbering-conventions.md) contient des informations sur la dénomination ID.

Nous utilisons le préfixe générique "ID_" pour les Œd de commande. Les id de commande sont >0x8000. La ligne de message ou la barre d’état affichera la chaîne de description de commande s’il y a une ressource STRINGTABLE avec les mêmes IDENTIFIANTs que l’ID de commande.

Dans les ressources de votre application, une pièce d’identité de commande peut s’appliquer à plusieurs endroits :

- Dans une ressource STRINGTABLE qui a la même pièce d’identité que l’invite de ligne de message.

- Dans peut-être de nombreuses ressources MENU qui sont attachés à des éléments de menu qui invoquent la même commande.

- (ADVANCED) dans un bouton de dialogue pour une commande GOSUB.

Dans le code source de votre application, un id de commande peut s’appliquer à plusieurs endroits :

- Dans votre RESOURCE. H (ou tout autre fichier d’en-tête de symbole principal) pour définir les IDENT de commande spécifiques à l’application.

- PERHAPS Dans un tableau d’identité utilisé pour créer une barre d’outils.

- Dans une macro ON_COMMAND.

- PERHAPS Dans une macro ON_UPDATE_COMMAND_UI.

Actuellement, la seule implémentation dans MFC qui nécessite des Œuvres de commande être >0x8000 est la mise en œuvre de dialogues/commandes GOSUB.

## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>GOSUB Commande, Utilisation de l’architecture de commandement dans les dialogues

L’architecture de commande des commandes de routage et d’activation fonctionne bien avec des fenêtres de cadre, des éléments de menu, des boutons de barre d’outils, des boutons de barre de dialogue, d’autres barres de commande et d’autres éléments d’interface utilisateur conçus pour mettre à jour sur la demande et les commandes d’itinéraire ou les identifiants de commande à une cible de commande principale (généralement la fenêtre principale de cadre). Cette cible de commande principale peut acheminer les notifications de commande ou de contrôle vers d’autres objets cibles de commande, le cas échéant.

Un dialogue (modal ou sans mode) peut bénéficier de certaines des caractéristiques de l’architecture de commande si vous attribuez l’ID de contrôle du contrôle de dialogue à l’ID de commande approprié. La prise en charge des dialogues n’est pas automatique, de sorte que vous devrez peut-être écrire un code supplémentaire.

Notez que pour que toutes ces fonctionnalités fonctionnent correctement, vos ids de commande doivent être >0x8000. Étant donné que de nombreux dialogues pourraient être acheminés vers le même cadre, les commandes partagées devraient être >0x8000, tandis que les CDI non partagés dans un dialogue spécifique devraient être <0x7FFF.

Vous pouvez placer un bouton normal dans un dialogue modal normal avec l’IDC du bouton réglé sur l’ID de commande approprié. Lorsque l’utilisateur sélectionne le bouton, le propriétaire du dialogue (généralement la fenêtre du cadre principal) obtient la commande comme n’importe quelle autre commande. C’est ce qu’on appelle une commande GOSUB car il est généralement utilisé pour soulever un autre dialogue (un GOSUB du premier dialogue).

Vous pouvez également `CWnd::UpdateDialogControls` appeler la fonction sur votre dialogue et lui passer l’adresse de votre fenêtre de cadre principale. Cette fonction permettra ou désactivera vos contrôles de dialogue en fonction de la question de savoir s’ils ont des gestionnaires de commande dans le cadre. Cette fonction est appelée automatiquement pour vous pour les barres de contrôle dans la boucle de votre application au ralenti, mais vous devez l’appeler directement pour les dialogues normaux que vous souhaitez avoir cette fonctionnalité.

## <a name="when-on_update_command_ui-is-called"></a>Quand ON_UPDATE_COMMAND_UI est appelé

Maintenir l’état activé/vérifié de tous les éléments de menu d’un programme tout le temps peut être un problème computationnellement coûteux. Une technique courante consiste à activer/vérifier les éléments de menu uniquement lorsque l’utilisateur sélectionne le POPUP. La mise en œuvre `CFrameWnd` MFC 2.0 des poignées du message WM_INITMENUPOPUP et utilise l’architecture de routage de commande pour déterminer l’état des menus par ON_UPDATE_COMMAND_UI les gestionnaires.

`CFrameWnd`gère également le message WM_ENTERIDLE pour décrire l’élément de menu actuel sélectionné sur la barre d’état (également connu sous le nom de ligne de message).

La structure de menu d’une application, éditée par Visual CMD, est utilisée pour représenter les commandes potentielles disponibles à WM_INITMENUPOPUP moment. ON_UPDATE_COMMAND_UI les gestionnaires peuvent modifier l’état ou le texte d’un menu, ou pour des utilisations avancées (comme la liste MrU Fichier ou le menu pop-up OLE Verbs), modifient en fait la structure du menu avant que le menu ne soit dessiné.

Le même type de traitement ON_UPDATE_COMMAND_UI est fait pour les barres d’outils (et autres barres de contrôle) lorsque l’application entre dans sa boucle de ralenti. Consultez la *référence de la bibliothèque de classe* et la note technique [31](../mfc/tn031-control-bars.md) pour plus d’informations sur les barres de contrôle.

## <a name="nested-pop-up-menus"></a>Menus Pop-up imbriqués

Si vous utilisez une structure de menu imbriquée, vous remarquerez que le gestionnaire ON_UPDATE_COMMAND_UI pour le premier élément de menu dans le menu pop-up est appelé dans deux cas différents.

Tout d’abord, il est appelé pour le menu pop-up lui-même. Cela est nécessaire parce que les menus pop-up n’ont pas d’ID et nous utilisons l’ID du premier élément de menu du menu pop-up pour se référer à l’ensemble du menu pop-up. Dans ce cas, la variable *m_pSubMenu* `CCmdUI` membre de l’objet sera non-NULL et pointera vers le menu pop-up.

Deuxièmement, il est appelé juste avant les éléments du menu dans le menu pop-up doivent être dessinés. Dans ce cas, l’ID se réfère uniquement *m_pSubMenu* à l’élément `CCmdUI` du premier menu et la variable m_pSubMenu membre de l’objet sera NULL.

Cela vous permet d’activer le menu pop-up distinct de ses éléments de menu, mais exige que vous écriviez du code de menu conscient. Par exemple, dans un menu imbriqué avec la structure suivante :

```Output
File>
    New>
    Sheet (ID_NEW_SHEET)
    Chart (ID_NEW_CHART)
```

Les commandes ID_NEW_SHEET et ID_NEW_CHART peuvent être activées ou désactivées de façon indépendante. Le **nouveau** menu pop-up doit être activé si l’un ou l’autre des deux est activé.

Le gestionnaire de commande pour ID_NEW_SHEET (la première commande dans le pop-up) ressemblerait à quelque chose comme:

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

Le gestionnaire de commande pour ID_NEW_CHART serait un gestionnaire de commande de mise à jour normale et ressemblerait à quelque chose comme:

```cpp
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)
{
    pCmdUI->Enable(m_bCanCreateChart);
}
```

## <a name="on_command-and-on_bn_clicked"></a>ON_COMMAND et ON_BN_CLICKED

Les macros de carte de message pour **ON_COMMAND** et **ON_BN_CLICKED** sont les mêmes. Le mécanisme de routage de notification de commande et de contrôle MFC n’utilise que l’ID de commande pour décider où s’acheminer. Les notifications de contrôle avec code de notification de contrôle de zéro (**BN_CLICKED**) sont interprétées comme des commandes.

> [!NOTE]
> En fait, tous les messages de notification de contrôle passent par la chaîne de gestionnaire de commande. Par exemple, il est techniquement possible pour vous d’écrire un gestionnaire de notification de contrôle pour **EN_CHANGE** dans votre classe de documents. Ce n’est généralement pas conseillé parce que les applications pratiques de cette fonctionnalité sont rares, la fonctionnalité n’est pas prise en charge par ClassWizard, et l’utilisation de la fonctionnalité peut entraîner un code fragile.

## <a name="disabling-the-automatic-disabling-of-button-controls"></a>Désactiver la désactivation automatique des contrôles des boutons

Si vous placez un contrôle de bouton sur une barre de dialogue, ou dans un dialogue en utilisant où vous appelez **CWnd::UpdateDialogControls** sur votre propre, vous remarquerez que les boutons qui n’ont pas **de ON_COMMAND** ou **ON_UPDATE_COMMAND_UI** les gestionnaires seront automatiquement désactivés pour vous par le cadre. Dans certains cas, vous n’aurez pas besoin d’avoir un gestionnaire, mais vous voudrez que le bouton reste activé. La façon la plus simple d’y parvenir est d’ajouter un gestionnaire de commande factice (facile à faire avec ClassWizard) et de ne rien y faire.

## <a name="window-message-routing"></a>Itinéraire de message de fenêtre

Ce qui suit décrit quelques sujets plus avancés sur les classes MFC et comment le routage de messages Windows et d’autres sujets les ont l’impact. L’information ici n’est décrite que brièvement. Consultez la *référence de la bibliothèque de classe* pour plus de détails sur les API publiques. Veuillez consulter le code source de la bibliothèque MFC pour plus d’informations sur les détails de la mise en œuvre.

Veuillez consulter [la Note Technique 17](../mfc/tn017-destroying-window-objects.md) pour plus de détails sur le nettoyage des fenêtres, un sujet très important pour toutes les classes dérivées du **CWnd.**

## <a name="cwnd-issues"></a>Questions CWnd

La fonction membre de la mise en œuvre **CWnd::OnChildNotify** fournit une architecture puissante et extensible pour les fenêtres pour enfants (également connu sous le nom de contrôles) pour accrocher ou autrement être informé des messages, des commandes et des notifications de contrôle qui vont à leurs parents (ou «propriétaire»). Si la fenêtre de l’enfant (/contrôle) est un objet **CWnd** lui-même, la fonction virtuelle **OnChildNotify** est appelée en premier avec les paramètres du message original (c’est-à-dire une structure **MSG).** La fenêtre de l’enfant peut laisser le message seul, le manger ou modifier le message pour le parent (rare).

L’implémentation **CWnd** par défaut gère les messages suivants et utilise le crochet **OnChildNotify** pour permettre aux fenêtres des enfants (contrôles) d’accéder d’abord au message :

- **WM_MEASUREITEM** et **WM_DRAWITEM** (pour l’auto-tirage)

- **WM_COMPAREITEM** et **WM_DELETEITEM** (pour l’auto-tirage)

- **WM_HSCROLL** et **WM_VSCROLL**

- **WM_CTLCOLOR**

- **WM_PARENTNOTIFY**

Vous remarquerez que le crochet **OnChildNotify** est utilisé pour changer les messages de propriétaire-tirage en messages d’auto-tirage.

En plus du crochet **OnChildNotify,** les messages de défilement ont d’autres comportements de routage. Veuillez voir ci-dessous pour plus de détails sur les barres de défilement et les sources de **WM_HSCROLL** et **de messages WM_VSCROLL.**

## <a name="cframewnd-issues"></a>Questions CFrameWnd

La classe **CFrameWnd** fournit la majeure partie de l’implémentation de mise à jour du routage de commande et de l’interface utilisateur. Ceci est principalement utilisé pour la fenêtre de cadre principale de l’application (**CWinApp::m_pMainWnd**) mais s’applique à toutes les fenêtres de cadre.

La fenêtre du cadre principal est la fenêtre avec la barre de menu et est le parent de la barre d’état ou la ligne de message. Veuillez vous référer à la discussion ci-dessus sur le routage des commandes et **WM_INITMENUPOPUP.**

La classe **CFrameWnd** assure la gestion de la vue active. Les messages suivants sont acheminés à travers la vue active :

- Tous les messages de commande (la vue active obtient d’abord leur accès).

- **WM_HSCROLL** et **WM_VSCROLL** messages des barres de défilement des frères et sœurs (voir ci-dessous).

- **WM_ACTIVATE** (et **WM_MDIACTIVATE** pour MDI) se transformer en appels à la fonction virtuelle **CView::OnActivateView**.

## <a name="cmdiframewndcmdichildwnd-issues"></a>CMDIFrameWnd/CMDIChildWnd Issues

Les deux classes de fenêtre de cadre MDI dérivent de **CFrameWnd** et sont donc tous deux activés pour le même type de routage de commande et de mise à jour utilisateur-interface fourni dans **CFrameWnd**. Dans une application MDI typique, seule la fenêtre principale du cadre (c’est-à-dire l’objet **CMDIFrameWnd)** détient la barre de menu et la barre d’état et est donc la principale source de la mise en œuvre du routage de commande.

Le système général de routage est que la fenêtre active de l’enfant MDI obtient d’abord l’accès aux commandes. Les **fonctions PréTranslateMessage** par défaut gèrent les tables d’accélérateur pour les fenêtres pour enfants MDI (première) et le cadre MDI (deuxième) ainsi que les accélérateurs de commande système MDI standard normalement manipulés par **TranslateMDISysAccel** (dernier).

## <a name="scroll-bar-issues"></a>Problèmes de barre de défilement

Lors de la manipulation de défilement-message (**WM_HSCROLL**/**OnHScroll** et / ou **WM_VSCROLL**/**OnVScroll**), vous devriez essayer d’écrire le code gestionnaire de sorte qu’il ne repose pas sur l’endroit où le message de barre de défilement vient. Ce n’est pas seulement un problème Windows général, puisque les messages de défilement peuvent provenir de commandes de barre de défilement vrai ou de **WS_HSCROLL**/**WS_VSCROLL** les barres de défilement qui ne sont pas défiler les commandes de barre.

MFC étend que pour permettre aux commandes de barre de défilement d’être soit enfant ou frères et sœurs de la fenêtre étant défilé (en fait, la relation parent /enfant entre la barre de défilement et la fenêtre étant défilé peut être n’importe quoi). Ceci est particulièrement important pour les barres de défilement partagées avec des fenêtres de splitter. Veuillez consulter [la Note Technique 29](../mfc/tn029-splitter-windows.md) pour plus de détails sur la mise en œuvre de **CSplitterWnd,** y compris plus d’informations sur les numéros de barre de défilement partagés.

Sur une note latérale, il ya deux classes **dérivées CWnd** où les styles de barre de défilement spécifiés au moment de la création sont piégés et non pas passé à Windows. Lorsqu’il est passé à une routine de création, **WS_HSCROLL** et **WS_VSCROLL** peuvent être définis indépendamment, mais après la création ne peut pas être changé. Bien sûr, vous ne devriez pas tester directement ou définir les bits de style WS_SCROLL de la fenêtre qu’ils ont créé.

Pour **CMDIFrameWnd,** les styles de barre de défilement que vous passez pour **créer** ou **ChargerFrame** sont utilisés pour créer le MDICLIENT. Si vous souhaitez avoir une zone MDICLIENT défilementable (comme le gestionnaire de programme Windows) assurez-vous de définir les deux styles de barre de défilement **(WS_HSCROLL** &#124; **WS_VSCROLL**) pour le style utilisé pour créer le **CMDIFrameWnd**.

Pour **CSplitterWnd,** les styles de barre de défilement s’appliquent aux barres spéciales de défilement partagé pour les régions de splitter. Pour les fenêtres de splitter statiques, vous ne définissez normalement pas l’un ou l’autre style de barre de défilement. Pour les fenêtres de splitter dynamique, vous aurez généralement le style de barre de défilement réglé pour la direction que vous diviserez, c’est-à-dire, **WS_HSCROLL** si vous pouvez diviser des lignes, **WS_VSCROLL** si vous pouvez diviser des colonnes.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
