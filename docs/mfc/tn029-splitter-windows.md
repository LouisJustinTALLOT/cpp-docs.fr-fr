---
description: 'En savoir plus sur : TN029 : fenêtres fractionnées'
title: 'TN029 : fenêtres fractionnées'
ms.date: 11/04/2016
f1_keywords:
- vc.windows.splitter
helpviewer_keywords:
- TN029
- splitter windows [MFC], about splitter windows
ms.assetid: 2c57ce99-2a3c-4eff-9cea-baccb13af075
ms.openlocfilehash: e1079adf403b64aa47f5aae00aa32f7da702ddcf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215636"
---
# <a name="tn029-splitter-windows"></a>TN029 : fenêtres fractionnées

Cette note décrit la [classe MFC CSplitterWnd](../mfc/reference/csplitterwnd-class.md), qui fournit des fractionnements de fenêtre et gère le redimensionnement des autres fenêtres de volet.

## <a name="splitter-styles"></a>Styles de séparateur

Un `CSplitterWnd` prend en charge deux styles différents de fractionnement des fenêtres.

Dans « séparateurs statiques », la fenêtre de fractionnement crée les volets lorsqu’elle est créée. L’ordre et le nombre de volets ne changent jamais. Les barres de fractionnement sont utilisées pour redimensionner les différents volets. Vous pouvez utiliser ce style pour afficher une classe d’affichage différente dans chaque volet. L’éditeur graphique Visual C++ et le gestionnaire de fichiers Windows sont des exemples de programmes qui utilisent ce style de séparateur. Ce style de fenêtre fractionnée n’utilise pas de zones de fractionnement.

Dans les « fractionnements dynamiques », des volets supplémentaires sont créés et détruits à mesure que l’utilisateur fractionne et annule le fractionnement des nouveaux affichages. Ce séparateur commence par une vue unique et fournit des zones de fractionnement permettant à l’utilisateur de lancer le fractionnement. La fenêtre de fractionnement crée dynamiquement un nouvel objet de vue lorsque la vue est fractionnée dans une direction. Ce nouvel objet View représente le nouveau volet. Si la vue est fractionnée en deux directions à l’aide de l’interface clavier, la fenêtre de fractionnement crée trois nouveaux objets de vue pour les trois nouveaux volets. Lorsque le fractionnement est actif, Windows affiche la zone de fractionnement sous la forme d’une barre de fractionnement entre les volets. Windows détruit des objets de vue supplémentaires lorsque l’utilisateur supprime une division, mais la vue d’origine reste jusqu’à ce que la fenêtre de fractionnement proprement dite soit détruite. Microsoft Excel et Microsoft Word sont des exemples d’applications qui utilisent le style de fractionnement dynamique.

Lorsque vous créez un type de fenêtre fractionnée, vous devez spécifier le nombre maximal de lignes et de colonnes que le séparateur va gérer. Un séparateur statique crée des volets pour remplir toutes les lignes et les colonnes. Un séparateur dynamique crée uniquement le premier volet lorsque le `CSplitterWnd` est créé.

Le nombre maximal de volets que vous pouvez spécifier pour les séparateurs statiques est de 16 lignes par 16 colonnes. Les configurations recommandées sont les suivantes :

- 1 ligne x 2 colonnes : généralement avec des volets différents

- 2 lignes x 1 colonne : généralement avec des volets différents

- 2 lignes x 2 colonnes : généralement avec des volets similaires

Le nombre maximal de volets que vous pouvez spécifier pour les fractionnements dynamiques est de 2 lignes par 2 colonnes. Les configurations recommandées sont les suivantes :

- 1 ligne x 2 colonnes : pour les données en colonnes

- 2 lignes x 1 colonne : pour le texte ou d’autres données

- 2 lignes x 2 colonnes : pour les données de grille ou orientées table

## <a name="splitter-examples"></a>Exemples de séparateur

La plupart des exemples de programmes MFC utilisent des fenêtres fractionnées directement ou indirectement. L’exemple général MFC [VIEWEX](../overview/visual-cpp-samples.md) illustre plusieurs utilisations de séparateurs statiques, notamment comment placer un séparateur dans un séparateur.

