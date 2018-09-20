---
title: 'TN061 : Messages ON_NOTIFY et WM_NOTIFY | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- ON_NOTIFY
- WM_NOTIFY
dev_langs:
- C++
helpviewer_keywords:
- ON_NOTIFY_EX message [MFC]
- TN061
- ON_NOTIFY message [MFC]
- ON_NOTIFY_EX_RANGE message [MFC]
- ON_NOTIFY_RANGE message [MFC]
- notification messages
- WM_NOTIFY message
ms.assetid: 04a96dde-7049-41df-9954-ad7bb5587caf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2395cb7b1f3d719fd64494ee9b9c7c64ba222bac
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381827"
---
# <a name="tn061-onnotify-and-wmnotify-messages"></a>TN061 : messages ON_NOTIFY et WM_NOTIFY

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note technique fournit des informations générales sur le nouveau message WM_NOTIFY et décrit la manière recommandée (et la plus courante) de gestion des messages WM_NOTIFY dans votre application MFC.

**Messages de notification dans Windows 3.x**

Dans Windows 3.x, contrôles notifier leurs parents d’événements tels que des clics de souris, change dans le contenu et de sélection et de peinture en arrière-plan en envoyant un message au parent. Simples notifications sont envoyées sous forme de messages WM_COMMAND spéciaux, avec le code de notification (par exemple, BN_CLICKED) et contrôler les ID empaqueté dans *wParam* et le handle du contrôle dans *lParam*. Notez que depuis *wParam* et *lParam* sont remplis, il n’existe aucun moyen de passer des données supplémentaires, ces messages peuvent être uniquement une notification simple. Par exemple, dans la notification BN_CLICKED, il est impossible d’envoyer des informations relatives à l’emplacement du curseur de la souris lorsque l’utilisateur a cliqué sur le bouton.

Lorsque les contrôles dans Windows 3.x devons envoient un message de notification qui inclut des données supplémentaires, ils utilisent différents messages spéciaux, y compris WM_CTLCOLOR, WM_VSCROLL, messages WM_HSCROLL, WM_DRAWITEM, WM_MEASUREITEM, WM_COMPAREITEM, WM_DELETEITEM, WM_ CHARTOITEM, WM_VKEYTOITEM et ainsi de suite. Ces messages peuvent être reflétées au contrôle qui les a envoyés. Pour plus d’informations, consultez [TN062 : réflexion de Message pour Windows contrôles](../mfc/tn062-message-reflection-for-windows-controls.md).

**Messages de notification dans Win32**

Pour les contrôles qui existaient dans Windows 3.1, l’API Win32 utilise la plupart des messages de notification qui ont été utilisés dans Windows 3.x. Toutefois, Win32 ajoute également un nombre de contrôles sophistiqués et complexes à ceux pris en charge dans Windows 3.x. Souvent, ces contrôles doivent envoyer des données supplémentaires avec leurs messages de notification. Au lieu d’ajouter un nouveau **WM_** <strong>\*</strong> du message pour chaque nouvelle notification qui a besoin de données supplémentaires, les concepteurs de l’API Win32 choisi d’ajouter qu’un seul message, WM_NOTIFY, ce qui peut s’écouler quantité de données supplémentaires de manière standardisée.

Messages WM_NOTIFY contiennent l’ID du contrôle qui envoie le message *wParam* et un pointeur vers une structure dans *lParam*. Cette structure est soit un **NMHDR** structure ou une structure supérieure a un **NMHDR** structure en tant que son premier membre. Notez que depuis le **NMHDR** membre est d’abord, un pointeur vers cette structure peut être utilisé comme pointeur vers un **NMHDR** ou comme pointeur vers la structure supérieure en fonction de la façon dont vous effectuer un cast.

