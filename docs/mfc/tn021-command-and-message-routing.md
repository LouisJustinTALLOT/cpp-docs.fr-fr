---
description: 'En savoir plus sur : TN021 : routage des commandes et des messages'
title: 'TN021 : Routage des commandes et des messages'
ms.date: 06/28/2018
f1_keywords:
- vc.routing
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
ms.openlocfilehash: 3cc481585fa2f1eacc3deb575e163d5a1644002c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215844"
---
# <a name="tn021-command-and-message-routing"></a>TN021 : Routage des commandes et des messages

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit l’architecture de routage et de répartition des commandes, ainsi que des rubriques avancées dans le routage des messages de la fenêtre générale.

Reportez-vous à Visual C++ pour obtenir des informations générales sur les architectures décrites ici, en particulier la distinction entre les messages Windows, les notifications de contrôle et les commandes. Cette remarque suppose que vous êtes familiarisé avec les problèmes décrits dans la documentation imprimée et que vous n’abordiez que des sujets très avancés.

## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>Les fonctionnalités MFC 1,0 de routage et de dispatch des commandes évoluent vers l’architecture MFC 2,0

Windows a le message WM_COMMAND qui est surchargé pour fournir des notifications de commandes de menu, de touches accélérateur et de notifications de contrôle de boîte de dialogue.

MFC 1,0 reposait un peu sur ce qui a permis à un gestionnaire de commandes (par exemple, « OnFileNew ») dans une `CWnd` classe dérivée d’être appelé en réponse à un WM_COMMAND spécifique. Cette méthode est collée avec une structure de données appelée table des messages et produit un mécanisme de commande très économe en espace.

MFC 1,0 offrait également des fonctionnalités supplémentaires pour séparer les notifications de contrôle des messages de commande. Les commandes sont représentées par un ID 16 bits, parfois connu sous le nom d’ID de commande. Les commandes démarrent normalement à partir d’un `CFrameWnd` (autrement dit, une sélection de menu ou un accélérateur traduit) et sont routées vers une variété d’autres fenêtres.

MFC 1,0 a utilisé le routage des commandes dans un sens limité pour l’implémentation de l’interface multidocument (MDI, multiple document interface). (Une fenêtre frame MDI délègue des commandes à sa fenêtre enfant MDI active.)

Cette fonctionnalité a été généralisée et étendue dans MFC 2,0 pour permettre la gestion des commandes par un plus grand nombre d’objets (pas seulement les objets de fenêtre). Il fournit une architecture plus formelle et plus extensible pour le routage des messages et réutilise le routage de la cible de commande pour non seulement la gestion des commandes, mais également pour la mise à jour des objets d’interface utilisateur (comme les éléments de menu et les boutons de barre d’outils) pour refléter la disponibilité actuelle d’une commande.

## <a name="command-ids"></a>ID de commande

Consultez Visual C++ pour obtenir une explication du processus de liaison et de routage des commandes. La [note technique 20](../mfc/tn020-id-naming-and-numbering-conventions.md) contient des informations sur l’attribution des noms d’ID.

Nous utilisons le préfixe générique « ID_ » pour les ID de commande. Les ID de commande sont >= 0x8000. La ligne de message ou la barre d’état affiche la chaîne de description de la commande s’il existe une ressource STRINGTABLE avec les mêmes ID que l’ID de commande.

Dans les ressources de votre application, un ID de commande peut apparaître à plusieurs endroits :

- Dans une ressource STRINGTABLE qui a le même ID que l’invite de ligne de message.

- Dans de nombreuses ressources de MENU qui sont attachées à des éléments de menu qui appellent la même commande.

- (Avancé) dans un bouton de boîte de dialogue pour une commande GOSUB.

Dans le code source de votre application, un ID de commande peut apparaître à plusieurs endroits :

- Dans votre ressource. H (ou un autre fichier d’en-tête de symbole principal) pour définir des ID de commande spécifiques à l’application.

- PEUT-être dans un tableau d’ID utilisé pour créer une barre d’outils.

- Dans une macro ON_COMMAND.

- PEUT-être dans une macro ON_UPDATE_COMMAND_UI.

Actuellement, la seule implémentation dans MFC qui requiert des ID de commande est >= 0x8000 est l’implémentation des boîtes de dialogue/commandes GOSUB.

## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>Commandes GOSUB, utilisation de l’architecture de commande dans les boîtes de dialogue

