---
title: "Contrôles ActiveX MFC : sous-classement d'un contrôle Windows"
ms.date: 09/12/2018
f1_keywords:
- precreatewindow
- IsSubclassed
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- subclassing
- DoSuperclassPaint method [MFC]
- subclassing Windows controls
- subclassing, Windows controls
- reflected messages, in ActiveX controls
- PreCreateWindow method, overriding
- MFC ActiveX controls [MFC], subclassed controls
- MFC ActiveX controls [MFC], creating
- IsSubclassed method [MFC]
ms.assetid: 3236d4de-401f-49b7-918d-c84559ecc426
ms.openlocfilehash: 354cd1cac5db775ea56cb5215a8528bdfe9ac5ab
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225005"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>Contrôles ActiveX MFC : sous-classement d'un contrôle Windows

Cet article explique le processus de sous-classement d'un contrôle Windows commun pour créer un contrôle ActiveX. Le sous-classement d'un contrôle Windows existant est un moyen rapide de développer un contrôle ActiveX. Le nouveau contrôle a les fonctionnalités du contrôle Windows sous-classé, telles que la peinture et la réponse aux clics de souris. Le [bouton](../overview/visual-cpp-samples.md) d’exemple de contrôles ActiveX MFC est un exemple de sous-classement d’un contrôle Windows.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

Pour sous-classer un contrôle Windows, effectuez les tâches suivantes :

