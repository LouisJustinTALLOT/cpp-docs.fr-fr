---
description: 'En savoir plus sur : TN062 : réflexion de message pour les contrôles Windows'
title: 'TN062 : réflexion de message pour les contrôles Windows'
ms.date: 06/28/2018
f1_keywords:
- vc.controls.messages
helpviewer_keywords:
- ON_WM_VKEYTOITEM_REFLECT macro [MFC]
- ON_WM_DRAWITEM_REFLECT macro [MFC]
- ON_WM_VSCROLL_REFLECT macro [MFC]
- ON_NOTIFY_REFLECT message [MFC]
- ON_CONTROL_REFLECT_EX macro [MFC]
- ON_UPDATE_COMMAND_UI_REFLECT macro [MFC]
- ON_NOTIFY_REFLECT_EX message [MFC]
- ON_WM_HSCROLL_REFLECT macro [MFC]
- message reflection [MFC]
- ON_WM_COMPAREITEM_REFLECT macro [MFC]
- ON_WM_MEASUREITEM_REFLECT macro [MFC]
- ON_NOTIFY message [MFC]
- WM_COMMAND [MFC]
- WM_CTLCOLOR message [MFC]
- TN062 [MFC]
- ON_WM_CHARTOITEM_REFLECT macro [MFC]
- ON_WM_CTLCOLOR_REFLECT macro [MFC]
- ON_WM_DELETEITEM_REFLECT macro [MFC]
- notification messages [MFC]
- ON_WM_PARENTNOTIFY_REFLECT macro [MFC]
- WM_NOTIFY message [MFC]
- ON_CONTROL_REFLECT macro
ms.assetid: 53efb0ba-fcda-4fa0-a3c7-14e0b78fb494
ms.openlocfilehash: 9dc106c1513032e654acfc2c4b86b8eb3b939578
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214726"
---
# <a name="tn062-message-reflection-for-windows-controls"></a>TN062 : réflexion de message pour les contrôles Windows

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note technique décrit la réflexion de message, une nouvelle fonctionnalité de MFC 4,0. Il contient également des instructions pour créer un contrôle réutilisable simple qui utilise la réflexion de message.

Cette note technique n’aborde pas la réflexion de message telle qu’elle s’applique aux contrôles ActiveX (anciennement appelés contrôles OLE). Consultez l’article [contrôles ActiveX : sous-classement d’un contrôle Windows](../mfc/mfc-activex-controls-subclassing-a-windows-control.md).

**Qu’est-ce que la réflexion de message ?**

Les contrôles Windows envoient souvent des messages de notification à leurs fenêtres parentes. Par exemple, de nombreux contrôles envoient un message de notification de couleur de contrôle (WM_CTLCOLOR ou l’une de ses variantes) à leur parent pour permettre au parent de fournir un pinceau pour peindre l’arrière-plan du contrôle.

Dans Windows et dans MFC avant la version 4,0, la fenêtre parente, souvent une boîte de dialogue, est responsable de la gestion de ces messages. Cela signifie que le code pour gérer le message doit être dans la classe de la fenêtre parente et qu’il doit être dupliqué dans chaque classe qui doit gérer ce message. Dans le cas ci-dessus, toutes les boîtes de dialogue qui souhaitaient des contrôles avec des arrière-plans personnalisés devaient gérer le message de notification de couleur de contrôle. Il serait beaucoup plus facile de réutiliser le code si une classe de contrôle pourrait être écrite pour gérer sa propre couleur d’arrière-plan.

Dans MFC 4,0, l’ancien mécanisme fonctionne toujours : les fenêtres parentes peuvent gérer les messages de notification. En outre, toutefois, MFC 4,0 facilite la réutilisation en fournissant une fonctionnalité appelée « réflexion de message » qui permet de gérer ces messages de notification dans la fenêtre de contrôle enfant ou la fenêtre parente, ou dans les deux. Dans l’exemple de couleur d’arrière-plan de contrôle, vous pouvez maintenant écrire une classe de contrôle qui définit sa propre couleur d’arrière-plan en gérant le message d’WM_CTLCOLOR réfléchi, le tout sans compter sur le parent. (Notez que dans la mesure où la réflexion de message est implémentée par MFC, et non par Windows, la classe de fenêtre parente doit être dérivée de pour que la `CWnd` réflexion de message fonctionne.)

