---
title: 'TN017 : Destruction d’objets fenêtres | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.objects
dev_langs:
- C++
helpviewer_keywords:
- destroying windows
- TN017
- PostNcDestroy method [MFC]
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c6bba255403d31e7a1fa03febb0c760d20cdc81c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384301"
---
# <a name="tn017-destroying-window-objects"></a>TN017 : destruction d’objets fenêtres
Cette note décrit l’utilisation de la [CWnd::PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy) (méthode). Utilisez cette méthode si vous voulez faire personnalisé d’allocation de `CWnd`-objets dérivés. Cette note explique également pourquoi vous devez utiliser [CWnd::DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow) pour détruire un objet Windows C++ au lieu du `delete` opérateur.  
  
 Si vous suivez les instructions de cette rubrique, vous devez quelques problèmes de nettoyage. Ces problèmes peuvent résulter de problèmes, tels que l’oubli de suppression/libérer de la mémoire de C++, oubli de libération des ressources système telles que `HWND`s ou la libération d’objets trop souvent.  
  
## <a name="the-problem"></a>Le problème  
 Chaque objet de windows (objet d’une classe dérivée de `CWnd`) représente un objet C++ et un `HWND`. Objets C++ sont allouées dans le segment de mémoire de l’application et `HWND`s sont allouées dans les ressources système par le Gestionnaire de fenêtrage. Comme il existe plusieurs façons de détruire un objet window, nous devons fournir un ensemble de règles qui empêchent le système des fuites de ressources ou de mémoire. Ces règles doivent également empêcher les objets et les handles Windows détruit plusieurs fois.  
  
## <a name="destroying-windows"></a>Détruire des fenêtres  
 Voici deux façons pour détruire un objet Windows autorisés :  
  
-   Appel de `CWnd::DestroyWindow` ou l’API Windows `DestroyWindow`.  
  
-   Supprimer explicitement avec le `delete` opérateur.  
  
 Le premier cas est de loin la plus courante. Cette condition s’applique même si votre code n’appelle pas `DestroyWindow` directement. Lorsque l’utilisateur ferme directement une fenêtre frame, cette action génère le `WM_CLOSE` message et la réponse à ce message par défaut consiste à appeler `DestroyWindow.` lorsqu’une fenêtre parente est détruite, Windows appelle `DestroyWindow` pour tous ses enfants.  
  
 Le deuxième cas, l’utilisation de la `delete` opérateur sur des objets de Windows, doit être rare. Voici quelques cas où l’utilisation `delete` est le bon choix.  
  
## <a name="auto-cleanup-with-cwndpostncdestroy"></a>Nettoyage automatique avec CWnd::PostNcDestroy  
 Lorsque le système supprime une fenêtre de Windows, le dernier message Windows envoyé à la fenêtre est `WM_NCDESTROY`. La valeur par défaut `CWnd` gestionnaire pour ce message est [CWnd::OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy). `OnNcDestroy` se détache le `HWND` à partir de C++ et appelez la fonction virtuelle `PostNcDestroy`. Certaines classes substituer cette fonction pour supprimer l’objet C++.  
  
 L’implémentation par défaut de `CWnd::PostNcDestroy` ne fait rien, ce qui convient pour les objets de fenêtre qui sont alloués sur le frame de pile ou incorporés dans d’autres objets. Cela n’est pas appropriée pour les objets de fenêtre qui sont conçues pour être alloués sur le tas sans d’autres objets. En d’autres termes, il n’est pas approprié pour les objets de fenêtre qui ne sont pas incorporés dans d’autres objets C++.  
  
 Ces classes sont conçues pour être seul alloués sur le tas remplacer le `PostNcDestroy` méthode pour effectuer un `delete this`. Cette instruction libère toute mémoire associée à l’objet C++. Même si la valeur par défaut `CWnd` appels de destructeur `DestroyWindow` si `m_hWnd` est non NULL, cela n’entraîne pas une récurrence infinie, car le handle pendant la phase de nettoyage sera détachée et NULL.  
  
