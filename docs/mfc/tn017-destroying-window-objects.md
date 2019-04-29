---
title: "TN017 : Destruction d'objets fenêtres"
ms.date: 11/04/2016
f1_keywords:
- vc.objects
helpviewer_keywords:
- destroying windows
- TN017
- PostNcDestroy method [MFC]
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
ms.openlocfilehash: 9e52112bed0f583a3f5652f9213bd5049d543a80
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306146"
---
# <a name="tn017-destroying-window-objects"></a>TN017 : Destruction d'objets fenêtres

Cette note décrit l’utilisation de la [CWnd::PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy) (méthode). Utilisez cette méthode si vous voulez faire personnalisé d’allocation de `CWnd`-objets dérivés. Cette note explique également pourquoi vous devez utiliser [CWnd::DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow) pour détruire un objet C++ Windows au lieu du **supprimer** opérateur.

Si vous suivez les instructions de cette rubrique, vous devez le moins de problèmes de nettoyage. Ces problèmes peuvent provenir de problèmes tels que l’oubli de suppression/libération de mémoire C++, oublier de libérer des ressources système, comme `HWND`s ou la libération d’objets trop souvent.

## <a name="the-problem"></a>Le problème

Chaque objet de windows (objet d’une classe dérivée de `CWnd`) représente à la fois un objet C++ et un `HWND`. Objets C++ sont alloués dans le segment de mémoire de l’application et `HWND`s sont allouées dans les ressources système par le Gestionnaire de fenêtres. Comme il existe plusieurs façons de détruire un objet de fenêtre, nous devons fournir un ensemble de règles qui empêchent le système les fuites de ressources ou de mémoire. Ces règles doivent également empêcher les objets et les handles de Windows en cours de destruction plusieurs fois.

## <a name="destroying-windows"></a>Destruction de Windows

Voici les deux méthodes autorisées pour détruire un objet de Windows :

- Appel `CWnd::DestroyWindow` ou l’API Windows `DestroyWindow`.

- Supprimer explicitement avec le **supprimer** opérateur.

Le premier cas est de loin les plus courants. Ce cas s’applique même si votre code n’appelle pas `DestroyWindow` directement. Lorsque l’utilisateur ferme directement une fenêtre frame, cette action génère le message WM_CLOSE, et la réponse par défaut à ce message consiste à appeler `DestroyWindow.` lorsqu’une fenêtre parente est détruite, Windows appelle `DestroyWindow` pour tous ses enfants.

Le deuxième cas, l’utilisation de la **supprimer** opérateur sur des objets de Windows, doit être rare. Voici quelques cas où l’utilisation **supprimer** est le bon choix.

## <a name="auto-cleanup-with-cwndpostncdestroy"></a>Nettoyage automatique avec CWnd::PostNcDestroy

Lorsque le système supprime une fenêtre de Windows, le dernier message Windows envoyé à la fenêtre est WM_NCDESTROY. La valeur par défaut `CWnd` gestionnaire pour ce message est [CWnd::OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy). `OnNcDestroy` Détache le `HWND` à partir de C++ et appeler la fonction virtuelle `PostNcDestroy`. Certaines classes substituer cette fonction pour supprimer l’objet C++.

L’implémentation par défaut de `CWnd::PostNcDestroy` ne fait rien, ce qui convient pour les objets de fenêtre qui sont alloués sur le frame de pile ou incorporées dans d’autres objets. Cela n’est pas appropriée pour les objets de fenêtre qui sont conçus pour être alloués sur le tas sans tous les autres objets. En d’autres termes, il n’est pas approprié pour les objets de fenêtre qui ne sont pas incorporés dans d’autres objets C++.

Ces classes sont conçues pour être seul alloués sur le tas remplacent le `PostNcDestroy` méthode pour effectuer un **supprimer ce**. Cette instruction libère toute mémoire associée à l’objet C++. Même si la valeur par défaut `CWnd` appels de destructeur `DestroyWindow` si *m_hWnd* est non NULL, cela n’aboutit pas à une récurrence infinie, car le handle pendant la phase de nettoyage sera détaché et NULL.