Les versions antérieures de MFC ont été similaires à la réflexion de message en fournissant des fonctions virtuelles pour quelques messages, telles que des messages pour les zones de liste owner-drawn (WM_DRAWITEM, etc.). Le nouveau mécanisme de réflexion de message est généralisé et cohérent.

La réflexion de message est à compatibilité descendante avec le code écrit pour les versions de MFC antérieures à 4,0.

Si vous avez fourni un gestionnaire pour un message spécifique, ou pour une plage de messages dans la classe de votre fenêtre parente, il remplace les gestionnaires de messages réfléchis pour le même message, à condition que vous n’appeliez pas la fonction de gestionnaire de classe de base dans votre propre gestionnaire. Par exemple, si vous gérez WM_CTLCOLOR dans votre classe de boîte de dialogue, votre gestion remplacera tous les gestionnaires de messages réfléchis.

Si, dans la classe de fenêtre parente, vous fournissez un gestionnaire pour un message de WM_NOTIFY spécifique ou une plage de messages WM_NOTIFY, votre gestionnaire est appelé uniquement si le contrôle enfant qui envoie ces messages n’a pas de gestionnaire de messages reflétés via `ON_NOTIFY_REFLECT()` . Si vous utilisez `ON_NOTIFY_REFLECT_EX()` dans votre table des messages, votre gestionnaire de messages peut ou non autoriser la fenêtre parente à gérer le message. Si le gestionnaire retourne la **valeur false**, le message est également géré par le parent, tandis qu’un appel qui retourne la **valeur true** n’autorise pas le parent à le gérer. Notez que le message réfléchi est géré avant le message de notification.

Lors de l’envoi d’un message WM_NOTIFY, le contrôle est proposé à la première chance de le gérer. Si un autre message réfléchi est envoyé, la fenêtre parente a la première chance de la gérer et le contrôle recevra le message réfléchi. Pour ce faire, il a besoin d’une fonction de gestionnaire et d’une entrée appropriée dans la table des messages de classe du contrôle.

La macro de table des messages pour les messages réfléchis est légèrement différente de celle des notifications régulières : elle n’a *_REFLECT* ajoutée à son nom habituel. Par exemple, pour gérer un message d’WM_NOTIFY dans le parent, vous utilisez la macro ON_NOTIFY dans la table des messages du parent. Pour gérer le message réfléchi dans le contrôle enfant, utilisez la macro ON_NOTIFY_REFLECT dans la table des messages du contrôle enfant. Dans certains cas, les paramètres sont également différents. Notez que ClassWizard peut généralement ajouter les entrées de la table des messages pour vous et fournir des implémentations de fonctions squelettes avec des paramètres corrects.

Pour plus d’informations sur le nouveau message WM_NOTIFY [, consultez TN061 : ON_NOTIFY et WM_NOTIFY messages](../mfc/tn061-on-notify-and-wm-notify-messages.md) .

**Entrées de la table des messages et prototypes de fonction gestionnaire pour les messages réfléchis**

Pour gérer un message de notification de contrôle réfléchi, utilisez les macros de table des messages et les prototypes de fonction listés dans le tableau ci-dessous.

ClassWizard peut généralement ajouter ces entrées de table des messages pour vous et fournir des implémentations de fonctions squelettes. Pour plus d’informations sur la façon de définir des gestionnaires pour les messages reflétés, consultez [définition d’un gestionnaire de messages pour un message réfléchi](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md) .

Pour convertir le nom du message en nom de macro réfléchi, ajoutez *on_* et ajoutez *_REFLECT*. Par exemple, WM_CTLCOLOR devient ON_WM_CTLCOLOR_REFLECT. (Pour voir quels messages peuvent être reflétés, effectuez la conversion inverse sur les entrées de macro dans le tableau ci-dessous.)

