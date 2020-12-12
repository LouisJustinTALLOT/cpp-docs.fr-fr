---
description: 'En savoir plus sur les messages suivants : TN061 : ON_NOTIFY et WM_NOTIFY'
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
ms.openlocfilehash: ecbbc03ad7328b163f89e5b1da095c8c179df097
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214752"
---
# <a name="tn061-on_notify-and-wm_notify-messages"></a>TN061 : messages ON_NOTIFY et WM_NOTIFY

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note technique fournit des informations générales sur le nouveau message WM_NOTIFY et décrit la méthode recommandée (et la plus courante) pour gérer les messages WM_NOTIFY dans votre application MFC.

**Messages de notification dans Windows 3. x**

Dans Windows 3. x, les contrôles notifient leurs parents d’événements tels que les clics de souris, les modifications de contenu et de sélection, et contrôlent le dessin de l’arrière-plan en envoyant un message au parent. Les notifications simples sont envoyées en tant que messages WM_COMMAND spéciaux, avec le code de notification (tel que BN_CLICKED) et l’ID de contrôle dans *wParam* et le handle du contrôle dans *lParam*. Notez que dans la mesure où *wParam* et *lParam* sont pleins, il n’existe aucun moyen de passer des données supplémentaires ; ces messages ne peuvent être que des notifications simples. Par exemple, dans la notification BN_CLICKED, il n’existe aucun moyen d’envoyer des informations sur l’emplacement du curseur de la souris lorsque l’utilisateur clique sur le bouton.

Lorsque les contrôles dans Windows 3. x doivent envoyer un message de notification incluant des données supplémentaires, ils utilisent différents messages à usage spécial, y compris WM_CTLCOLOR, WM_VSCROLL, WM_HSCROLL, WM_DRAWITEM, WM_MEASUREITEM, WM_COMPAREITEM, WM_DELETEITEM, WM_CHARTOITEM, WM_VKEYTOITEM, et ainsi de suite. Ces messages peuvent être reflétés dans le contrôle qui les a envoyés. Pour plus d’informations, consultez [TN062 : réflexion de message pour les contrôles Windows](../mfc/tn062-message-reflection-for-windows-controls.md).

**Messages de notification dans Win32**

Pour les contrôles qui existaient dans Windows 3,1, l’API Win32 utilise la plupart des messages de notification qui ont été utilisés dans Windows 3. x. Toutefois, Win32 ajoute également un certain nombre de contrôles sophistiqués et complexes à ceux pris en charge dans Windows 3. x. Ces contrôles doivent souvent envoyer des données supplémentaires avec leurs messages de notification. Au lieu d’ajouter un  nouveau <strong>\*</strong> message de WM_ pour chaque nouvelle notification nécessitant des données supplémentaires, les concepteurs de l’API Win32 choisissent d’ajouter un seul message, WM_NOTIFY, qui peut transmettre n’importe quelle quantité de données supplémentaires de manière standardisée.

WM_NOTIFY messages contiennent l’ID du contrôle qui envoie le message dans *wParam* et un pointeur vers une structure dans *lParam*. Cette structure est soit une structure **NMHDR** , soit une structure plus grande qui a une structure **NMHDR** comme premier membre. Notez que dans la mesure où le membre **NMHDR** est tout d’abord, un pointeur vers cette structure peut être utilisé comme pointeur vers un **NMHDR** ou comme pointeur vers la plus grande structure en fonction de la façon dont vous effectuez le cast.

Dans la plupart des cas, le pointeur pointe vers une structure plus grande et vous devez effectuer un cast de celui-ci quand vous l’utilisez. Dans quelques notifications, telles que les notifications courantes (dont les noms commencent par **NM_**) et les notifications de TTN_SHOW et de TTN_POP du contrôle d’info-bulle, est une structure **NMHDR** réellement utilisée.

La structure **NMHDR** ou le membre initial contient le handle et l’ID du contrôle qui envoie le message et le code de notification (par exemple TTN_SHOW). Le format de la structure **NMHDR** est indiqué ci-dessous :

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

Pour un message de TTN_SHOW, le membre de **code** est défini sur TTN_SHOW.

La plupart des notifications passent un pointeur vers une structure plus grande qui contient une structure **NMHDR** en tant que premier membre. Par exemple, considérez la structure utilisée par le message de notification LVN_KEYDOWN du contrôle List View, qui est envoyé lorsqu’une touche est enfoncée dans un contrôle List View. Le pointeur pointe vers une structure **LV_KEYDOWN** , qui est définie comme indiqué ci-dessous :

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

Notez que puisque le membre **NMHDR** est tout d’abord dans cette structure, le pointeur que vous transmettez dans le message de notification peut être converti en un pointeur vers un **NMHDR** ou un pointeur vers un **LV_KEYDOWN**.

**Notifications communes à tous les nouveaux contrôles Windows**

Certaines notifications sont communes à tous les nouveaux contrôles Windows. Ces notifications passent un pointeur vers une structure **NMHDR** .

|Code de notification|Envoyé car|
|-----------------------|------------------|
|NM_CLICK|L’utilisateur a cliqué avec le bouton gauche de la souris dans le contrôle|
|NM_DBLCLK|Utilisateur double-cliqué avec le bouton gauche de la souris dans le contrôle|
|NM_RCLICK|L’utilisateur a cliqué avec le bouton droit de la souris dans le contrôle|
|NM_RDBLCLK|Utilisateur double-clic avec le bouton droit de la souris dans le contrôle|
|NM_RETURN|L’utilisateur a appuyé sur la touche entrée alors que le contrôle a le focus d’entrée|
|NM_SETFOCUS|Le contrôle a reçu le focus d’entrée|
|NM_KILLFOCUS|Le contrôle a perdu le focus d’entrée|
|NM_OUTOFMEMORY|Le contrôle n’a pas pu terminer une opération, car la mémoire disponible est insuffisante|