> [!NOTE]
>  Le système appelle généralement `CWnd::PostNcDestroy` lorsqu’il a traité les fenêtres `WM_NCDESTROY` message et le `HWND` et l’objet fenêtre C++ n’êtes plus connecté. Le système appelle également `CWnd::PostNcDestroy` dans l’implémentation de la plupart des [CWnd::Create](../mfc/reference/cwnd-class.md#create) appelle si l’échec se produit. Les règles de nettoyage automatique sont décrits plus loin dans cette rubrique.  
  
## <a name="auto-cleanup-classes"></a>Classes de nettoyage automatique  
 Les classes suivantes ne sont pas conçus pour le nettoyage automatique. Ils sont généralement incorporés dans d’autres objets C++ ou dans la pile :  
  
-   Tous les contrôles Windows standards (`CStatic`, `CEdit`, `CListBox`, et ainsi de suite).  
  
-   Toutes les fenêtres enfants directement dérivées `CWnd` (par exemple, les contrôles personnalisés).  
  
-   Fenêtres fractionnées (`CSplitterWnd`).  
  
-   Par défaut les barres de contrôles (classes dérivées de `CControlBar`, consultez [Technical Note 31](../mfc/tn031-control-bars.md) permettant la suppression automatique des objets de barres de contrôle).  
  
-   Les boîtes de dialogue (`CDialog`) conçu pour les boîtes de dialogue modales sur le frame de pile.  
  
-   La norme de toutes les boîtes de dialogue à l’exception de `CFindReplaceDialog`.  
  
-   Les boîtes de dialogue par défaut créés par ClassWizard.  
  
 Les classes suivantes sont conçues pour le nettoyage automatique. En règle générale, ils sont alloués par eux-mêmes sur le tas :  
  
-   La fenêtre frame principale (dérivé directement ou indirectement de `CFrameWnd`).  
  
-   Afficher les fenêtres (dérivé directement ou indirectement de `CView`).  
  
 Si vous souhaitez arrêter ces règles, vous devez substituer la `PostNcDestroy` méthode dans votre classe dérivée. Pour ajouter le nettoyage automatique à votre classe, appelez votre classe de base, puis effectuez une `delete this`. Pour supprimer le nettoyage automatique de votre classe, appelez `CWnd::PostNcDestroy` directement à la place de la `PostNcDestroy` méthode de votre classe de base directe.  
  
 L’utilisation la plus courante de la modification du comportement de nettoyage automatique est à créer une boîte de dialogue non modale qui peut être alloué sur le tas.  
  
## <a name="when-to-call-delete"></a>Lorsqu’à l’appel de delete  
 Nous vous recommandons d’appeler `DestroyWindow` pour détruire un objet Windows, la méthode C++ ou global `DestroyWindow` API.  
  
 N’appelez pas global `DestroyWindow` API pour détruire une fenêtre enfant MDI. Vous devez utiliser la méthode virtuelle `CWnd::DestroyWindow` à la place.  
  
 Pour des objets fenêtre C++ qui n’effectuent pas le nettoyage automatique, à l’aide du `delete` opérateur peut entraîner une fuite de mémoire lorsque vous essayez d’appeler `DestroyWindow` dans le `CWnd::~CWnd` destructeur si la VTBL ne pointe pas vers la classe dérivée correctement. Cela se produit car le système ne trouve pas que les détruire la méthode à appeler. À l’aide de `DestroyWindow` au lieu de `delete` permet d’éviter ces problèmes. Étant donné que cela peut être une erreur subtile, la compilation en mode débogage génère l’avertissement suivant si vous sont exposés.  
  
```  
Warning: calling DestroyWindow in CWnd::~CWnd  
    OnDestroy or PostNcDestroy in derived class will not be called  
```  
  
 Dans le cas d’objets Windows C++ qui n’effectuent pas le nettoyage automatique, vous devez appeler `DestroyWindow`. Si vous utilisez la `delete` opérateur directement, l’allocateur de mémoire de diagnostic MFC vous informera que vous sont la libération de mémoire deux fois. Les deux occurrences sont votre premier appel explicite et l’appel indirect à `delete this` dans l’implémentation de nettoyage automatique de `PostNcDestroy`.  
  
 Après avoir appelé `DestroyWindow` sur un objet non-le nettoyage automatique, l’objet C++ sera toujours, mais `m_hWnd` sera NULL. Après avoir appelé `DestroyWindow` sur un objet de nettoyage automatique, l’objet C++ seront perdue, libérée par l’opérateur C++ delete dans l’implémentation de nettoyage automatique de `PostNcDestroy`.  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