Dans la plupart des cas, le pointeur pointe vers une structure plus importante et vous devrez effectuer un cast lorsque vous l’utilisez. Dans certaines notifications uniquement, tels que les notifications courants (dont le nom commence avec **NM_**) et l’outil de Conseil du contrôle TTN_SHOW et TTN_POP les notifications, est un **NMHDR** structure réellement utilisée.

Le **NMHDR** structure ou le membre initial contient le handle et l’ID du contrôle qui envoie le message et le code de notification (par exemple, TTN_SHOW). Le format de la **NMHDR** structure est illustrée ci-dessous :

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

Pour un message TTN_SHOW, le **code** membre est défini sur TTN_SHOW.

La plupart des notifications passer un pointeur vers une plus grande structure qui contient un **NMHDR** structure en tant que son premier membre. Par exemple, considérez la structure utilisée par le message de notification du contrôle list view LVN_KEYDOWN, qui est envoyé lorsqu’une touche est enfoncée dans un contrôle list view. Le pointeur pointe vers un **LV_KEYDOWN** structure, ce qui est défini comme indiqué ci-dessous :

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

Notez que depuis le **NMHDR** membre apparaît en premier dans cette structure, le pointeur que vous êtes passé dans le message de notification peut être converti en pointeur vers un **NMHDR** ou un pointeur vers un **LV_KEYDOWN** .

**Notifications est courant de tous les nouveaux contrôles Windows**

Certaines notifications sont communes à tous les nouveaux contrôles Windows. Ces notifications passent un pointeur vers un **NMHDR** structure.

|Code de notification|Envoyé, car|
|-----------------------|------------------|
|NM_CLICK|Utilisateur a cliqué sur le bouton gauche de la souris dans le contrôle|
|NM_DBLCLK|Utilisateur double-clique avec le bouton gauche dans le contrôle|
|NM_RCLICK|Utilisateur a cliqué sur le bouton droit de la souris dans le contrôle|
|NM_RDBLCLK|Dans le contrôle bouton de double-clic droit de la souris utilisateur|
|NM_RETURN|Utilisateur a appuyé sur la touche entrée alors que le contrôle a le focus d’entrée|
|NM_SETFOCUS|Contrôle a reçu le focus d’entrée|
|NM_KILLFOCUS|Contrôle a perdu le focus d’entrée|
|NM_OUTOFMEMORY|Contrôle n’a pas pu terminer une opération, car il n’était pas suffisamment de mémoire disponible|

##  <a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a> ON_NOTIFY : Gestion des Messages WM_NOTIFY dans les Applications MFC

La fonction `CWnd::OnNotify` gère les messages de notification. Son implémentation par défaut vérifie la table des messages pour les gestionnaires de notification à appeler. En règle générale, vous ne substituez pas `OnNotify`. Au lieu de cela, vous fournissez une fonction de gestionnaire et ajoutez une entrée de table des messages pour ce gestionnaire à la table des messages de la classe de votre fenêtre propriétaire.

ClassWizard, par le biais de la feuille de propriétés ClassWizard, créez l’entrée de table des messages ON_NOTIFY et vous fournir une fonction de gestionnaire squelette. Pour plus d’informations sur l’utilisation de ClassWizard pour faciliter cette opération, consultez [mappage des Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md).

La macro de la table des messages ON_NOTIFY présente la syntaxe suivante :

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

où les paramètres sont :

*wNotifyCode*<br/>
Le code du message de notification à gérer, tels que LVN_KEYDOWN.

*ID*<br/>
L’identificateur de l’enfant du contrôle pour lequel la notification est envoyée.

*memberFxn*<br/>
La fonction membre à appeler quand cette notification est envoyée.

Votre fonction membre doit être déclarée avec le prototype suivant :

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

où les paramètres sont :

*pNotifyStruct*<br/>
Pointeur vers la structure de notification, comme décrit dans la section ci-dessus.

*Résultat*<br/>
Un pointeur vers le code de résultat que vous allez définir avant de retourner.

## <a name="example"></a>Exemple

