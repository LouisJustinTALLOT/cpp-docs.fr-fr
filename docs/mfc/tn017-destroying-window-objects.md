---
title: 'TN017 : destruction d’objets fenêtres'
ms.date: 11/04/2016
f1_keywords:
- vc.objects
helpviewer_keywords:
- destroying windows
- TN017
- PostNcDestroy method [MFC]
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
ms.openlocfilehash: 9802669468cbbba89f23b8ac127358d1fc15ec9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370423"
---
# <a name="tn017-destroying-window-objects"></a>TN017 : destruction d’objets fenêtres

Cette note décrit l’utilisation de la méthode [CWnd::PostNcDestroy.](../mfc/reference/cwnd-class.md#postncdestroy) Utilisez cette méthode si vous voulez `CWnd`faire l’allocation personnalisée d’objets dérivés. Cette note explique également pourquoi vous devez utiliser [CWnd::DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow) pour détruire un objet Windows C AU lieu de l’opérateur de **suppression.**

Si vous suivez les lignes directrices dans ce sujet, vous aurez peu de problèmes de nettoyage. Ces problèmes peuvent résulter de problèmes tels que l’oubli de supprimer `HWND`/ gratuit mémoire C, oublier de libérer des ressources système comme s, ou de libérer des objets trop de fois.

## <a name="the-problem"></a>Le problème

Chaque objet windows (objet d’une classe dérivée) `CWnd`représente `HWND`à la fois un objet C et un . Les objets CMD sont attribués dans le `HWND`tas de l’application et les ressources du système sont alloués dans les ressources du système par le gestionnaire de fenêtre. Parce qu’il existe plusieurs façons de détruire un objet de fenêtre, nous devons fournir un ensemble de règles qui empêchent les ressources du système ou les fuites de mémoire. Ces règles doivent également empêcher les objets et les poignées Windows d’être détruits plus d’une fois.

## <a name="destroying-windows"></a>Détruire Windows

Voici les deux moyens autorisés de détruire un objet Windows :

- Appel `CWnd::DestroyWindow` ou l’API `DestroyWindow`Windows .

- Suppression explicite avec l’opérateur **de suppression.**

Le premier cas est de loin le plus commun. Ce cas s’applique même `DestroyWindow` si votre code n’appelle pas directement. Lorsque l’utilisateur ferme directement une fenêtre de cadre, cette action génère le message WM_CLOSE, et la réponse par défaut à ce message est d’appeler `DestroyWindow.` Quand une fenêtre parente est détruite, Windows appelle `DestroyWindow` tous ses enfants.

Le deuxième cas, l’utilisation de l’opérateur de **suppression** sur les objets Windows, devrait être rare. Ce qui suit sont quelques cas où l’utilisation **de supprimer** est le bon choix.

## <a name="auto-cleanup-with-cwndpostncdestroy"></a>Nettoyage automatique avec CWnd::PostNcDestroy

Lorsque le système détruit une fenêtre Windows, le dernier message Windows envoyé à la fenêtre est WM_NCDESTROY. Le `CWnd` gestionnaire par défaut pour ce message est [CWnd::OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy). `OnNcDestroy`détachera l’objet `HWND` de l’objet Cmd `PostNcDestroy`et appellera la fonction virtuelle . Certaines classes remplacent cette fonction pour supprimer l’objet C.

La mise `CWnd::PostNcDestroy` en œuvre par défaut de ne fait rien, ce qui est approprié pour les objets de fenêtre qui sont alloués sur le cadre de pile ou intégrés dans d’autres objets. Ceci n’est pas approprié pour les objets de fenêtre qui sont conçus pour être alloués sur le tas sans aucun autre objet. En d’autres termes, il n’est pas approprié pour les objets de fenêtre qui ne sont pas intégrés dans d’autres objets C.

Ces classes qui sont conçues pour être allouées `PostNcDestroy` seules sur le tas remplacent la méthode pour effectuer une **suppression de ce**. Cette déclaration libérera toute mémoire associée à l’objet C. Même si `CWnd` le destructeur par défaut appelle `DestroyWindow` si *m_hWnd* n’est pas-NULL, cela ne conduit pas à une récursion infinie parce que la poignée sera détachée et NULL pendant la phase de nettoyage.

> [!NOTE]
> Le système `CWnd::PostNcDestroy` appelle habituellement après qu’il traite `HWND` le message Windows WM_NCDESTROY et l’objet de fenêtre et le Cmd ne sont plus connectés. Le système fera `CWnd::PostNcDestroy` également appel à la mise en œuvre de la plupart des [CWnd: :Créer des](../mfc/reference/cwnd-class.md#create) appels en cas de défaillance. Les règles de nettoyage automatique sont décrites plus tard dans ce sujet.

## <a name="auto-cleanup-classes"></a>Classes de nettoyage automatique

Les cours suivants ne sont pas conçus pour le nettoyage automatique. Ils sont généralement intégrés dans d’autres objets C OU sur la pile :

- Tous les contrôles`CStatic` `CEdit`Windows `CListBox`standard ( , , , et ainsi de suite).

- Toutes les fenêtres `CWnd` d’enfant dérivées directement de (par exemple, les contrôles personnalisés).

- Fenêtres Splitter`CSplitterWnd`( ).

- Barres de contrôle par `CControlBar`défaut (classes dérivées de , voir [Note technique 31](../mfc/tn031-control-bars.md) pour permettre la suppression automatique pour les objets de barre de commande).

- Dialogs`CDialog`( ) conçu pour les dialogues modaux sur le cadre de pile.

- Tous les dialogues `CFindReplaceDialog`standard sauf .

- Les dialogues par défaut créés par ClassWizard.

Les cours suivants sont conçus pour le nettoyage automatique. Ils sont généralement attribués par eux-mêmes sur le tas:

- Fenêtres à cadre principal (dérivées directement ou indirectement de `CFrameWnd`).

- Afficher les fenêtres (dérivées `CView`directement ou indirectement de ).

Si vous voulez enfreindre ces `PostNcDestroy` règles, vous devez passer outre à la méthode dans votre classe dérivée. Pour ajouter le nettoyage automatique à votre classe, appelez votre classe de base, puis **supprimez ceci.** Pour supprimer le nettoyage automatique de `CWnd::PostNcDestroy` votre classe, appelez directement au lieu de la `PostNcDestroy` méthode de votre classe de base directe.

L’utilisation la plus courante de changer le comportement de nettoyage automatique est de créer un dialogue sans mode qui peut être alloué sur le tas.

## <a name="when-to-call-delete"></a>Quand appeler supprimer

Nous vous recommandons `DestroyWindow` d’appeler pour détruire un objet Windows, `DestroyWindow` soit la méthode C OU l’API globale.

N’appelez pas `DestroyWindow` l’API mondiale pour détruire une fenêtre MDI Child. Vous devriez utiliser `CWnd::DestroyWindow` la méthode virtuelle à la place.

Pour les objets de fenêtre CMD qui n’effectuent pas de nettoyage automatique, l’utilisation de l’opérateur **de suppression** peut provoquer une fuite de mémoire lorsque vous essayez d’appeler `DestroyWindow` le `CWnd::~CWnd` destructeur si le VTBL ne pointe pas vers la classe correctement dérivée. Cela se produit parce que le système ne peut pas trouver la méthode de destruction appropriée à appeler. L’utilisation `DestroyWindow` au lieu de **supprimer** évite ces problèmes. Parce que cela peut être une erreur subtile, la compilation en mode débogé générera l’avertissement suivant si vous êtes à risque.

```
Warning: calling DestroyWindow in CWnd::~CWnd
    OnDestroy or PostNcDestroy in derived class will not be called
```

Dans le cas des objets Windows CMD qui effectuent `DestroyWindow`le nettoyage automatique, vous devez appeler . Si vous utilisez directement l’opérateur **de suppression,** l’alloueur de mémoire diagnostique MFC vous informera que vous libérez la mémoire deux fois. Les deux événements sont votre premier appel explicite et l’appel indirect `PostNcDestroy`pour supprimer **cela** dans la mise en œuvre de nettoyage automatique de .

Après `DestroyWindow` avoir fait appel à un objet de non-nettoyage automatique, l’objet CMD sera toujours là, mais *m_hWnd* sera NULL. Après `DestroyWindow` avoir fait appel à un objet de nettoyage automatique, l’objet CMD sera disparu, libéré `PostNcDestroy`par l’opérateur de suppression C ' dans la mise en œuvre de nettoyage automatique de .

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