L’architecture de commande des commandes de routage et d’activation fonctionne bien avec les fenêtres Frame, les éléments de menu, les boutons de barre d’outils, les boutons de la barre de boîte de dialogue, d’autres barres de contrôles et d’autres éléments de l’interface utilisateur conçus pour mettre à jour à la demande et les commandes de routage ou les ID de contrôle vers une cible de commande principale (généralement Cette cible de commande principale peut acheminer la commande ou contrôler les notifications vers d’autres objets cibles de commande, le cas échéant.

Une boîte de dialogue (modale ou non modale) peut tirer parti de certaines des fonctionnalités de l’architecture de commande si vous assignez l’ID de contrôle du contrôle de boîte de dialogue à l’ID de commande approprié. La prise en charge des boîtes de dialogue n’étant pas automatique, vous devrez peut-être écrire du code supplémentaire.

Notez que pour que toutes ces fonctionnalités fonctionnent correctement, vos ID de commande doivent être >= 0x8000. Étant donné que de nombreuses boîtes de dialogue peuvent être acheminées vers le même frame, les commandes partagées doivent être >= 0x8000, tandis que les IDCs non partagés dans une boîte de dialogue spécifique doivent être <= 0x7FFF.

Vous pouvez placer un bouton normal dans une boîte de dialogue modale normale, avec l’IDC du bouton défini sur l’ID de commande approprié. Lorsque l’utilisateur sélectionne le bouton, le propriétaire de la boîte de dialogue (généralement la fenêtre frame principale) obtient la commande comme n’importe quelle autre commande. C’est ce qu’on appelle une commande GOSUB dans la mesure où elle est généralement utilisée pour afficher une autre boîte de dialogue (un GOSUB de la première boîte de dialogue).

Vous pouvez également appeler la fonction `CWnd::UpdateDialogControls` dans votre boîte de dialogue et la passer à l’adresse de votre fenêtre frame principale. Cette fonction active ou désactive vos contrôles de boîte de dialogue selon qu’ils possèdent ou non des gestionnaires de commandes dans le frame. Cette fonction est appelée automatiquement pour vous pour les barres de contrôle dans la boucle inactive de votre application, mais vous devez l’appeler directement pour les boîtes de dialogue normales pour lesquelles vous souhaitez disposer de cette fonctionnalité.

## <a name="when-on_update_command_ui-is-called"></a>Lorsque ON_UPDATE_COMMAND_UI est appelé

Conserver l’état activé/activé de tous les éléments de menu d’un programme tout le temps peut être un problème de calcul coûteux. Une technique courante consiste à activer/vérifier les éléments de menu uniquement lorsque l’utilisateur sélectionne la fenêtre contextuelle. L’implémentation MFC 2,0 de `CFrameWnd` gère le message WM_INITMENUPOPUP et utilise l’architecture de routage des commandes pour déterminer les États des menus via des gestionnaires de ON_UPDATE_COMMAND_UI.

`CFrameWnd` gère également le message de WM_ENTERIDLE pour décrire l’élément de menu actuel sélectionné dans la barre d’État (également appelée ligne de message).

La structure de menus d’une application, modifiée par Visual C++, est utilisée pour représenter les commandes potentielles disponibles au moment de l’WM_INITMENUPOPUP. Les gestionnaires de ON_UPDATE_COMMAND_UI peuvent modifier l’État ou le texte d’un menu, ou pour des utilisations avancées (telles que la liste des fichiers récents ou le menu contextuel verbes OLE), modifient en fait la structure du menu avant le dessin du menu.

Le même type de traitement de ON_UPDATE_COMMAND_UI est effectué pour les barres d’outils (et d’autres barres de contrôle) lorsque l’application entre sa boucle inactive. Pour plus d’informations sur les barres de contrôles, consultez la référence de la *bibliothèque de classes* et la [note technique 31](../mfc/tn031-control-bars.md) .

## <a name="nested-pop-up-menus"></a>Menus contextuels imbriqués

Si vous utilisez une structure de menus imbriquée, vous remarquerez que le gestionnaire de ON_UPDATE_COMMAND_UI pour le premier élément de menu dans le menu contextuel est appelé dans deux cas différents.

Tout d’abord, elle est appelée pour le menu contextuel lui-même. Cela est nécessaire car les menus contextuels n’ont pas d’ID et nous utilisons l’ID du premier élément de menu du menu contextuel pour faire référence au menu contextuel entier. Dans ce cas, la variable de membre *m_pSubMenu* de l' `CCmdUI` objet sera non null et pointera vers le menu contextuel.

Deuxièmement, il est appelé juste avant que les éléments de menu du menu contextuel soient dessinés. Dans ce cas, l’ID fait uniquement référence au premier élément de menu et la variable membre *m_pSubMenu* de l' `CCmdUI` objet a la valeur null.

Cela vous permet d’activer le menu contextuel distinct de ses éléments de menu, mais vous oblige à écrire un code de prise en charge de menu. Par exemple, dans un menu imbriqué avec la structure suivante :

```Output
File>
    New>
    Sheet (ID_NEW_SHEET)
    Chart (ID_NEW_CHART)
```

Les commandes ID_NEW_SHEET et ID_NEW_CHART peuvent être activées ou désactivées de manière indépendante. Le **nouveau** menu contextuel doit être activé si l’un des deux est activé.

Le gestionnaire de commandes pour ID_NEW_SHEET (la première commande de la fenêtre contextuelle) ressemble à ceci :

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

Le gestionnaire de commandes pour ID_NEW_CHART est un gestionnaire de commandes de mise à jour normal qui ressemble à ceci :

```cpp
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)
{
    pCmdUI->Enable(m_bCanCreateChart);
}
```

## <a name="on_command-and-on_bn_clicked"></a>ON_COMMAND et ON_BN_CLICKED

Les macros de la table des messages pour **ON_COMMAND** et **ON_BN_CLICKED** sont les mêmes. La commande MFC et le mécanisme de routage des notifications de contrôle utilisent uniquement l’ID de commande pour déterminer l’emplacement de routage. Les notifications de contrôle avec un code de notification de contrôle de zéro (**BN_CLICKED**) sont interprétées comme des commandes.

> [!NOTE]
> En fait, tous les messages de notification de contrôle passent par la chaîne du gestionnaire de commandes. Par exemple, il est techniquement possible d’écrire un gestionnaire de notifications de contrôle pour **EN_CHANGE** dans votre classe de document. Cela n’est généralement pas recommandé, car les applications pratiques de cette fonctionnalité sont peu nombreuses, la fonctionnalité n’est pas prise en charge par ClassWizard et l’utilisation de la fonctionnalité peut entraîner un code fragile.

## <a name="disabling-the-automatic-disabling-of-button-controls"></a>Désactivation de la désactivation automatique des contrôles Button

Si vous placez un contrôle bouton sur une barre de boîte de dialogue, ou dans une boîte de dialogue qui vous permet d’appeler **CWnd :: UpdateDialogControls** vous-même, vous remarquerez que les boutons qui n’ont pas de gestionnaires **ON_COMMAND** ou **ON_UPDATE_COMMAND_UI** seront automatiquement désactivés par l’infrastructure. Dans certains cas, vous n’aurez pas besoin d’un gestionnaire, mais vous voudrez que le bouton reste activé. Le moyen le plus simple d’y parvenir consiste à ajouter un gestionnaire de commandes factices (facile à faire avec ClassWizard) et à ne rien faire.

## <a name="window-message-routing"></a>Routage des messages de fenêtre

Les rubriques suivantes décrivent des rubriques plus avancées sur les classes MFC et expliquent comment le routage des messages Windows et d’autres rubriques les affectent. Les informations ici sont uniquement décrites brièvement. Pour plus d’informations sur les API publiques, reportez-vous à la référence de la *bibliothèque de classes* . Pour plus d’informations sur les détails d’implémentation, consultez le code source de la bibliothèque MFC.

Reportez-vous à la [note technique 17](../mfc/tn017-destroying-window-objects.md) pour plus d’informations sur le nettoyage de la fenêtre, un sujet très important pour toutes les classes dérivées de **CWnd**.

## <a name="cwnd-issues"></a>Problèmes de CWnd

La fonction membre d’implémentation **CWnd :: OnChildNotify** fournit une architecture puissante et extensible pour les fenêtres enfants (également appelées contrôles) pour raccorder des messages, des commandes et des notifications de contrôle qui accèdent à leur parent (ou « propriétaire »). Si la fenêtre enfant (/Control) est un objet C++ **CWnd** lui-même, la fonction virtuelle **OnChildNotify** est appelée en premier avec les paramètres du message d’origine (autrement dit, une structure **MSG** ). La fenêtre enfant peut conserver le message seul, le manger ou modifier le message pour le parent (rare).

L’implémentation **CWnd** par défaut gère les messages suivants et utilise le hook **OnChildNotify** pour permettre aux fenêtres enfants (contrôles) d’accéder d’abord au message :

- **WM_MEASUREITEM** et **WM_DRAWITEM** (pour le dessin automatique)

- **WM_COMPAREITEM** et **WM_DELETEITEM** (pour le dessin automatique)

- **WM_HSCROLL** et **WM_VSCROLL**

- **WM_CTLCOLOR**

- **WM_PARENTNOTIFY**

Vous remarquerez que le hook **OnChildNotify** est utilisé pour modifier les messages owner-draw en messages de dessin automatique.

Outre le hook **OnChildNotify** , les messages de défilement ont un comportement de routage plus poussé. Pour plus d’informations sur les barres de défilement et les sources des messages **WM_HSCROLL** et **WM_VSCROLL** , voir ci-dessous.

## <a name="cframewnd-issues"></a>Problèmes CFrameWnd

La classe **CFrameWnd** fournit la majeure partie de l’implémentation de la mise à jour du routage des commandes et de l’interface utilisateur. Cela est principalement utilisé pour la fenêtre frame principale de l’application (**CWinApp :: m_pMainWnd**), mais s’applique à toutes les fenêtres Frame.

La fenêtre frame principale est la fenêtre avec la barre de menus et est le parent de la barre d’État ou de la ligne de message. Reportez-vous à la discussion ci-dessus sur le routage des commandes et les **WM_INITMENUPOPUP.**

La classe **CFrameWnd** fournit la gestion de la vue active. Les messages suivants sont routés via la vue active :

- Tous les messages de commande (la vue active reçoit tout d’abord un accès).

- **WM_HSCROLL** et **WM_VSCROLL** des messages à partir de barres de défilement frères (voir ci-dessous).

- **WM_ACTIVATE** (et **WM_MDIACTIVATE** pour MDI) sont convertis en appels à la fonction virtuelle **CView :: OnActivateView**.

## <a name="cmdiframewndcmdichildwnd-issues"></a>Problèmes de CMDIFrameWnd/CMDIChildWnd

Les deux classes de fenêtre frame MDI dérivent de **CFrameWnd** et, par conséquent, sont activées pour le même type de routage de commande et mise à jour de l’interface utilisateur fournie dans **CFrameWnd**. Dans une application MDI classique, seule la fenêtre frame principale (autrement dit, l’objet **CMDIFrameWnd** ) contient la barre de menus et la barre d’État, et constitue donc la principale source de l’implémentation du routage des commandes.

Le schéma de routage général est que la fenêtre enfant MDI active accède tout d’abord aux commandes. Les fonctions **PreTranslateMessage** par défaut gèrent les tables d’accélérateurs pour les fenêtres MDI enfants (premier) et le frame MDI (second), ainsi que pour les accélérateurs de commande système MDI standard normalement gérés par **TranslateMDISysAccel** (Last).

## <a name="scroll-bar-issues"></a>Problèmes de barre de défilement

Lors du traitement des messages de défilement (**WM_HSCROLL** / **OnHScroll** et/ou **WM_VSCROLL** / **OnVScroll**), vous devez essayer d’écrire le code du gestionnaire afin qu’il ne repose pas sur l’origine du message de la barre de défilement. Il s’agit non seulement d’un problème Windows général, car les messages de défilement peuvent provenir de contrôles de barre de défilement true ou de **WS_HSCROLL** / **WS_VSCROLL** des barres de défilement qui ne sont pas des contrôles de barre de défilement.

MFC étend cela pour permettre aux contrôles de barre de défilement d’être enfants ou frères de la fenêtre défilante (en fait, la relation parent/enfant entre la barre de défilement et la fenêtre défilante peut être n’importe quoi). Cela est particulièrement important pour les barres de défilement partagées avec des fenêtres fractionnées. Reportez-vous à la [note technique 29](../mfc/tn029-splitter-windows.md) pour plus d’informations sur l’implémentation de **CSplitterWnd** , y compris des informations supplémentaires sur les problèmes de barre de défilement partagée.

À l’heure actuelle, il existe deux classes dérivées **CWnd** où les styles de barre de défilement spécifiés au moment de la création sont interceptés et non passés à Windows. Lorsqu’elle est transmise à une routine de création, **WS_HSCROLL** et **WS_VSCROLL** peuvent être définis indépendamment, mais après la création ne peut pas être modifié. Bien entendu, vous ne devez pas tester ou définir directement les bits de style WS_SCROLL de la fenêtre qu’ils ont créée.

Pour **CMDIFrameWnd** , les styles de barre de défilement que vous passez pour **Create** ou **LoadFrame** sont utilisés pour créer le MdiClient. Si vous souhaitez avoir une zone MDICLIENT défilante (par exemple, le gestionnaire de programmes Windows), veillez à définir les deux styles de barre de défilement (**WS_HSCROLL** &#124; **WS_VSCROLL**) pour le style utilisé pour créer le **CMDIFrameWnd**.

Pour **CSplitterWnd** , les styles de barre de défilement s’appliquent aux barres de défilement partagées spéciales pour les zones de fractionnement. Pour les fenêtres fractionnées statiques, vous ne définissez normalement pas de style de barre de défilement. Pour les fenêtres fractionnées dynamiques, le style de barre de défilement est généralement défini pour la direction à fractionner. autrement dit, **WS_HSCROLL** si vous pouvez fractionner des lignes, **WS_VSCROLL** si vous pouvez fractionner des colonnes.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
