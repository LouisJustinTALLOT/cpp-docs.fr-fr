---
title: 'TN061 : messages ON_NOTIFY et WM_NOTIFY'
ms.date: 06/28/2018
helpviewer_keywords:
- ON_NOTIFY_EX message [MFC]
- TN061
- ON_NOTIFY message [MFC]
- ON_NOTIFY_EX_RANGE message [MFC]
- ON_NOTIFY_RANGE message [MFC]
- notification messages
- WM_NOTIFY message
ms.assetid: 04a96dde-7049-41df-9954-ad7bb5587caf
ms.openlocfilehash: 845558dad6b9f6e820c759cb83fce2c6cbceaa0c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366598"
---
# <a name="tn061-on_notify-and-wm_notify-messages"></a>TN061 : messages ON_NOTIFY et WM_NOTIFY

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note technique fournit des informations générales sur le nouveau message WM_NOTIFY et décrit la façon recommandée (et la plus courante) de traiter les messages WM_NOTIFY dans votre application MFC.

**Messages de notification dans Windows 3.x**

Dans Windows 3.x, les contrôles informent leurs parents d’événements tels que les clics de souris, les changements de contenu et de sélection, et contrôlent la peinture de fond en envoyant un message au parent. Des notifications simples sont envoyées sous forme de messages WM_COMMAND spéciaux, avec le code de notification (comme BN_CLICKED) et l’ID de contrôle emballé dans *wParam* et la poignée du contrôle dans *lParam*. Notez que puisque *wParam* et *lParam* sont pleins, il n’y a aucun moyen de passer des données supplémentaires - ces messages peuvent être seulement une notification simple. Par exemple, dans la notification BN_CLICKED, il n’y a aucun moyen d’envoyer des informations sur l’emplacement du curseur de souris lorsque le bouton a été cliqué.

Lorsque les commandes de Windows 3.x doivent envoyer un message de notification qui inclut des données supplémentaires, elles utilisent une variété de messages spéciaux, y compris les WM_CTLCOLOR, les WM_VSCROLL, les WM_HSCROLL, les WM_DRAWITEM, les WM_MEASUREITEM, les WM_COMPAREITEM, les WM_DELETEITEM, les WM_CHARTOITEM, les WM_VKEYTOITEM, etc. Ces messages peuvent être reflétés à nouveau au contrôle qui les a envoyés. Pour plus d’informations, voir [TN062: Message Reflection for Windows Controls](../mfc/tn062-message-reflection-for-windows-controls.md).

**Messages de notification dans Win32**

Pour les contrôles qui existaient dans Windows 3.1, l’API Win32 utilise la plupart des messages de notification qui ont été utilisés dans Windows 3.x. Cependant, Win32 ajoute également un certain nombre de contrôles sophistiqués et complexes à ceux pris en charge dans Windows 3.x. Fréquemment, ces contrôles doivent envoyer des données supplémentaires avec leurs messages de notification. Plutôt que d’ajouter un nouveau<strong>\*</strong> message **WM_** pour chaque nouvelle notification qui a besoin de données supplémentaires, les concepteurs de l’API Win32 ont choisi d’ajouter un seul message, WM_NOTIFY, qui peut passer n’importe quelle quantité de données supplémentaires d’une manière standardisée.

WM_NOTIFY messages contiennent l’ID du contrôle envoyant le message dans *wParam* et un pointeur à une structure dans *lParam*. Cette structure est soit une structure **NMHDR** ou une structure plus grande qui a une structure **NMHDR** comme son premier membre. Notez que puisque le membre **NMHDR** est le premier, un pointeur à cette structure peut être utilisé comme un pointeur à un **NMHDR** ou comme un pointeur à la structure plus grande en fonction de la façon dont vous le lancez.

Dans la plupart des cas, le pointeur indiquera une structure plus grande et vous aurez besoin de le lancer lorsque vous l’utilisez. Dans seulement quelques notifications, telles que les notifications courantes (dont les noms commencent par **NM_**) et les notifications TTN_SHOW et TTN_POP du contrôle des conseils d’outils, est une structure **NMHDR** réellement utilisée.

