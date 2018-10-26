---
title: 'TN062 : Réflexion pour les contrôles Windows du Message | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.controls.messages
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 994095042dc473fda315b6d842d9ec9355ff3671
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055396"
---
# <a name="tn062-message-reflection-for-windows-controls"></a>TN062 : réflexion de message pour les contrôles Windows

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note technique décrit la réflexion de message, une nouvelle fonctionnalité dans 4.0 de MFC. Il contient également des instructions pour la création d’un contrôle réutilisable simple qui utilise la réflexion de message.

Cette note technique ne traite pas la réflexion de message tel qu’il s’applique aux contrôles ActiveX (anciennement contrôles OLE). Consultez l’article [contrôles ActiveX : sous-classement d’un contrôle Windows](../mfc/mfc-activex-controls-subclassing-a-windows-control.md).

**Quelle est la réflexion de Message**

Les contrôles Windows envoient fréquemment des messages de notification dans leur fenêtre parente. Par exemple, de nombreux contrôles envoient un message de notification de couleur contrôle (WM_CTLCOLOR ou une de ses variantes) à leur parent pour permettre au parent de fournir un pinceau pour peindre l’arrière-plan du contrôle.

Dans Windows et MFC avant la version 4.0, la fenêtre parente, souvent une boîte de dialogue est chargée de gérer ces messages. Cela signifie que le code permettant de gérer le message doit se trouver dans la classe de la fenêtre parent et qu’il doit être dupliqué dans chaque classe qui a besoin de traiter ce message. Dans le cas ci-dessus, chaque boîte de dialogue qui souhaitait contrôles avec des arrière-plans personnalisés seriez obligé de gérer le message de notification de couleur de contrôle. Il serait beaucoup plus facile de réutiliser le code si une classe de contrôle peut être écrite qui traiterait sa propre couleur d’arrière-plan.

Dans MFC 4.0, l’ancien mécanisme fonctionne toujours, fenêtres parentes peuvent gérer les messages de notification. En outre, toutefois, MFC 4.0 facilite la réutilisation en fournissant une fonctionnalité appelée « réflexion de message » qui permet à ces messages de notification pour être gérée dans la fenêtre de contrôle enfant ou de la fenêtre parente, ou les deux. Dans l’exemple de couleur d’arrière-plan du contrôle, vous pouvez maintenant écrire une classe de contrôle qui définit sa propre couleur d’arrière-plan en gérant le message réfléchi WM_CTLCOLOR, tout cela sans s’appuyer sur le parent. (Notez que dans la mesure où la réflexion de message est implémentée par MFC, pas par Windows, la classe de fenêtre parente doit être dérivée `CWnd` pour la réflexion de message fonctionne.)

Les versions antérieures de MFC fait quelque chose de similaire à la réflexion de message en fournissant des fonctions virtuelles de certains messages, telles que les messages pour les zones de liste owner-drawn (WM_DRAWITEM et ainsi de suite). Le nouveau mécanisme de réflexion de message est généralisée et cohérente.

Réflexion de message est à compatibilité descendante avec le code écrit pour les versions de la bibliothèque MFC avant 4.0.

Si vous avez fourni un gestionnaire pour un message spécifique, ou pour une plage de messages, dans la classe de la fenêtre parente, il remplace répercutées gestionnaires de messages pour le même message fournie vous n’appelez pas la fonction de gestionnaire de classe de base dans votre propre gestionnaire. Par exemple, si vous gérez WM_CTLCOLOR dans votre classe de boîte de dialogue, votre gestion de substituer les gestionnaires de messages réfléchis.

Si, dans votre classe de fenêtre parente, vous fournissez un gestionnaire pour un message WM_NOTIFY spécifique ou un message de la plage de WM_NOTIFY, votre gestionnaire sera appelé uniquement si le contrôle enfant envoi de ces messages n’a pas un gestionnaire de messages réfléchis via `ON_NOTIFY_REFLECT()`. Si vous utilisez `ON_NOTIFY_REFLECT_EX()` dans votre table des messages, votre gestionnaire de messages peut ou peut ne pas autoriser la fenêtre parente à gérer le message. Si le gestionnaire retourne **FALSE**, le message sera géré par le parent de même, lors d’un appel retourne **TRUE** n’autorise pas le parent afin de le gérer. Notez que le message réfléchi est traité avant que le message de notification.

Lorsqu’un message WM_NOTIFY est envoyé, le contrôle est proposé à la première occasion de le gérer. Si un autre message réfléchi est envoyée, la fenêtre parente a la première occasion de le gérer et le contrôle reçoit le message réfléchi. Pour ce faire, il doit une fonction de gestionnaire et une entrée appropriée dans la table de messages de classe du contrôle.