Les trois exceptions à la règle ci-dessus sont les suivantes :

- La macro pour les notifications de WM_COMMAND est ON_CONTROL_REFLECT.

- La macro pour WM_NOTIFY réflexions est ON_NOTIFY_REFLECT.

- La macro pour ON_UPDATE_COMMAND_UI réflexions est ON_UPDATE_COMMAND_UI_REFLECT.

Dans chacun des cas spéciaux ci-dessus, vous devez spécifier le nom de la fonction membre du gestionnaire. Dans les autres cas, vous devez utiliser le nom standard de votre fonction gestionnaire.

Les significations des paramètres et des valeurs de retour des fonctions sont documentées sous le nom de la fonction ou le *nom de la fonction avec la* valeur précédée. Par exemple, `CtlColor` est documenté dans `OnCtlColor` . Plusieurs gestionnaires de messages réfléchis nécessitent moins de paramètres que les gestionnaires similaires dans une fenêtre parente. Faites simplement correspondre les noms figurant dans le tableau ci-dessous avec les noms des paramètres formels dans la documentation.

|Entrée de mappage|Prototype de fonction|
|---------------|------------------------|
|**ON_CONTROL_REFLECT (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg void** `memberFxn` **( );**|
|**ON_NOTIFY_REFLECT (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg void** `memberFxn` **(NMHDR** <strong>\*</strong> `pNotifyStruct` **, LRESULT** <strong>\*</strong> *résultat* **);**|
|**ON_UPDATE_COMMAND_UI_REFLECT (** `memberFxn` **)**|**afx_msg void** `memberFxn` **(CCmdUI** <strong>\*</strong> `pCmdUI` **);**|
|**ON_WM_CTLCOLOR_REFLECT ()**|**AFX_MSG HBRUSH CtlColor (CDC** <strong>\*</strong> `pDC` **, Uint** `nCtlColor` **);**|
|**ON_WM_DRAWITEM_REFLECT ()**|**afx_msg void DrawItem (LPDRAWITEMSTRUCT** `lpDrawItemStruct` **);**|
|**ON_WM_MEASUREITEM_REFLECT ()**|**afx_msg void MeasureItem (LPMEASUREITEMSTRUCT** `lpMeasureItemStruct` **);**|
|**ON_WM_DELETEITEM_REFLECT ()**|**afx_msg void DeleteItem (LPDELETEITEMSTRUCT** `lpDeleteItemStruct` **);**|
|**ON_WM_COMPAREITEM_REFLECT ()**|**afx_msg int CompareItem (LPCOMPAREITEMSTRUCT** `lpCompareItemStruct` **);**|
|**ON_WM_CHARTOITEM_REFLECT ()**|**afx_msg int CharToItem (uint** `nKey` **, uint** `nIndex` **);**|
|**ON_WM_VKEYTOITEM_REFLECT ()**|**afx_msg int VKeyToItem (uint** `nKey` **, uint** `nIndex` **);**|
|**ON_WM_HSCROLL_REFLECT ()**|**afx_msg void HScroll (uint** `nSBCode` **, uint** `nPos` **);**|
|**ON_WM_VSCROLL_REFLECT ()**|**afx_msg void VScroll (uint** `nSBCode` **, uint** `nPos` **);**|
|**ON_WM_PARENTNOTIFY_REFLECT ()**|**afx_msg void ParentNotify (uint** `message` **, lParam** `lParam` **);**|

Les macros ON_NOTIFY_REFLECT et ON_CONTROL_REFLECT ont des variations qui autorisent plusieurs objets (tels que le contrôle et son parent) à gérer un message donné.

|Entrée de mappage|Prototype de fonction|
|---------------|------------------------|
|**ON_NOTIFY_REFLECT_EX (** `wNotifyCode` **,** `memberFxn` **)**|**AFX_MSG bool** `memberFxn` **(NMHDR** <strong>\*</strong> `pNotifyStruct` **, LRESULT** <strong>\*</strong> *résultat* **);**|
|**ON_CONTROL_REFLECT_EX (** `wNotifyCode` **,** `memberFxn` **)**|**AFX_MSG bool** `memberFxn` **( );**|

## <a name="handling-reflected-messages-an-example-of-a-reusable-control"></a>Gestion des messages réfléchis : exemple de contrôle réutilisable

Cet exemple simple crée un contrôle réutilisable appelé `CYellowEdit` . Le contrôle fonctionne de la même manière qu’un contrôle d’édition normal, à ceci près qu’il affiche du texte noir sur un arrière-plan jaune. Il est facile d’ajouter des fonctions membres qui permettent au `CYellowEdit` contrôle d’afficher des couleurs différentes.

### <a name="to-try-the-example-that-creates-a-reusable-control"></a>Pour essayer l’exemple qui crée un contrôle réutilisable

1. Créer une boîte de dialogue dans une application existante. Pour plus d’informations, consultez la rubrique de l' [éditeur de boîtes de dialogue](../windows/dialog-editor.md) .

   Vous devez disposer d’une application dans laquelle développer le contrôle réutilisable. Si vous n’avez pas d’application existante à utiliser, créez une application basée sur des boîtes de dialogue à l’aide de AppWizard.

2. Une fois votre projet chargé dans Visual C++, utilisez ClassWizard pour créer une nouvelle classe appelée `CYellowEdit` en fonction de `CEdit` .

3. Ajoutez trois variables membres à votre `CYellowEdit` classe. Les deux premières sont des variables *COLORREF* pour contenir la couleur du texte et la couleur d’arrière-plan. Le troisième sera un `CBrush` objet qui contiendra le pinceau pour peindre l’arrière-plan. L' `CBrush` objet vous permet de créer le pinceau une seule fois, de le référencer après cela et de détruire le pinceau automatiquement lorsque le `CYellowEdit` contrôle est détruit.

4. Initialisez les variables membres en écrivant le constructeur comme suit :

    ```cpp
    CYellowEdit::CYellowEdit()
    {
        m_clrText = RGB(0, 0, 0);
        m_clrBkgnd = RGB(255, 255, 0);
        m_brBkgnd.CreateSolidBrush(m_clrBkgnd);
    }
    ```

5. À l’aide de ClassWizard, ajoutez un gestionnaire pour le message WM_CTLCOLOR réfléchi à votre `CYellowEdit` classe. Notez que le signe égal devant le nom de message dans la liste des messages que vous pouvez gérer indique que le message est reflété. Cela est décrit dans [définition d’un gestionnaire de messages pour un message réfléchi](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).

   ClassWizard ajoute la macro de table des messages et la fonction squelette suivantes :

    ```cpp
    ON_WM_CTLCOLOR_REFLECT()
    // Note: other code will be in between....

    HBRUSH CYellowEdit::CtlColor(CDC* pDC, UINT nCtlColor)
    {
        // TODO: Change any attributes of the DC here
        // TODO: Return a non-NULL brush if the
        //       parent's handler should not be called
        return NULL;
    }
    ```

6. Remplacez le corps de la fonction par le code suivant. Le code spécifie la couleur du texte, la couleur d’arrière-plan du texte et la couleur d’arrière-plan du reste du contrôle.

    ```cpp
    pDC->SetTextColor(m_clrText);   // text
    pDC->SetBkColor(m_clrBkgnd);    // text bkgnd
    return m_brBkgnd;               // ctl bkgnd
    ```

7. Créez un contrôle d’édition dans votre boîte de dialogue, puis attachez-le à une variable membre en double-cliquant sur le contrôle d’édition tout en maintenant la touche CTRL enfoncée. Dans la boîte de dialogue Ajouter une variable membre, terminez le nom de la variable et choisissez « contrôle » pour la catégorie, puis « CYellowEdit » pour le type de variable. N’oubliez pas de définir l’ordre de tabulation dans la boîte de dialogue. Veillez également à inclure le fichier d’en-tête pour le `CYellowEdit` contrôle dans le fichier d’en-tête de votre boîte de dialogue.

8. Créez et exécutez votre application. Le contrôle d’édition aura un arrière-plan jaune.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