La structure **du NMHDR** ou le membre initial contient la poignée et l’ID du contrôle envoyant le message et le code de notification (comme TTN_SHOW). Le format de la structure **NMHDR** est indiqué ci-dessous :

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

Pour un message TTN_SHOW, le membre du **code** serait configuré pour TTN_SHOW.

La plupart des notifications passent un pointeur à une structure plus grande qui contient une structure **NMHDR** comme son premier membre. Par exemple, considérez la structure utilisée par le message de notification LVN_KEYDOWN du contrôle de la liste, qui est envoyé lorsqu’une clé est pressée dans un contrôle de vue de liste. Le pointeur indique une structure **LV_KEYDOWN,** qui est définie comme indiquée ci-dessous:

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

Notez que puisque le membre **NMHDR** est le premier dans cette structure, le pointeur que vous êtes passé dans le message de notification peut être jeté soit à un pointeur à un **NMHDR** ou un pointeur à un **LV_KEYDOWN**.

**Notifications communes à tous les nouveaux contrôles Windows**

Certaines notifications sont courantes à tous les nouveaux contrôles Windows. Ces notifications passent un pointeur à une structure **NMHDR.**

|Code de notification|Envoyé parce que|
|-----------------------|------------------|
|NM_CLICK|L’utilisateur a cliqué sur le bouton de la souris gauche dans le contrôle|
|NM_DBLCLK|Utilisateur double-clic bouton de souris gauche dans le contrôle|
|NM_RCLICK|L’utilisateur a cliqué sur le bouton de la souris droite dans le contrôle|
|NM_RDBLCLK|Utilisateur double-clic bouton de souris droite dans le contrôle|
|NM_RETURN|L’utilisateur a appuyé sur la clé ENTER tandis que le contrôle a une mise au point d’entrée|
|NM_SETFOCUS|Le contrôle a été mis en évidence|
|NM_KILLFOCUS|Le contrôle a perdu l’accent sur les intrants|
|NM_OUTOFMEMORY|Le contrôle ne pouvait pas effectuer une opération parce qu’il n’y avait pas assez de mémoire disponible|

## <a name="on_notify-handling-wm_notify-messages-in-mfc-applications"></a><a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a>ON_NOTIFY : Traiter les messages WM_NOTIFY dans les applications MFC

La `CWnd::OnNotify` fonction gère les messages de notification. Sa implémentation par défaut vérifie la carte de message pour les gestionnaires de notification à appeler. En général, vous ne `OnNotify`l’emportez pas . Au lieu de cela, vous fournissez une fonction de gestionnaire et ajoutez une entrée de carte de message pour ce gestionnaire à la carte de message de la classe de votre propriétaire.

ClassWizard, via la feuille de propriété ClassWizard, peut créer l’entrée ON_NOTIFY carte de message et vous fournir une fonction de gestionnaire squelette. Pour plus d’informations sur l’utilisation de ClassWizard pour faciliter les choses, voir [Messages de cartographie vers les fonctions](../mfc/reference/mapping-messages-to-functions.md).

La macro ON_NOTIFY carte de message a la syntaxe suivante :

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

où les paramètres sont :

*wNotifyCode (en)*<br/>
Le code pour le message de notification à traiter, comme LVN_KEYDOWN.

*id*<br/>
L’identifiant enfant du contrôle pour lequel la notification est envoyée.

*membreFxn*<br/>
La fonction membre à appeler lorsque cette notification est envoyée.

Votre fonction de membre doit être déclarée avec le prototype suivant :

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

où les paramètres sont :

*pNotifyStruct*<br/>
Un pointeur à la structure de notification, tel que décrit dans la section ci-dessus.

*Résultat*<br/>
Un pointeur sur le code de résultat que vous définirez avant votre retour.

## <a name="example"></a>Exemple