La macro de table des messages pour les messages réfléchis est légèrement différente de celle pour les notifications régulières : il a *_REFLECT* ajouté à son nom habituel. Par exemple, pour traiter un message WM_NOTIFY dans le parent, vous utilisez la macro ON_NOTIFY dans la table des messages du parent. Pour gérer le message réfléchi dans le contrôle enfant, utilisez la macro ON_NOTIFY_REFLECT dans la table des messages du contrôle enfant. Dans certains cas, les paramètres diffèrent également. Notez que ClassWizard peut généralement ajouter les entrées de table des messages pour vous fournir des implémentations squelette de fonction avec des paramètres corrects.

Consultez [TN061 : Messages ON_NOTIFY et WM_NOTIFY](../mfc/tn061-on-notify-and-wm-notify-messages.md) pour plus d’informations sur le nouveau message WM_NOTIFY.

**Entrées de table des messages et les Prototypes de fonction de gestionnaire pour les Messages réfléchis**

Pour gérer un message de notification de contrôle réfléchi, utilisez les macros de table des messages et les prototypes de fonctions répertoriées dans le tableau ci-dessous.

ClassWizard peut généralement ajouter ces entrées de table des messages pour vous et fournir des implémentations squelette de fonction. Consultez [définition d’un gestionnaire de messages pour un Message réfléchi](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md) pour plus d’informations sur la définition de gestionnaires de messages réfléchis.

Pour convertir le nom de la macro réfléchi à partir du nom de message, vous devez ajouter *ON_* et ajouter *_REFLECT*. Par exemple, WM_CTLCOLOR devient ON_WM_CTLCOLOR_REFLECT. (Pour afficher les messages peuvent être reflétées, effectuent la conversion opposée sur les entrées de macro dans le tableau ci-dessous.)

Les trois exceptions à la règle ci-dessus sont les suivantes :

- La macro pour les notifications de WM_COMMAND est ON_CONTROL_REFLECT.

- La macro pour les réflexions WM_NOTIFY est ON_NOTIFY_REFLECT.

- La macro pour les réflexions ON_UPDATE_COMMAND_UI est ON_UPDATE_COMMAND_UI_REFLECT.

Dans chacun des cas spéciaux ci-dessus, vous devez spécifier le nom de la fonction membre de gestionnaire. Dans les autres cas, vous devez utiliser le nom standard de votre fonction de gestionnaire.

Les significations des paramètres et valeurs de retour des fonctions sont documentés sous le nom de fonction ou le nom de fonction avec *sur* ajouté. Par exemple, `CtlColor` est documenté dans `OnCtlColor`. Plusieurs gestionnaires de messages réfléchis doivent moins de paramètres que les gestionnaires similaire dans une fenêtre parente. Venez correspondent aux noms dans le tableau ci-dessous avec les noms des paramètres formels dans la documentation.

