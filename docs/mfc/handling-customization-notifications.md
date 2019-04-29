---
title: Gestion des notifications de personnalisation
ms.date: 11/04/2016
f1_keywords:
- TBN_CUSTHELP
- TBN_QUERYINSERT
- TBNOTIFY
- NMHDR
- TBN_TOOLBARCHANGE
- TBN_ENDDRAG
- NM_SETFOCUS
- TBN_RESET
- NM_RETURN
- NM_ENDWAIT
- NM_STARTWAIT
- TBN_BEGINDRAG
- NM_OUTOFMEMORY
- TBN_QUERYDELETE
- NM_DBLCLK
- TBN_ENDADJUST
- NM_KILLFOCUS
- NM_RCLICK
- TBN_BEGINADJUST
- NM_CLICK
helpviewer_keywords:
- TBN_ENDADJUST notification [MFC]
- TBNOTIFY notification [MFC]
- TBN_BEGINDRAG notification [MFC]
- TBN_TOOLBARCHANGE notification [MFC]
- NM_CLICK notification [MFC]
- NM_RETURN notification [MFC]
- NM_RCLICK notification [MFC]
- TBN_ENDDRAG notification [MFC]
- TBN_BEGINADJUST notification [MFC]
- NM_ENDWAIT notification [MFC]
- NM_KILLFOCUS notification [MFC]
- NM_SETFOCUS notification [MFC]
- NM_OUTOFMEMORY notification [MFC]
- TBN_QUERYINSERT notification [MFC]
- NMHDR [MFC]
- NM_STARTWAIT notification [MFC]
- CToolBarCtrl class [MFC], handling notifications
- TBN_CUSTHELP notification [MFC]
- TBN_RESET notification [MFC]
- NM_DBLCLK notification [MFC]
- TBN_QUERYDELETE notification [MFC]
- NM_RDBLCLK notification [MFC]
- TBN_GETBUTTONINFO notification [MFC]
ms.assetid: 219ea08e-7515-4b98-85cb-47120f08c0a2
ms.openlocfilehash: dc34f3eaa4b085b9d8acbaf47b21cf1825627100
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240685"
---
# <a name="handling-customization-notifications"></a>Gestion des notifications de personnalisation

Un contrôle commun de barre d’outils Windows a des fonctionnalités de personnalisation intégrées, notamment une boîte de dialogue de personnalisation définie par le système, qui permettent à l’utilisateur d’insérer, de supprimer ou de réorganiser les boutons de barre d’outils. L’application détermine si les fonctionnalités de personnalisation sont disponibles et contrôle l’étendue selon laquelle l’utilisateur peut personnaliser la barre d’outils.