Pour spécifier que `OnKeydownList1` vous souhaitez que la `CListCtrl` fonction de `IDC_LIST1`membre gère LVN_KEYDOWN messages à partir de l’ID de qui est , vous utiliseriez ClassWizard pour ajouter ce qui suit à votre carte de message:

```cpp
ON_NOTIFY(LVN_KEYDOWN, IDC_LIST1, OnKeydownList1)
```

Dans l’exemple ci-dessus, la fonction fournie par ClassWizard est la suivante :

```cpp
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)
{
    LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR;

    // TODO: Add your control notification handler
    //       code here

    *pResult = 0;
}
```

Notez que ClassWizard fournit automatiquement un pointeur du type approprié. Vous pouvez accéder à la structure de notification par *pNMHDR* ou *pLVKeyDow*.

## <a name="on_notify_range"></a><a name="_mfcnotes_on_notify_range"></a>ON_NOTIFY_RANGE

Si vous avez besoin de traiter le même message WM_NOTIFY pour un ensemble de contrôles, vous pouvez utiliser ON_NOTIFY_RANGE plutôt que ON_NOTIFY. Par exemple, vous pouvez avoir un ensemble de boutons pour lesquels vous souhaitez effectuer la même action pour un certain message de notification.

Lorsque vous utilisez ON_NOTIFY_RANGE, vous spécifiez une gamme contigue d’identifiants pour enfants pour lesquels gérer le message de notification en spécifiant les identifiants de début et de fin de la plage.

ClassWizard ne gère pas ON_NOTIFY_RANGE; pour l’utiliser, vous devez modifier votre carte de message vous-même.

Le prototype d’entrée et de fonction de carte de message pour ON_NOTIFY_RANGE sont les suivants :

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

où les paramètres sont :

*wNotifyCode (en)*<br/>
Le code pour le message de notification à traiter, comme LVN_KEYDOWN.

*id*<br/>
Le premier identificateur dans la gamme contigue d’identifiants.

*idLast (en)*<br/>
Le dernier identificateur dans la gamme contigue d’identifiants.

*membreFxn*<br/>
La fonction membre à appeler lorsque cette notification est envoyée.

Votre fonction de membre doit être déclarée avec le prototype suivant :

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

où les paramètres sont :

*id*<br/>
L’identifiant enfant du contrôle qui a envoyé la notification.

*pNotifyStruct*<br/>
Un pointeur à la structure de notification, comme décrit ci-dessus.

*Résultat*<br/>
Un pointeur sur le code de résultat que vous définirez avant votre retour.

## <a name="on_notify_ex-on_notify_ex_range"></a><a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a>ON_NOTIFY_EX, ON_NOTIFY_EX_RANGE

Si vous voulez plus d’un objet dans le routage de notification pour gérer un message, vous pouvez utiliser ON_NOTIFY_EX (ou ON_NOTIFY_EX_RANGE) plutôt que ON_NOTIFY (ou ON_NOTIFY_RANGE). La seule différence entre la version **EX** et la version régulière est que la fonction membre demandée pour la version **EX** renvoie un **BOOL** qui indique si oui ou non le traitement des messages doit continuer. Le retour **de FALSE** de cette fonction vous permet de traiter le même message dans plus d’un objet.

ClassWizard ne gère pas ON_NOTIFY_EX ou ON_NOTIFY_EX_RANGE; si vous souhaitez utiliser l’un ou l’autre d’entre eux, vous devez modifier votre carte de message vous-même.

Le prototype d’entrée et de fonction de carte de message pour ON_NOTIFY_EX et ON_NOTIFY_EX_RANGE sont les suivants. Les significations des paramètres sont les mêmes que pour les versions non**EX.**

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

Le prototype pour les deux ci-dessus est le même:

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

Dans les deux cas, *id* détient l’identifiant de l’enfant du contrôle qui a envoyé la notification.

Votre fonction doit retourner **VRAI** si le message de notification a été entièrement manipulé ou **FALSE** si d’autres objets dans le routage de commande doivent avoir une chance de gérer le message.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