|Entrée de mappage|Prototype de fonction|
|---------------|------------------------|
|**ON_CONTROL_REFLECT (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg void** `memberFxn` **() ;**|
|**ON_NOTIFY_REFLECT (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg void** `memberFxn` **(NMHDR** <strong>\*</strong> `pNotifyStruct` **, LRESULT** <strong>\*</strong> *résultat* **) ;**|
|**ON_UPDATE_COMMAND_UI_REFLECT (** `memberFxn` **)**|**afx_msg void** `memberFxn` **(CCmdUI** <strong>\*</strong> `pCmdUI` **) ;**|
|**() ON_WM_CTLCOLOR_REFLECT**|**afx_msg HBRUSH CtlColor (CDC** <strong>\*</strong> `pDC` **, UINT** `nCtlColor` **) ;**|
|**() ON_WM_DRAWITEM_REFLECT**|**afx_msg void DrawItem (LPDRAWITEMSTRUCT** `lpDrawItemStruct` **) ;**|
|**() ON_WM_MEASUREITEM_REFLECT**|**afx_msg void MeasureItem (LPMEASUREITEMSTRUCT** `lpMeasureItemStruct` **) ;**|
|**() ON_WM_DELETEITEM_REFLECT**|**afx_msg void DeleteItem (LPDELETEITEMSTRUCT** `lpDeleteItemStruct` **) ;**|
|**() ON_WM_COMPAREITEM_REFLECT**|**int afx_msg CompareItem (LPCOMPAREITEMSTRUCT** `lpCompareItemStruct` **) ;**|
|**() ON_WM_CHARTOITEM_REFLECT**|**int afx_msg CharToItem (UINT** `nKey` **, UINT** `nIndex` **) ;**|
|**() ON_WM_VKEYTOITEM_REFLECT**|**int afx_msg VKeyToItem (UINT** `nKey` **, UINT** `nIndex` **) ;**|
|**() ON_WM_HSCROLL_REFLECT**|**afx_msg void HScroll (UINT** `nSBCode` **, UINT** `nPos` **) ;**|
|**() ON_WM_VSCROLL_REFLECT**|**afx_msg void VScroll (UINT** `nSBCode` **, UINT** `nPos` **) ;**|
|**() ON_WM_PARENTNOTIFY_REFLECT**|**afx_msg void ParentNotify (UINT** `message` **, LPARAM** `lParam` **) ;**|

Les macros ON_NOTIFY_REFLECT et ON_CONTROL_REFLECT ont des variations qui permettent de traiter un message donné plusieurs objets (par exemple, le contrôle et son parent).

|Entrée de mappage|Prototype de fonction|
|---------------|------------------------|
|**ON_NOTIFY_REFLECT_EX (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **(NMHDR** <strong>\*</strong> `pNotifyStruct` **, LRESULT** <strong>\*</strong> *résultat* **) ;**|
|**ON_CONTROL_REFLECT_EX (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **() ;**|

## <a name="handling-reflected-messages-an-example-of-a-reusable-control"></a>Gestion des Messages de réfléchi : Un exemple d’un contrôle réutilisable

Cet exemple simple crée un contrôle réutilisable appelé `CYellowEdit`. Le contrôle fonctionne comme un contrôle d’édition standard, à ceci près qu’il affiche du texte noir sur un arrière-plan jaune. Il est facile d’ajouter des fonctions membres qui permettraient le `CYellowEdit` contrôle pour afficher des couleurs différentes.

### <a name="to-try-the-example-that-creates-a-reusable-control"></a>Pour tester l’exemple qui crée un contrôle réutilisable

1. Créer une nouvelle boîte de dialogue dans une application existante. Pour plus d’informations, consultez le [éditeur de boîte de dialogue](../windows/dialog-editor.md) rubrique.

   Vous devez disposer d’une application permettant de développer le contrôle réutilisable. Si vous n’avez pas une application existante à utiliser, créez une application basée sur la boîte de dialogue à l’aide de AppWizard.

2. Avec votre projet est chargé dans Visual C++, utiliser ClassWizard pour créer une nouvelle classe appelée `CYellowEdit` selon `CEdit`.

3. Ajoutez trois variables membre à votre `CYellowEdit` classe. Les deux premières seront *COLORREF* variables devant contenir la couleur du texte et la couleur d’arrière-plan. La troisième sera un `CBrush` objet qui contiendra le pinceau pour peindre l’arrière-plan. Le `CBrush` objet vous permet de créer le pinceau d’une seule fois, simplement la référence après cela et à détruire le pinceau automatiquement lorsque le `CYellowEdit` est détruit.

4. Initialiser les variables de membre en écrivant le constructeur comme suit :

    ```cpp
    CYellowEdit::CYellowEdit()
    {
        m_clrText = RGB(0, 0, 0);
        m_clrBkgnd = RGB(255, 255, 0);
        m_brBkgnd.CreateSolidBrush(m_clrBkgnd);
    }
    ```

5. À l’aide de ClassWizard, ajoutez un gestionnaire pour le message WM_CTLCOLOR réfléchi à votre `CYellowEdit` classe. Notez que le signe égal devant le nom du message dans la liste des messages, que vous pouvez gérer indique que le message est reflété. Cette opération est décrite dans [définition d’un gestionnaire de messages pour un Message réfléchi](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).

   ClassWizard ajoute la fonction de macro et de la structure de table des messages suivante pour vous :

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

6. Remplacez le corps de la fonction avec le code suivant. Le code spécifie la couleur du texte, la couleur d’arrière-plan du texte et la couleur d’arrière-plan pour le reste du contrôle.

    ```cpp
    pDC->SetTextColor(m_clrText);   // text
    pDC->SetBkColor(m_clrBkgnd);    // text bkgnd
    return m_brBkgnd;               // ctl bkgnd
    ```

7. Créez un contrôle d’édition dans votre boîte de dialogue, puis attachez-le à une variable membre en double-cliquant sur le contrôle d’édition tout en maintenant enfoncée une touche de contrôle. Dans la boîte de dialogue Ajouter une Variable membre, terminer le nom de variable et choisissez « Contrôle » pour la catégorie, puis « CYellowEdit » pour le type de variable. N’oubliez pas de définir l’ordre de tabulation dans la boîte de dialogue. En outre, veillez à inclure le fichier d’en-tête pour le `CYellowEdit` contrôle dans le fichier d’en-tête de votre boîte de dialogue.

8. Générez et exécutez votre application. Le contrôle d’édition aura un arrière-plan jaune.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