Vous pouvez également utiliser ClassWizard pour créer une classe de fenêtre frame enfant MDI (multiple document interface) qui contient une fenêtre fractionnée. Pour plus d’informations sur les fenêtres fractionnées, consultez [plusieurs types de documents, vues et fenêtres Frame](../mfc/multiple-document-types-views-and-frame-windows.md).

## <a name="terminology-used-by-implementation"></a>Terminologie utilisée par l’implémentation

Voici une liste de termes spécifiques aux fenêtres fractionnées :

`CSplitterWnd`: Fenêtre qui fournit des contrôles de fractionnement de volet et des barres de défilement qui sont partagées entre tous les volets d’une ligne ou d’une colonne. Vous spécifiez des lignes et des colonnes avec des nombres de base zéro (le premier volet est Row = 0 et Column = 0).

Pane : fenêtre spécifique à l’application `CSplitterWnd` gérée par un. Un volet est généralement un objet dérivé de la [classe CView](../mfc/reference/cview-class.md), mais peut être n’importe quel objet [CWND](../mfc/reference/cwnd-class.md) avec l’ID de fenêtre enfant approprié.

Pour utiliser un `CWnd` objet dérivé de, transmettez la RUNTIME_CLASS de l’objet à la `CreateView` fonction comme vous le feriez si vous utilisiez une `CView` classe dérivée de. Votre classe doit utiliser DECLARE_DYNCREATE et IMPLEMENT_DYNCREATE, car l’infrastructure utilise la création dynamique au moment de l’exécution. Bien qu’il y ait beaucoup de code dans `CSplitterWnd` qui est spécifique à la `CView` classe, [CObject :: IsKindOf](../mfc/reference/cobject-class.md#iskindof) est toujours utilisé avant l’exécution de ces actions.

Barre de fractionnement : contrôle placé entre les lignes et les colonnes de volets. Il peut être utilisé pour ajuster la taille des lignes ou des colonnes de volets.

Zone de fractionnement : contrôle dans un dynamique `CSplitterWnd` que vous pouvez utiliser pour créer des lignes ou des colonnes de volets. Il se trouve en haut des barres de défilement verticales ou à gauche des barres de défilement horizontales.

Intersection de séparateur : intersection d’une barre de fractionnement verticale et d’une barre de fractionnement horizontale. Vous pouvez la faire glisser pour ajuster la taille d’une ligne et d’une colonne de volets simultanément.

## <a name="shared-scroll-bars"></a>Barres de défilement partagées

La `CSplitterWnd` classe prend également en charge les barres de défilement partagées. Ces contrôles de barre de défilement sont des enfants de `CSplitterWnd` et sont partagés avec les différents volets du séparateur.

Par exemple, dans une fenêtre de colonne à 1 ligne x 2, vous pouvez spécifier WS_VSCROLL lors de la création du `CSplitterWnd` . Windows crée un contrôle de barre de défilement spécial qui est partagé entre les deux volets.

```
[      ][      ][^]
[pane00][pane01][|]
[      ][      ][v]
```

Lorsque l’utilisateur déplace la barre de défilement, WM_VSCROLL messages sont envoyés aux deux vues. Quand l’une des vues définit la position de la barre de défilement, la barre de défilement partagée est définie.

Notez que les barres de défilement partagées sont particulièrement utiles avec des objets de vue similaires. Si vous combinez des vues de différents types dans un séparateur, vous devrez peut-être écrire du code spécial pour coordonner leurs positions de défilement. Toute `CView` classe dérivée qui utilise les `CWnd` API de barre de défilement délègue à la barre de défilement partagée, si elle existe. L' `CScrollView` implémentation est un exemple de `CView` classe qui prend en charge les barres de défilement partagées. Les classes qui ne sont pas dérivées de, les classes `CView` qui reposent sur des barres de défilement sans contrôle ou les classes qui utilisent des implémentations Windows standard (par exemple, `CEditView` ) ne fonctionnent pas avec la fonctionnalité de barre de défilement partagée de `CSplitterWnd` .

## <a name="minimum-sizes"></a>Tailles minimales

Pour chaque ligne, il y a une hauteur de ligne minimale et, pour chaque colonne, il y a une largeur de colonne minimale. Cette valeur minimale garantit qu’un volet n’est pas trop petit pour être affiché en détail.

Pour une fenêtre fractionnée statique, la hauteur de ligne minimale initiale et la largeur de colonne sont 0. Pour une fenêtre fractionnée dynamique, la hauteur de ligne minimale initiale et la largeur de colonne sont définies par le paramètre *sizeMin* de la `CSplitterWnd::Create` fonction.

Vous pouvez modifier ces tailles minimales à l’aide des fonctions [CSplitterWnd :: SetRowInfo](../mfc/reference/csplitterwnd-class.md#setrowinfo) et [CSplitterWnd :: SetColumnInfo](../mfc/reference/csplitterwnd-class.md#setcolumninfo) .

## <a name="actual-vs-ideal-sizes"></a>Tailles réelles et tailles idéales

La disposition des volets dans la fenêtre fractionnée dépend de la taille du frame qui les contient. Quand un utilisateur redimensionne le frame conteneur, le `CSplitterWnd` repositionne et redimensionne les volets afin qu’ils s’adaptent aussi bien que possible.

L’utilisateur peut définir manuellement la hauteur de ligne et la largeur de colonne, ou le programme peut définir la taille idéale à l’aide de la `CSplitterWnd` classe. La taille réelle peut être inférieure ou supérieure à la taille idéale. Windows ajustera la taille réelle s’il n’y a pas assez de place pour afficher la taille idéale ou s’il y a trop d’espace vide à droite ou en bas de la fenêtre fractionnée.

## <a name="custom-controls"></a>Contrôles personnalisés

Vous pouvez remplacer de nombreuses fonctions pour fournir un comportement personnalisé et une interface personnalisée. Vous pouvez remplacer ce premier jeu pour fournir une image de remplacement pour les différents composants graphiques d’une fenêtre fractionnée.

- `virtual void OnDrawSpltter(CDC* pDC, ESplitType nType, const CRect& rect);`

- `virtual void OnInvertTracker(const CRect& rect);`

Vous appelez cette fonction pour créer un contrôle de barre de défilement partagé. Vous pouvez la remplacer pour créer des contrôles supplémentaires en regard de la barre de défilement.

- `virtual BOOL CreateScrollBarCtrl(DWORD dwStyle, UINT nID);`

Ces fonctions implémentent la logique de la fenêtre fractionnée dynamique. Vous pouvez les remplacer pour fournir une logique de séparateur plus avancée.

- `virtual void DeleteView(int row, int col);`

- `virtual BOOL SplitRow(int cyBefore);`

- `virtual BOOL SplitColumn(int cxBefore);`

- `virtual void DeleteRow(int rowDelete);`

- `virtual void DeleteColumn(int colDelete);`

## <a name="cview-functionality"></a>Fonctionnalité CView

La `CView` classe utilise les commandes de niveau supérieur suivantes pour déléguer à l' `CSplitterWnd` implémentation. Comme ces commandes sont virtuelles, l' `CView` implémentation standard ne nécessitera pas la liaison de l' `CSplitterWnd` implémentation entière. Pour les applications qui utilisent `CView` mais pas `CSplitterWnd` , l’implémentation n’est `CSplitterWnd` pas liée à l’application.

- `virtual BOOL CanActivateNext(BOOL bPrev = FALSE);`

   Vérifie si ID_NEXT_PANE ou ID_PREV_PANE est actuellement possible.

- `virtual void ActivateNext(BOOL bPrev = FALSE);`

   Exécute la commande « volet suivant » ou « volet précédent ».

- `virtual BOOL DoKeyboardSplit();`

   Exécute la commande de fractionnement du clavier, généralement « fractionnement de fenêtre ».

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