## <a name="on_notify-handling-wm_notify-messages-in-mfc-applications"></a><a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a> ON_NOTIFY : gestion des messages WM_NOTIFY dans les applications MFC

La fonction `CWnd::OnNotify` gère les messages de notification. Son implémentation par défaut vérifie la table des messages pour les gestionnaires de notification à appeler. En général, vous ne remplacez pas `OnNotify` . Au lieu de cela, vous fournissez une fonction de gestionnaire et ajoutez une entrée de table des messages pour ce gestionnaire à la table des messages de la classe de votre fenêtre propriétaire.

ClassWizard, via la feuille de propriétés ClassWizard, peut créer l’entrée de table des messages ON_NOTIFY et vous fournir une fonction de gestionnaire squelette. Pour plus d’informations sur l’utilisation de ClassWizard pour faciliter cette opération, consultez [mappage de messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md).

La macro de table des messages ON_NOTIFY a la syntaxe suivante :

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

où les paramètres sont :

*wNotifyCode*<br/>
Code du message de notification à gérer, par exemple LVN_KEYDOWN.

*id*<br/>
Identificateur enfant du contrôle pour lequel la notification est envoyée.

*memberFxn*<br/>
Fonction membre à appeler quand cette notification est envoyée.

Votre fonction membre doit être déclarée avec le prototype suivant :

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

où les paramètres sont :

*pNotifyStruct*<br/>
Pointeur vers la structure de notification, comme décrit dans la section ci-dessus.

*result*<br/>
Pointeur vers le code de résultat que vous allez définir avant de retourner.

## <a name="example"></a>Exemple

Pour spécifier que la fonction membre `OnKeydownList1` doit gérer des messages LVN_KEYDOWN à partir du `CListCtrl` dont l’ID est `IDC_LIST1` , vous devez utiliser ClassWizard pour ajouter ce qui suit à votre table des messages :

```cpp
ON_NOTIFY(LVN_KEYDOWN, IDC_LIST1, OnKeydownList1)
```

Dans l’exemple ci-dessus, la fonction fournie par ClassWizard est la suivante :

```cpp
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)
{
    LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR;

    // TODO: Add your control notification handler
    //       code here

    *pResult = 0;
}
```

Notez que ClassWizard fournit automatiquement un pointeur du type approprié. Vous pouvez accéder à la structure de notification via *pNMHDR* ou *pLVKeyDow*.

## <a name="on_notify_range"></a><a name="_mfcnotes_on_notify_range"></a> ON_NOTIFY_RANGE

Si vous devez traiter le même WM_NOTIFY message pour un ensemble de contrôles, vous pouvez utiliser ON_NOTIFY_RANGE plutôt que ON_NOTIFY. Par exemple, vous pouvez avoir un ensemble de boutons pour lesquels vous souhaitez effectuer la même action pour un certain message de notification.

Lorsque vous utilisez ON_NOTIFY_RANGE, vous spécifiez une plage contiguë d’identificateurs enfants pour lesquels gérer le message de notification en spécifiant les identificateurs enfants de début et de fin de la plage.

ClassWizard ne gère pas ON_NOTIFY_RANGE ; pour l’utiliser, vous devez modifier votre carte des messages vous-même.

L’entrée de la table des messages et le prototype de fonction pour ON_NOTIFY_RANGE sont les suivants :

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

où les paramètres sont :

*wNotifyCode*<br/>
Code du message de notification à gérer, par exemple LVN_KEYDOWN.

*id*<br/>
Premier identificateur dans la plage contiguë d’identificateurs.

*idLast*<br/>
Dernier identificateur dans la plage contiguë d’identificateurs.

*memberFxn*<br/>
Fonction membre à appeler quand cette notification est envoyée.

Votre fonction membre doit être déclarée avec le prototype suivant :

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

où les paramètres sont :

*id*<br/>
Identificateur enfant du contrôle qui a envoyé la notification.

*pNotifyStruct*<br/>
Pointeur vers la structure de notification, comme décrit ci-dessus.

*result*<br/>
Pointeur vers le code de résultat que vous allez définir avant de retourner.

## <a name="on_notify_ex-on_notify_ex_range"></a><a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a> ON_NOTIFY_EX, ON_NOTIFY_EX_RANGE

Si vous souhaitez que plusieurs objets du routage de notification gèrent un message, vous pouvez utiliser ON_NOTIFY_EX (ou ON_NOTIFY_EX_RANGE) plutôt que ON_NOTIFY (ou ON_NOTIFY_RANGE). La seule différence entre la version **ex** et la version normale est que la fonction membre appelée pour la version **ex** retourne une valeur **booléenne** qui indique si le traitement des messages doit continuer ou non. Le retour de **false** à partir de cette fonction vous permet de traiter le même message dans plusieurs objets.

ClassWizard ne gère pas ON_NOTIFY_EX ou ON_NOTIFY_EX_RANGE ; Si vous souhaitez utiliser l’une d’entre elles, vous devez modifier votre table des messages vous-même.

L’entrée de la table des messages et le prototype de fonction pour ON_NOTIFY_EX et ON_NOTIFY_EX_RANGE sont les suivants. Les significations des paramètres sont les mêmes que pour les versions non-**ex** .

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

Le prototype pour les deux éléments ci-dessus est le même :

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

Dans les deux cas, l' *ID* contient l’identificateur enfant du contrôle qui a envoyé la notification.

Votre fonction doit retourner la **valeur true** si le message de notification a été entièrement géré ou **false** si d’autres objets du routage des commandes doivent avoir la possibilité de gérer le message.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
