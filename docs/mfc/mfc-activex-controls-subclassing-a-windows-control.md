---
title: 'Contrôles ActiveX MFC : Sous-classement d’un contrôle Windows | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- precreatewindow
- IsSubclassed
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95d6109bdc6ae28b748ee0be78e14ab62bba10fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355435"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>Contrôles ActiveX MFC : sous-classement d'un contrôle Windows
Cet article explique le processus de sous-classement d'un contrôle Windows commun pour créer un contrôle ActiveX. Le sous-classement d'un contrôle Windows existant est un moyen rapide de développer un contrôle ActiveX. Le nouveau contrôle a les fonctionnalités du contrôle Windows sous-classé, telles que la peinture et la réponse aux clics de souris. Exemple de contrôles ActiveX MFC [bouton](../visual-cpp-samples.md) est un exemple de sous-classement d’un contrôle Windows.  
  
 Pour sous-classer un contrôle Windows, effectuez les tâches suivantes :  
  
-   [Substituer les fonctions membres IsSubclassedControl et PreCreateWindow de COleControl](#_core_overriding_issubclassedcontrol_and_precreatewindow)  
  
-   [Modifier la fonction membre OnDraw](#_core_modifying_the_ondraw_member_function)  
  
-   [Gérer les messages de contrôle ActiveX (OCM Renvoyés) au contrôle](#_core_handling_reflected_window_messages)  
  
    > [!NOTE]
    >  Partie de ce travail est réalisée pour vous par l’Assistant contrôle ActiveX si vous sélectionnez le contrôle pour être sous-classé à l’aide de la **sélectionner une classe de fenêtre parente** liste déroulante sur le **paramètres de contrôle** page.  
  
 Consultez l'article Q243454 de la Base de connaissances pour plus d'informations sur le sous-classement d'un contrôle.  
  
##  <a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a> Remplacement de IsSubclassedControl et PreCreateWindow  
 Pour remplacer `PreCreateWindow` et `IsSubclassedControl`, ajoutez les lignes de code suivantes à la section `protected` de la déclaration de classe de contrôle :  
  
 [!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]  
  
 Dans le fichier d'implémentation du contrôle (.CPP), ajoutez les lignes de code suivantes pour implémenter les fonctions remplacées :  
  
 [!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]  
  
 Notez que, dans cet exemple, le contrôle de bouton Windows est spécifié dans `PreCreateWindow`. Toutefois, tous les contrôles Windows standard peuvent être sous-classés. Pour plus d’informations sur les contrôles Windows standard, consultez [contrôles](../mfc/controls-mfc.md).  
  
 Lors du sous-classement d’un contrôle Windows, vous pouvez souhaiter spécifier le style de fenêtre (**WS_**) ou le style de fenêtre étendue (**WS_EX_**) à utiliser lors de la création de la fenêtre du contrôle. Vous pouvez définir des valeurs pour ces paramètres dans le `PreCreateWindow` fonction membre en modifiant le **cs.style** et **cs.dwExStyle** champs de la structure. Les modifications apportées à ces champs doivent être effectuées à l'aide d'une opération `OR`, pour conserver les indicateurs de valeur par défaut définis par la classe `COleControl`. Par exemple, si le contrôle sous-classe le contrôle BUTTON et que vous voulez un contrôle qui apparaisse comme une case à cocher, insérez la ligne de code suivante dans l'implémentation de `CSampleCtrl::PreCreateWindow`, avant l'instruction RETURN :  
  
 [!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]  
  
 Cette opération ajoute le **BS_CHECKBOX** style d’indicateur, tout en laissant l’indicateur de style par défaut (**WS_CHILD**) de la classe `COleControl` intacts.  
  
##  <a name="_core_modifying_the_ondraw_member_function"></a> Modification de la fonction membre OnDraw  
 Si vous souhaitez que votre contrôle sous-classé conserve la même apparence que le contrôle Windows correspondant, la fonction membre `OnDraw` du contrôle doit contenir un seul appel à la fonction membre `DoSuperclassPaint`, comme dans l'exemple suivant :  
  
 [!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]  
  
 La fonction membre `DoSuperclassPaint`, implémentée par `COleControl`, utilise la procédure de fenêtre du contrôle Windows pour dessiner le contrôle dans le contexte matériel spécifié, au sein du rectangle englobant. Cela rend le contrôle visible même s'il n'est pas actif.  
  
> [!NOTE]
>  Le `DoSuperclassPaint` fonction membre fonctionne qu’avec les types de contrôles qui permettent un contexte de périphérique soient transmis comme le **wParam** d’un `WM_PAINT` message. Cela inclut certains contrôles Windows standards, tels que **barre de défilement** et **bouton**et tous les contrôles communs. Pour les contrôles qui ne prennent pas en charge ce comportement, vous devez fournir votre propre code pour afficher un contrôle inactif correctement.  
  
##  <a name="_core_handling_reflected_window_messages"></a> Gestion des Messages de fenêtre réfléchis  
 Les contrôles Windows envoient généralement certains messages de fenêtre à leur fenêtre parente. Certains de ces messages, tels que **WM_COMMAND**, fournir une notification d’une action de l’utilisateur. D'autres, telles que `WM_CTLCOLOR`, sont utilisés pour obtenir les informations de la fenêtre parente. Un contrôle ActiveX communique généralement avec la fenêtre parente par d'autres moyens. Les notifications sont communiquées en expédiant des événements (envoi de notifications d'événements) et des informations sur le conteneur de contrôle sont obtenues lors de l'accès aux propriétés ambiantes du conteneur. Comme ces techniques de communication existent, les conteneurs de contrôle ActiveX ne sont pas sensés traiter les messages de fenêtre envoyés par le contrôle.  
  
 Pour empêcher le conteneur de recevoir les messages de fenêtre envoyés par un contrôle Windows sous-classé, `COleControl` crée une fenêtre supplémentaire pour servir de parent du contrôle. Cette fenêtre supplémentaire, appelée "réflecteur", n'est créée que pour un contrôle ActiveX qui sous-classe un contrôle Windows et a la même taille et position que la fenêtre de contrôle. La fenêtre réflecteur intercepte certains messages de fenêtre et les envoie au contrôle. Le contrôle, dans sa procédure de fenêtre, peut ensuite traiter ces messages réfléchis en utilisant les actions appropriées pour un contrôle ActiveX (par exemple, déclencher un événement). Consultez [ID de Message de fenêtre réfléchi](../mfc/reflected-window-message-ids.md) pour une liste des fenêtres interceptés messages et leurs correspondantes messages réfléchis.  
  
 Un conteneur de contrôles ActiveX peut être conçu pour effectuer le renvoi de message lui-même, éliminant le besoin de `COleControl` de créer la fenêtre de réflection et de réduire la charge d'exécution pour un contrôle Windows sous-classé. `COleControl` détecte si le conteneur prend en charge cette fonctionnalité en recherchant une propriété ambiante MessageReflect avec une valeur de **TRUE**.  
  
 Pour traiter un message de fenêtre réfléchi, ajoutez une entrée à la table des messages de contrôle et implémentez une fonction gestionnaire. Comme les messages réfléchis ne font pas partie de l'ensemble standard de messages définis par Windows, l'Affichage de classes ne prend pas en charge l'ajout de ces gestionnaires de messages. Toutefois, il n'est pas difficile d'ajouter un gestionnaire manuellement.  
  
 Pour ajouter un gestionnaire de messages pour un message de fenêtre réfléchi manuellement, procédez comme suit :  
  
-   Dans le fichier .H de la classe de contrôle, déclarez une fonction gestionnaire. La fonction doit avoir un type de retour de **LRESULT** et deux paramètres, de types **WPARAM** et **LPARAM**, respectivement. Par exemple :  
  
     [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]  
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]  
  
-   Dans le fichier .cpp de la classe de contrôle , ajoutez une entrée `ON_MESSAGE` à la table des messages. Les paramètres de cette entrée doivent être l'identificateur de message et le nom de la fonction gestionnaire. Par exemple :  
  
     [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]  
  
-   Également dans le. Fichier CPP, implémenter la **OnOcmCommand** fonction membre pour traiter le message réfléchi. Le **wParam** et **lParam** paramètres sont les mêmes que ceux du message de fenêtre d’origine.  
  
 Pour obtenir un exemple de messages réfléchis sont traités, reportez-vous à l’exemple de contrôles ActiveX MFC [bouton](../visual-cpp-samples.md). Il montre une **OnOcmCommand** gestionnaire qui détecte le **BN_CLICKED** code notification et répond en déclenchant (envoyant) un événement Click.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