> [!NOTE]
>  Le système appelle généralement `CWnd::PostNcDestroy` lorsqu’il a traité le message WM_NCDESTROY de Windows et le `HWND` et C++ objet window n’êtes plus connecté. Le système appelle également `CWnd::PostNcDestroy` dans l’implémentation de la plupart des [CWnd::Create](../mfc/reference/cwnd-class.md#create) appelle si l’échec se produit. Les règles de nettoyage automatique sont décrites plus loin dans cette rubrique.

## <a name="auto-cleanup-classes"></a>Classes de nettoyage automatique

Les classes suivantes ne sont pas conçus pour le nettoyage automatique. Ils sont généralement incorporés dans d’autres objets C++ ou sur la pile :

- Tous les contrôles Windows standards (`CStatic`, `CEdit`, `CListBox`, et ainsi de suite).

- Toutes les fenêtres enfants directement dérivées `CWnd` (par exemple, les contrôles personnalisés).

- Fenêtres fractionnées (`CSplitterWnd`).

- Par défaut les barres de contrôles (classes dérivées de `CControlBar`, consultez [Technical Note 31](../mfc/tn031-control-bars.md) permettant la suppression automatique des objets de barre de contrôle).

- Boîtes de dialogue (`CDialog`) conçu pour les boîtes de dialogue modales sur le frame de pile.

- La norme de toutes les boîtes de dialogue à l’exception `CFindReplaceDialog`.

- Les boîtes de dialogue par défaut créés par ClassWizard.

Les classes suivantes sont conçues pour le nettoyage automatique. En règle générale, ils sont alloués par eux-mêmes sur le tas :

- La fenêtre frame principale (dérivé directement ou indirectement de `CFrameWnd`).

- Afficher les fenêtres (dérivé directement ou indirectement de `CView`).

Si vous souhaitez arrêter ces règles, vous devez substituer la `PostNcDestroy` méthode dans votre classe dérivée. Pour ajouter le nettoyage automatique à votre classe, appeler votre classe de base, puis effectuez une **supprimer ce**. Pour supprimer le nettoyage automatique de votre classe, appelez `CWnd::PostNcDestroy` directement au lieu du `PostNcDestroy` méthode de votre classe de base directe.

L’utilisation la plus courante de la modification du comportement de nettoyage automatique consiste à créer une boîte de dialogue non modale qui peut être alloué sur le tas.

## <a name="when-to-call-delete"></a>Lorsqu’à l’appel de delete

Nous vous recommandons d’appeler `DestroyWindow` pour détruire un objet de Windows, la méthode C++ ou global `DestroyWindow` API.

N’appelez pas global `DestroyWindow` API pour détruire une fenêtre enfant MDI. Vous devez utiliser la méthode virtuelle `CWnd::DestroyWindow` à la place.

Pour des objets fenêtre C++ qui n’effectuent pas de nettoyage automatique, à l’aide du **supprimer** opérateur peut provoquer une fuite de mémoire lorsque vous essayez d’appeler `DestroyWindow` dans le `CWnd::~CWnd` destructeur si la VTBL ne pointe pas vers la classe dérivée correctement. Cela se produit car le système ne trouve pas qu'approprié détruire la méthode à appeler. À l’aide de `DestroyWindow` au lieu de **supprimer** permet d’éviter ces problèmes. Étant donné que cela peut être une erreur subtile, compilation en mode débogage génère l’avertissement suivant si vous êtes au risque.

```
Warning: calling DestroyWindow in CWnd::~CWnd
    OnDestroy or PostNcDestroy in derived class will not be called
```

Dans le cas d’objets C++ Windows qui effectuent le nettoyage automatique, vous devez appeler `DestroyWindow`. Si vous utilisez le **supprimer** opérateur directement, l’allocateur de mémoire de diagnostic MFC vous informera que vous sont libération de mémoire deux fois. Les deux occurrences sont votre premier appel explicite et l’appel indirect à **supprimer cette** dans l’implémentation de nettoyage automatique de `PostNcDestroy`.

Après avoir appelé `DestroyWindow` sur un objet non--nettoyage automatique, le C++ objet sera toujours, mais *m_hWnd* sera NULL. Après avoir appelé `DestroyWindow` sur un objet de nettoyage automatique, l’objet C++ auront disparu, libérée par l’opérateur de suppression de C++ dans l’implémentation de nettoyage automatique de `PostNcDestroy`.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