Pour spécifier que vous souhaitez que la fonction membre `OnKeydownList1` à traiter les messages LVN_KEYDOWN à partir de la `CListCtrl` dont l’ID est `IDC_LIST1`, vous utiliseriez ClassWizard pour ajouter les éléments suivants à votre table des messages :

```cpp
ON_NOTIFY(LVN_KEYDOWN, IDC_LIST1, OnKeydownList1)
```

Dans l’exemple ci-dessus, la fonction fournie par ClassWizard est :

```cpp
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)
{
    LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR;

    // TODO: Add your control notification handler
    //       code here

    *pResult = 0;
}
```

Notez que ClassWizard fournit automatiquement un pointeur du type approprié. Vous pouvez accéder à la structure de notification à l’aide *pNMHDR* ou *pLVKeyDow*.

##  <a name="_mfcnotes_on_notify_range"></a> ON_NOTIFY_RANGE

Si vous avez besoin traiter le message WM_NOTIFY même pour un ensemble de contrôles, vous pouvez utiliser ON_NOTIFY_RANGE plutôt que ON_NOTIFY. Par exemple, peut avoir un ensemble de boutons pour lequel vous souhaitez effectuer la même action pour un certain message de notification.

Lorsque vous utilisez ON_NOTIFY_RANGE, vous spécifiez une plage contiguë d’identificateurs d’enfant pour qui gérer le message de notification en spécifiant le début et de fin des identificateurs des enfants de la plage.

ClassWizard ne gère pas ON_NOTIFY_RANGE ; pour l’utiliser, vous devez modifier votre table des messages à vous-même.

L’entrée de table des messages et le prototype de fonction pour ON_NOTIFY_RANGE sont les suivantes :

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

où les paramètres sont :

*wNotifyCode*<br/>
Le code du message de notification à gérer, tels que LVN_KEYDOWN.

*ID*<br/>
Le premier identificateur dans la plage contiguë d’identificateurs.

*idLast*<br/>
Le dernier identificateur dans la plage contiguë d’identificateurs.

*memberFxn*<br/>
La fonction membre à appeler quand cette notification est envoyée.

Votre fonction membre doit être déclarée avec le prototype suivant :

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

où les paramètres sont :

*ID*<br/>
L’identificateur de l’enfant du contrôle qui a envoyé la notification.

*pNotifyStruct*<br/>
Pointeur vers la structure de notification, comme décrit ci-dessus.

*Résultat*<br/>
Un pointeur vers le code de résultat que vous allez définir avant de retourner.

##  <a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a> ON_NOTIFY_EX, ON_NOTIFY_EX_RANGE

Si vous souhaitez que plusieurs objets dans la routage pour gérer un message de notification, vous pouvez utiliser ON_NOTIFY_EX (ou ON_NOTIFY_EX_RANGE) au lieu de ON_NOTIFY (ou ON_NOTIFY_RANGE). La seule différence entre la **EX** version et la version standard est que la fonction membre est appelée pour la **EX** version retourne un **BOOL** indiquant ou non traitement des messages doit continuer. Retour **FALSE** à partir de cette fonction vous permet de traiter le message même dans plusieurs objets.

ClassWizard ne gère pas ON_NOTIFY_EX ou ON_NOTIFY_EX_RANGE ; Si vous souhaitez utiliser une d'entre elles, vous devez modifier votre table des messages à vous-même.

L’entrée de table des messages et le prototype de fonction pour ON_NOTIFY_EX et ON_NOTIFY_EX_RANGE sont les suivantes. Les significations des paramètres sont identiques à celles non -**EX** versions.

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

Le prototype pour les deux la méthode ci-dessus est le même :

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

Dans les deux cas, *id* contient l’identificateur de l’enfant du contrôle qui a envoyé la notification.

Votre fonction doit renvoyer **TRUE** si le message de notification a été complètement géré ou **FALSE** si les autres objets dans le routage des commandes doivent avoir une chance de traiter le message.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