Vous pouvez proposer ces fonctionnalités de personnalisation à l’utilisateur en donnant la barre d’outils le **CCS_ADJUSTABLE** style. Les fonctionnalités de personnalisation permettent à l’utilisateur de faire glisser un bouton à un nouvel emplacement ou de supprimer un bouton en le faisant glisser en dehors de la barre d’outils. En outre, l’utilisateur peut double-cliquer sur la barre d’outils pour afficher la boîte de dialogue **Personnaliser la barre d’outils** , qui lui permet d’ajouter, de supprimer et de réorganiser les boutons de barre d’outils. L’application peut afficher la boîte de dialogue en utilisant la fonction membre [Customize](../mfc/reference/ctoolbarctrl-class.md#customize) .

Le contrôle de barre d’outils envoie des messages de notification à la fenêtre parente à chaque étape du processus de personnalisation. Si l’utilisateur maintient enfoncée la touche Maj et commence à faire glisser un bouton, la barre d’outils gère automatiquement l’opération glisser. La barre d’outils envoie le message de notification **TBN_QUERYDELETE** à la fenêtre parente pour déterminer si le bouton peut être supprimé. L’opération glisser se termine si la fenêtre parente retourne **FALSE**. Dans le cas contraire, la barre d’outils capture l’entrée de la souris et attend que l’utilisateur relâche le bouton de la souris.

Quand l’utilisateur relâche le bouton de la souris, le contrôle de barre d’outils détermine l’emplacement du curseur de la souris. Si le curseur se trouve en dehors de la barre d’outils, le bouton est supprimé. Si le curseur se trouve sur un autre bouton de barre d’outils, la barre d’outils envoie le message de notification **TBN_QUERYINSERT** à la fenêtre parente pour déterminer si un bouton peut être inséré à gauche du bouton concerné. Le bouton est inséré si la fenêtre parente retourne **TRUE**; sinon, il n’est pas inséré. La barre d’outils envoie le message de notification **TBN_TOOLBARCHANGE** pour signaler la fin de l’opération glisser.

Si l’utilisateur commence une opération glisser sans maintenir la touche Maj enfoncée, le contrôle de barre d’outils envoie le message de notification **TBN_BEGINDRAG** à la fenêtre propriétaire. Une application qui implémente son propre code de déplacement des boutons peut utiliser ce message comme signal pour commencer une opération glisser. La barre d’outils envoie le message de notification **TBN_ENDDRAG** pour signaler la fin de l’opération glisser.

Un contrôle de barre d’outils envoie des messages de notification quand l’utilisateur personnalise une barre d’outils en utilisant la boîte de dialogue **Personnaliser la barre d’outils** . La barre d’outils envoie le message de notification **TBN_BEGINADJUST** une fois que l’utilisateur a double-cliqué sur la barre d’outils, mais avant la création de la boîte de dialogue. Ensuite, la barre d’outils commence à envoyer une série de messages de notification **TBN_QUERYINSERT** pour déterminer si la barre d’outils autorise l’insertion de boutons. Quand la fenêtre parente retourne **TRUE**, la barre d’outils cesse d’envoyer des messages de notification **TBN_QUERYINSERT** . Si la fenêtre parente ne retourne pas **TRUE** pour un bouton, la barre d’outils détruit la boîte de dialogue.

Ensuite, le contrôle de barre d’outils détermine si des boutons peuvent être supprimés de la barre d’outils en envoyant un message de notification **TBN_QUERYDELETE** pour chaque bouton de la barre d’outils. La fenêtre parente retourne **TRUE** pour indiquer qu’un bouton peut être supprimé ; sinon, elle retourne **FALSE**. La barre d’outils ajoute tous les boutons de barre d’outils à la boîte de dialogue, mais affiche en grisé ceux qui ne peuvent pas être supprimés.

Chaque fois que le contrôle de barre d’outils a besoin d’informations sur un bouton dans la boîte de dialogue Personnaliser la barre d’outils, il envoie le message de notification **TBN_GETBUTTONINFO** , en spécifiant l’index du bouton pour lequel il a besoin d’informations et l’adresse d’une structure **TBNOTIFY** . La fenêtre parente doit remplir la structure avec les informations appropriées.

La boîte de dialogue **Personnaliser la barre d’outils** comprend un bouton Aide et un bouton Réinitialiser. Quand l’utilisateur choisit le bouton Aide, le contrôle de barre d’outils envoie le message de notification **TBN_CUSTHELP** . La fenêtre parente doit répondre en affichant des informations d’aide. La boîte de dialogue envoie le message de notification **TBN_RESET** quand l’utilisateur sélectionne le bouton Réinitialiser. Ce message signale que la barre d’outils va réinitialiser la boîte de dialogue.

Ces messages sont tous des messages **WM_NOTIFY** , et ils peuvent être gérés dans votre fenêtre propriétaire en ajoutant des entrées de table des messages sous la forme suivante à la table des messages de votre fenêtre propriétaire :

```cpp
ON_NOTIFY( wNotifyCode, idControl, memberFxn )
```

- **wNotifyCode**

   Code identificateur du message de notification, comme **TBN_BEGINADJUST**.

- **idControl**

   L’identificateur du contrôle qui envoie la notification.

- **memberFxn**

   La fonction membre à appeler quand cette notification est reçue.

Votre fonction membre doit être déclarée avec le prototype suivant :

```cpp
afx_msg void memberFxn( NMHDR * pNotifyStruct, LRESULT * result );
```

Si le gestionnaire de messages de notification retourne une valeur, elle doit être placée dans le **LRESULT** vers lequel pointe *result*.

Pour chaque message, `pNotifyStruct` pointe vers une structure **NMHDR** ou vers une structure **TBNOTIFY** . Ces structures sont décrites ci-dessous :

La structure **NMHDR** contient les membres suivants :

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;  // handle of control sending message
    UINT idFrom;// identifier of control sending message
    UINT code;  // notification code; see below
} NMHDR;
```

- **hwndFrom**

   Handle de fenêtre du contrôle qui envoie la notification. Pour convertir ce handle en un pointeur `CWnd` , utilisez [CWnd::FromHandle](../mfc/reference/cwnd-class.md#fromhandle).

- **idFrom**

   Identificateur du contrôle qui envoie la notification.

- **code**

   Code de la notification. Ce membre peut être une valeur spécifique à un type de contrôle, comme **TBN_BEGINADJUST** ou **TTN_NEEDTEXT**, ou il peut être une des valeurs de notification courantes répertoriées ci-dessous :

   - **NM_CLICK** L’utilisateur a cliqué dans le contrôle avec le bouton gauche de la souris.

   - **NM_DBLCLK** L’utilisateur a double-cliqué dans le contrôle avec le bouton gauche de la souris.

   - **NM_KILLFOCUS** Le contrôle n’a plus le focus d’entrée.

   - **NM_OUTOFMEMORY** Le contrôle n’a pas pu terminer une opération, car la mémoire disponible n’est pas suffisante.

   - **NM_RCLICK** L’utilisateur a cliqué dans le contrôle avec le bouton droit de la souris.

   - **NM_RDBLCLK** L’utilisateur a double-cliqué dans le contrôle avec le bouton droit de la souris.

   - **NM_RETURN** Le contrôle a le focus d’entrée et l’utilisateur a appuyé sur la touche Entrée.

   - **NM_SETFOCUS** Le contrôle a reçu le focus d’entrée.

La structure **TBNOTIFY** contient les membres suivants :

```cpp
typedef struct {
    NMHDR hdr; // information common to all WM_NOTIFY messages
    int iItem; // index of button associated with notification
    TBBUTTON tbButton; // info about button associated withnotification
    int cchText;   // count of characters in button text
    LPSTR lpszText;// address of button text
} TBNOTIFY, FAR* LPTBNOTIFY;
```

- **hdr**

   Informations communes à tous les messages **WM_NOTIFY** .

- **iItem**

   Index du bouton associé à la notification.

- **tbButton**

   **TBBUTTON** structure qui contient des informations sur le bouton de barre d’outils associé à la notification.

- **cchText**

   Nombre de caractères dans le texte du bouton.

- **lpszText**

   Pointeur vers le texte du bouton.

Les notifications envoyées par la barre d’outils sont les suivantes :

- **TBN_BEGINADJUST**

   Envoyé lorsque l’utilisateur commence la personnalisation d’un contrôle de barre d’outils. Le pointeur pointe vers une structure **NMHDR** qui contient des informations sur la notification. Le gestionnaire ne doit retourner aucune valeur spécifique.

- **TBN_BEGINDRAG**

   Envoyé lorsque l’utilisateur commence à faire glisser un bouton dans un contrôle de barre d’outils. Le pointeur pointe vers une structure **TBNOTIFY** . Le membre **iItem** contient l’index de base zéro du bouton qui est glissé. Le gestionnaire ne doit retourner aucune valeur spécifique.

- **TBN_CUSTHELP**

   Envoyé lorsque l’utilisateur choisit le bouton Aide dans la boîte de dialogue Personnaliser la barre d’outils. Pas de valeur de retour. Le pointeur pointe vers une structure **NMHDR** qui contient des informations sur le message de notification. Le gestionnaire ne doit retourner aucune valeur spécifique.

- **TBN_ENDADJUST**

   Envoyé lorsque l’utilisateur arrête la personnalisation d’un contrôle de barre d’outils. Le pointeur pointe vers une structure **NMHDR** qui contient des informations sur le message de notification. Le gestionnaire ne doit retourner aucune valeur spécifique.

- **TBN_ENDDRAG**

   Envoyé lorsque l’utilisateur arrête de faire glisser un bouton dans un contrôle de barre d’outils. Le pointeur pointe vers une structure **TBNOTIFY** . Le membre **iItem** contient l’index de base zéro du bouton qui est glissé. Le gestionnaire ne doit retourner aucune valeur spécifique.

- **TBN_GETBUTTONINFO**

   Envoyé lorsque l’utilisateur personnalise un contrôle de barre d’outils. La barre d’outils utilise ce message de notification pour extraire les informations nécessaires à la boîte de dialogue Personnaliser la barre d’outils. Le pointeur pointe vers une structure **TBNOTIFY** . Le membre **iItem** membre spécifie l’index de base zéro d’un bouton. Les membres **pszText** et **cchText** spécifient l’adresse et la longueur en caractères du texte du bouton. Une application doit remplir la structure avec des informations sur le bouton. Retourne **TRUE** si les informations sur le bouton ont été copiées vers la structure ; sinon, **FALSE** .

- **TBN_QUERYDELETE**

   Envoyé lorsque l’utilisateur personnalise une barre d’outils pour déterminer si un bouton peut être supprimé à partir d’un contrôle de barre d’outils. Le pointeur pointe vers une structure **TBNOTIFY** . Le membre **iItem** contient l’index de base zéro du bouton à supprimer. Retourne **TRUE** pour autoriser la suppression du bouton ou **FALSE** pour empêcher la suppression du bouton.

- **TBN_QUERYINSERT**

   Envoyé lorsque l’utilisateur personnalise un contrôle de barre d’outils pour déterminer si un bouton peut être inséré à gauche du bouton concerné. Le pointeur pointe vers une structure **TBNOTIFY** . Le membre **iItem** contient l’index de base zéro du bouton à insérer. Retourne **TRUE** pour autoriser l’insertion d’un bouton devant le bouton concerné, ou **FALSE** pour empêcher l’insertion du bouton.

- **TBN_RESET**

   Envoyé lorsque l’utilisateur réinitialise le contenu de la boîte de dialogue Personnaliser la barre d’outils. Le pointeur pointe vers une structure **NMHDR** qui contient des informations sur le message de notification. Le gestionnaire ne doit retourner aucune valeur spécifique.

- **TBN_TOOLBARCHANGE**

   Envoyé une fois que l’utilisateur a personnalisé un contrôle de barre d’outils. Le pointeur pointe vers une structure **NMHDR** qui contient des informations sur le message de notification. Le gestionnaire ne doit retourner aucune valeur spécifique.

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
