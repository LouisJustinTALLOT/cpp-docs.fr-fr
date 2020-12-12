---
description: 'En savoir plus sur : TN017 : destruction d’objets fenêtres'
title: 'TN017 : destruction d’objets fenêtres'
ms.date: 11/04/2016
f1_keywords:
- vc.objects
helpviewer_keywords:
- destroying windows
- TN017
- PostNcDestroy method [MFC]
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
ms.openlocfilehash: 86ce1255055db98a247ac8997aa7d146eb135583
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215909"
---
# <a name="tn017-destroying-window-objects"></a>TN017 : destruction d’objets fenêtres

Cette note décrit l’utilisation de la méthode [CWnd ::P ostncdestroy](../mfc/reference/cwnd-class.md#postncdestroy) . Utilisez cette méthode si vous souhaitez effectuer une allocation personnalisée d' `CWnd` objets dérivés de. Cette note explique également pourquoi vous devez utiliser [CWnd ::D estroywindow](../mfc/reference/cwnd-class.md#destroywindow) pour détruire un objet Windows C++ au lieu de l' **`delete`** opérateur.

Si vous suivez les instructions de cette rubrique, vous aurez quelques problèmes de nettoyage. Ces problèmes peuvent être liés à des problèmes tels que l’oubli de la suppression/la libération de la mémoire C++, l’oubli de libérer des ressources système telles que `HWND` des ou la libération d’objets trop souvent.

## <a name="the-problem"></a>Le problème

Chaque objet Windows (objet d’une classe dérivée de `CWnd` ) représente à la fois un objet C++ et un `HWND` . Les objets C++ sont alloués dans le tas de l’application et `HWND` sont alloués dans les ressources système par le gestionnaire de fenêtrage. Étant donné qu’il existe plusieurs façons de détruire un objet Window, nous devons fournir un ensemble de règles qui empêchent les ressources système ou les fuites de mémoire. Ces règles doivent également empêcher la destruction de plusieurs objets et Handles Windows plus d’une fois.

## <a name="destroying-windows"></a>Destruction de fenêtres

Voici les deux façons autorisées de détruire un objet Windows :

- Appel `CWnd::DestroyWindow` de ou de l’API Windows `DestroyWindow` .

- Suppression explicite avec l' **`delete`** opérateur.

Le premier cas est de loin le plus courant. Ce cas s’applique même si votre code n’appelle pas `DestroyWindow` directement. Lorsque l’utilisateur ferme directement une fenêtre frame, cette action génère le message WM_CLOSE et la réponse par défaut à ce message est appelée `DestroyWindow.` lorsqu’une fenêtre parente est détruite, Windows appelle `DestroyWindow` tous ses enfants.

Le deuxième cas, l’utilisation de l' **`delete`** opérateur sur les objets Windows, doit être rare. Voici quelques cas où l’utilisation **`delete`** de est le choix approprié.

## <a name="auto-cleanup-with-cwndpostncdestroy"></a>Nettoyage automatique avec CWnd ::P ostNcDestroy

Lorsque le système détruit une fenêtre Windows, le dernier message Windows envoyé à la fenêtre est WM_NCDESTROY. Le gestionnaire par défaut `CWnd` de ce message est [CWnd :: OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy). `OnNcDestroy` détache le `HWND` de l’objet C++ et appelle la fonction virtuelle `PostNcDestroy` . Certaines classes remplacent cette fonction pour supprimer l’objet C++.

L’implémentation par défaut de `CWnd::PostNcDestroy` ne fait rien, ce qui est approprié pour les objets de fenêtre qui sont alloués sur le frame de pile ou incorporés dans d’autres objets. Cela ne convient pas pour les objets de fenêtre qui sont conçus pour être alloués sur le tas sans autres objets. En d’autres termes, il n’est pas approprié pour les objets de fenêtre qui ne sont pas incorporés dans d’autres objets C++.

Les classes qui sont conçues pour être allouées seules sur le tas remplacent la `PostNcDestroy` méthode pour effectuer une **suppression**. Cette instruction libère toute mémoire associée à l’objet C++. Même si le destructeur par défaut `CWnd` appelle `DestroyWindow` si *m_hWnd* n’est pas null, cela n’entraîne pas de récurrence infinie car le handle sera détaché et null pendant la phase de nettoyage.

> [!NOTE]
> Le système appelle généralement `CWnd::PostNcDestroy` une fois qu’il a traité le message de WM_NCDESTROY Windows et que l' `HWND` objet de fenêtre C++ n’est plus connecté. Le système appelle également `CWnd::PostNcDestroy` dans l’implémentation de la plupart des appels de [CWnd :: Create](../mfc/reference/cwnd-class.md#create) si une défaillance se produit. Les règles de nettoyage automatique sont décrites plus loin dans cette rubrique.

## <a name="auto-cleanup-classes"></a>Nettoyage automatique des classes

Les classes suivantes ne sont pas conçues pour le nettoyage automatique. Ils sont généralement incorporés dans d’autres objets C++ ou sur la pile :

- Tous les contrôles Windows standard ( `CStatic` , `CEdit` ,, etc `CListBox` .).

- Toutes les fenêtres enfants dérivées directement de `CWnd` (par exemple, les contrôles personnalisés).

- Fenêtres fractionnées ( `CSplitterWnd` ).

- Barres de contrôles par défaut (classes dérivées de `CControlBar` , consultez la [note technique 31](../mfc/tn031-control-bars.md) pour activer la suppression automatique pour les objets de barre de contrôle).

- Boîtes de dialogue ( `CDialog` ) conçues pour les boîtes de dialogue modales sur le frame de pile.

- Toutes les boîtes de dialogue standard, à l’exception de `CFindReplaceDialog` .

- Boîtes de dialogue par défaut créées par ClassWizard.

Les classes suivantes sont conçues pour le nettoyage automatique. Elles sont généralement allouées par elles-mêmes sur le tas :

- Fenêtres Frame principales (dérivées directement ou indirectement de `CFrameWnd` ).

- Affichez les fenêtres (dérivées directement ou indirectement de `CView` ).

Si vous souhaitez arrêter ces règles, vous devez substituer la `PostNcDestroy` méthode dans votre classe dérivée. Pour ajouter le nettoyage automatique à votre classe, appelez votre classe de base, puis **supprimez**-la. Pour supprimer le nettoyage automatique de votre classe, appelez `CWnd::PostNcDestroy` directement à la place de la `PostNcDestroy` méthode de votre classe de base directe.

L’utilisation la plus courante de la modification du comportement de nettoyage automatique consiste à créer une boîte de dialogue non modale qui peut être allouée sur le tas.

## <a name="when-to-call-delete"></a>Quand appeler Delete

Nous vous recommandons d’appeler `DestroyWindow` pour détruire un objet Windows, soit la méthode C++, soit l' `DestroyWindow` API globale.

N’appelez pas l' `DestroyWindow` API globale pour détruire une fenêtre enfant MDI. Vous devez utiliser la méthode virtuelle à la `CWnd::DestroyWindow` place.

Pour les objets fenêtre C++ qui n’effectuent pas de nettoyage automatique, l’utilisation de l' **`delete`** opérateur peut provoquer une fuite de mémoire lorsque vous essayez d’appeler `DestroyWindow` dans le `CWnd::~CWnd` destructeur si le VTBL ne pointe pas vers la classe dérivée correctement. Cela est dû au fait que le système ne trouve pas la méthode Destroy appropriée à appeler. L’utilisation `DestroyWindow` de au lieu de **`delete`** évite ces problèmes. Comme il peut s’agir d’une erreur subtile, la compilation en mode débogage génère l’avertissement suivant en cas de risque.

```
Warning: calling DestroyWindow in CWnd::~CWnd
    OnDestroy or PostNcDestroy in derived class will not be called
```

Dans le cas d’objets Windows C++ qui effectuent un nettoyage automatique, vous devez appeler `DestroyWindow` . Si vous utilisez l' **`delete`** opérateur directement, l’allocateur de mémoire MFC diagnostic vous informera que vous libérez de la mémoire deux fois. Les deux occurrences sont votre premier appel explicite et l’appel indirect pour **supprimer cela** dans l’implémentation du nettoyage automatique de `PostNcDestroy` .

Après `DestroyWindow` l’appel de sur un objet qui n’est pas à nettoyage automatique, l’objet C++ est toujours en cours d’entourage, mais *m_hWnd* a la valeur null. Après l’appel `DestroyWindow` de sur un objet de nettoyage automatique, l’objet c++ est supprimé, libéré par l’opérateur c++ Delete dans l’implémentation du nettoyage automatique de `PostNcDestroy` .

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