- [Remplacez les fonctions membres IsSubclassedControl et PreCreateWindow de COleControl](#_core_overriding_issubclassedcontrol_and_precreatewindow)

- [Modifiez la fonction membre OnDraw](#_core_modifying_the_ondraw_member_function)

- [Traitez tous les messages du contrôle ActiveX (OCM) renvoyés au contrôle](#_core_handling_reflected_window_messages)

   > [!NOTE]
   > La majeure partie de ce travail est effectuée pour vous par l’Assistant contrôle ActiveX si vous sélectionnez le contrôle à sous-classé à l’aide de la liste déroulante **Sélectionner la classe de fenêtre parente** dans la page **paramètres du contrôle** .

## <a name="overriding-issubclassedcontrol-and-precreatewindow"></a><a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a>Substitution de IsSubclassedControl et de PreCreateWindow

Pour substituer `PreCreateWindow` et `IsSubclassedControl` , ajoutez les lignes de code suivantes à la **`protected`** section de la déclaration de classe du contrôle :

[!code-cpp[NVC_MFC_AxSub#1](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]

Dans le fichier d'implémentation du contrôle (.CPP), ajoutez les lignes de code suivantes pour implémenter les fonctions remplacées :

[!code-cpp[NVC_MFC_AxSub#2](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]

Notez que, dans cet exemple, le contrôle de bouton Windows est spécifié dans `PreCreateWindow`. Toutefois, tous les contrôles Windows standard peuvent être sous-classés. Pour plus d’informations sur les contrôles Windows standard, consultez [contrôles](controls-mfc.md).

Lors du sous-classement d'un contrôle Windows, vous pouvez préciser le style de fenêtre (WS_) ou le style de fenêtre étendue (WS_EX_) à utiliser lors de la création de la fenêtre du contrôle. Vous pouvez définir des valeurs pour ces paramètres dans la `PreCreateWindow` fonction membre en modifiant les `cs.style` champs de `cs.dwExStyle` structure et. Les modifications apportées à ces champs doivent être effectuées à l’aide d’une opération **ou** , afin de conserver les indicateurs par défaut définis par la classe `COleControl` . Par exemple, si le contrôle sous-classe le contrôle BUTTON et que vous voulez un contrôle qui apparaisse comme une case à cocher, insérez la ligne de code suivante dans l'implémentation de `CSampleCtrl::PreCreateWindow`, avant l'instruction RETURN :

[!code-cpp[NVC_MFC_AxSub#3](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]

Cette opération ajoute l’indicateur de style BS_CHECKBOX, tout en laissant l’indicateur de style par défaut (WS_CHILD) de la classe `COleControl` intact.

## <a name="modifying-the-ondraw-member-function"></a><a name="_core_modifying_the_ondraw_member_function"></a>Modification de la fonction membre OnDraw

Si vous souhaitez que votre contrôle sous-classé conserve la même apparence que le contrôle Windows correspondant, la fonction membre `OnDraw` du contrôle doit contenir un seul appel à la fonction membre `DoSuperclassPaint`, comme dans l'exemple suivant :

[!code-cpp[NVC_MFC_AxSub#4](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]

La fonction membre `DoSuperclassPaint`, implémentée par `COleControl`, utilise la procédure de fenêtre du contrôle Windows pour dessiner le contrôle dans le contexte matériel spécifié, au sein du rectangle englobant. Cela rend le contrôle visible même s'il n'est pas actif.

> [!NOTE]
> La `DoSuperclassPaint` fonction membre fonctionne uniquement avec ces types de contrôles qui permettent de transmettre un contexte de périphérique en tant que *wParam* d’un message de WM_PAINT. Cela inclut certains contrôles Windows standard, tels que SCROLLBAR et BUTTON, et tous les contrôles communs. Pour les contrôles qui ne prennent pas en charge ce comportement, vous devez fournir votre propre code pour afficher un contrôle inactif correctement.

## <a name="handling-reflected-window-messages"></a><a name="_core_handling_reflected_window_messages"></a>Gestion des messages de fenêtre réfléchie

Les contrôles Windows envoient généralement certains messages de fenêtre à leur fenêtre parente. Certains de ces messages, comme WM_COMMAND, notifient une action effectuée par l'utilisateur. D’autres, telles que WM_CTLCOLOR, sont utilisées pour obtenir des informations à partir de la fenêtre parente. Un contrôle ActiveX communique généralement avec la fenêtre parente par d'autres moyens. Les notifications sont communiquées en expédiant des événements (envoi de notifications d'événements) et des informations sur le conteneur de contrôle sont obtenues lors de l'accès aux propriétés ambiantes du conteneur. Comme ces techniques de communication existent, les conteneurs de contrôle ActiveX ne sont pas sensés traiter les messages de fenêtre envoyés par le contrôle.

Pour empêcher le conteneur de recevoir les messages de fenêtre envoyés par un contrôle Windows sous-classé, `COleControl` crée une fenêtre supplémentaire pour servir de parent du contrôle. Cette fenêtre supplémentaire, appelée "réflecteur", n'est créée que pour un contrôle ActiveX qui sous-classe un contrôle Windows et a la même taille et position que la fenêtre de contrôle. La fenêtre réflecteur intercepte certains messages de fenêtre et les envoie au contrôle. Le contrôle, dans sa procédure de fenêtre, peut ensuite traiter ces messages réfléchis en utilisant les actions appropriées pour un contrôle ActiveX (par exemple, déclencher un événement). Consultez la page [ID de message de fenêtre réfléchi](reflected-window-message-ids.md) pour obtenir la liste des messages Windows interceptés et leurs messages reflétés correspondants.

Un conteneur de contrôles ActiveX peut être conçu pour effectuer le renvoi de message lui-même, éliminant le besoin de `COleControl` de créer la fenêtre de réflection et de réduire la charge d'exécution pour un contrôle Windows sous-classé. `COleControl`détecte si le conteneur prend en charge cette fonctionnalité en recherchant une propriété ambiante MessageReflect avec la valeur **true**.

Pour traiter un message de fenêtre réfléchi, ajoutez une entrée à la table des messages de contrôle et implémentez une fonction gestionnaire. Comme les messages réfléchis ne font pas partie de l'ensemble standard de messages définis par Windows, l'Affichage de classes ne prend pas en charge l'ajout de ces gestionnaires de messages. Toutefois, il n'est pas difficile d'ajouter un gestionnaire manuellement.

Pour ajouter un gestionnaire de messages pour un message de fenêtre réfléchi manuellement, procédez comme suit :

- Dans le fichier .H de la classe de contrôle, déclarez une fonction gestionnaire. La fonction doit avoir un type de retour **LRESULT** et deux paramètres, avec les types **wParam** et **lParam**, respectivement. Par exemple :

   [!code-cpp[NVC_MFC_AxSub#5](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]
    [!code-cpp[NVC_MFC_AxSub#6](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]

- Dans la classe de contrôle. CPP, ajoutez une entrée ON_MESSAGE à la table des messages. Les paramètres de cette entrée doivent être l'identificateur de message et le nom de la fonction gestionnaire. Par exemple :

   [!code-cpp[NVC_MFC_AxSub#7](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]

- Également dans le. CPP, implémentez la `OnOcmCommand` fonction membre pour traiter le message réfléchi. Les paramètres *wParam* et *lParam* sont les mêmes que ceux du message de fenêtre d’origine.

Pour obtenir un exemple de traitement des messages reflétés, reportez-vous au [bouton](../overview/visual-cpp-samples.md)d’exemple contrôles ActiveX MFC. Il montre un `OnOcmCommand` gestionnaire qui détecte le BN_CLICKED code de notification et répond en déclenchant (envoyant) un `Click` événement.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)
