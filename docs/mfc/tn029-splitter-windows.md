---
title: 'TN029 : Séparateur Windows | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.windows.splitter
dev_langs:
- C++
helpviewer_keywords:
- TN029
- splitter windows [MFC], about splitter windows
ms.assetid: 2c57ce99-2a3c-4eff-9cea-baccb13af075
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25bb9fa0956c55918d997a2c697725593660be3b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020283"
---
# <a name="tn029-splitter-windows"></a>TN029 : fenêtres fractionnées
Cette note décrit la bibliothèque MFC [CSplitterWnd, classe](../mfc/reference/csplitterwnd-class.md), qui fournit la fenêtre se divise et gère le redimensionnement des autres fenêtres de volet.  
  
## <a name="splitter-styles"></a>Styles de séparateur  
 Un `CSplitterWnd` prend en charge deux styles différents de fractionnement de windows.  
  
 Dans « séparateurs statiques », la fenêtre de séparateur crée les volets lors de sa création. L’ordre et le nombre de volets ne changent jamais. Barres de fractionnement permet de redimensionner les volets différents. Vous pouvez utiliser ce style pour afficher une classe d’affichage différent dans chaque volet. L’éditeur d’images Visual C++ et le Gestionnaire de fichiers Windows sont des exemples de programmes qui utilisent ce style de séparateur. Ce style de fenêtre de séparateur n’utilise pas de zones de séparateur.  
  
 Dans les « dynamiques fenêtres fractionnées, » volets supplémentaires sont créés et détruits en tant que l’utilisateur fractionne et les fractionnements d’annulation nouveaux affichages. Ce séparateur commence par une vue unique et fournit des zones de séparateur pour l’utilisateur lancer le fractionnement. La fenêtre de séparateur crée dynamiquement un nouvel objet de vue lorsque la vue est fractionnée en une seule direction. Ce nouvel objet de vue représente le nouveau volet. Si la vue est divisée dans deux directions à l’aide de l’interface de clavier, la fenêtre de séparateur crée trois nouveaux objets de vue pour les trois volets de nouveau. Pendant que le fractionnement est actif, Windows affiche la boîte de fractionnement en tant qu’une barre de fractionnement entre les volets. Windows détruit les objets de vue lorsque l’utilisateur supprime un fractionnement, mais le reste de vue d’origine jusqu'à ce que la fenêtre de séparateur lui-même est détruit. Microsoft Excel et Microsoft Word sont des exemples d’applications qui utilisent le style de séparateur dynamique.  
  
 Lorsque vous créez un de ces types de fenêtre fractionnée, vous devez spécifier le nombre maximal de lignes et colonnes qui gère le séparateur. Un séparateur statique créera des volets pour remplir toutes les lignes et colonnes. Un séparateur dynamique créera uniquement le premier volet lorsque le `CSplitterWnd` est créé.  
  
 Le nombre maximal de volets que vous pouvez spécifier pour les fenêtres fractionnées statiques est 16 lignes par 16 colonnes. Les configurations recommandées sont :  
  
-   colonnes de la 1 ligne x 2 : généralement avec les différents volets  
  
-   colonne de 2 lignes x 1 : généralement avec les différents volets  
  
-   les colonnes 2 lignes x 2 : généralement avec les volets similaire  
  
 Le nombre maximal de volets que vous pouvez spécifier pour les fenêtres fractionnées dynamiques est de 2 lignes sur 2 colonnes. Les configurations recommandées sont :  
  
-   colonnes de la 1 ligne x 2 : pour les données en colonnes  
  
-   colonne de 2 lignes x 1 : pour les données textuelles ou autres  
  
-   les colonnes 2 lignes x 2 : grille ou une table orientée données  
  
## <a name="splitter-examples"></a>Exemples de fractionnement  
 La plupart des exemples de programmes MFC utilisent des fenêtres fractionnées directement ou indirectement. L’exemple général MFC [VIEWEX](../visual-cpp-samples.md) illustre plusieurs utilisations de fenêtres fractionnées statiques, notamment comment placer un séparateur dans un séparateur.  
  
 Vous pouvez également utiliser ClassWizard pour créer un nouveau plusieurs document interface (multidocument MDI) enfant classe de fenêtre frame qui contient une fenêtre fractionnée. Pour plus d’informations sur les fenêtres fractionnées, consultez [plusieurs Types de documents, vues et Frame Windows](../mfc/multiple-document-types-views-and-frame-windows.md).  
  
## <a name="terminology-used-by-implementation"></a>Terminologie utilisée dans l’implémentation  
 Voici une liste de termes qui sont spécifiques aux fenêtres fractionnées :  
  
 `CSplitterWnd`:  
 Une fenêtre qui fournit des contrôles de volet de fractionnement et de barres de défilement qui sont partagés entre tous les volets sur une ligne ou colonne. Vous spécifiez des lignes et colonnes avec des numéros de base zéro (le premier volet est ligne = 0 et colonne = 0).  
  
 Volet :  
 Une fenêtre spécifique à l’application qui un `CSplitterWnd` gère. Un volet est généralement un objet qui est dérivé le [classe CView](../mfc/reference/cview-class.md), mais peut être toute [CWnd](../mfc/reference/cwnd-class.md) objet ayant l’ID de fenêtre enfant approprié.  
  
 À utiliser un `CWnd`-dérivés d’objet, transmettez le RUNTIME_CLASS de l’objet à la `CreateView` fonctionne comme vous le feriez si vous utilisiez un `CView`-classe dérivée. Votre classe doit utiliser DECLARE_DYNCREATE et IMPLEMENT_DYNCREATE, car l’infrastructure utilise la création dynamique lors de l’exécution. Bien qu’il y a beaucoup de code dans `CSplitterWnd` qui est spécifique à la `CView` (classe), [CObject::IsKindOf](../mfc/reference/cobject-class.md#iskindof) est toujours utilisé avant que ces actions sont effectuées.  
  
 Barre de fractionnement :  
 Un contrôle qui est placé entre les lignes et colonnes de volets. Il peut servir à ajuster la taille des lignes ou colonnes de volets.  
  
 Boîte de fractionnement :  
 Un contrôle dans un dynamique `CSplitterWnd` que vous pouvez utiliser pour créer de nouvelles lignes ou colonnes de volets. Il se trouve en haut à gauche des barres de défilement horizontale ou des barres de défilement verticale.  
  
 Intersection de fractionnement :  
 L’intersection d’une barre de fractionnement verticale et une barre de fractionnement horizontale. Vous pouvez le faire glisser pour ajuster la taille d’une ligne et la colonne de volets simultanément.  
  
## <a name="shared-scroll-bars"></a>Les barres de défilement partagé  
 Le `CSplitterWnd` classe prend également en charge les barres de défilement partagé. Ces contrôles de barre de défilement sont des enfants de la `CSplitterWnd` et sont partagées avec les différents volets dans l’outil de fractionnement.  
  
 Par exemple, dans une fenêtre de la colonne 1, ligne x 2, vous pouvez spécifier WS_VSCROLL lors de la création du `CSplitterWnd`. Windows crée un contrôle de barre de défilement spécial qui est partagé entre les deux volets.  
  
```  
[      ][      ][^]  
[pane00][pane01][|]  
[      ][      ][v]  
```  
  
 Lorsque l’utilisateur déplace la barre de défilement, les messages WM_VSCROLL recevront les deux vues. Lorsque des affichages définit la position de barre de défilement, la barre de défilement partagé sera définie.  
  
 Notez que les barres de défilement partagé sont particulièrement utiles avec les objets de vue similaires. Si vous mélangez des vues de types différents dans un séparateur, vous devez écrire un code spécial pour coordonner leurs positions de défilement. N’importe quel `CView`-classe dérivée qui utilise le `CWnd` API va déléguer à la barre de défilement partagé s’il existe de barre de défilement. Le `CScrollView` implémentation est un exemple d’un `CView` classe qui prend en charge partagée des barres de défilement. Les classes qui ne sont pas dérivés de `CView`, les classes qui s’appuient sur les barres de défilement de non-control ou des classes qui utilisent des implémentations Windows standard (par exemple, `CEditView`) ne fonctionne pas avec la fonctionnalité de barre de défilement partagé de `CSplitterWnd`.  
  
## <a name="minimum-sizes"></a>Tailles minimales  
 Pour chaque ligne, il existe une hauteur de ligne minimale, et pour chaque colonne a une largeur de colonne minimale. Ce minimum garantit qu’un volet n’est pas trop petit pour être représentée en détail terminée.  
  
 Pour une fenêtre fractionnée statique, la largeur de colonnes et la hauteur initiale de ligne minimale est 0. Pour une fenêtre fractionnée dynamique, la largeur de colonnes et la hauteur minimale de ligne initiale sont définies le *sizeMin* paramètre de la `CSplitterWnd::Create` (fonction).  
  
 Vous pouvez modifier ces tailles minimales en utilisant le [CSplitterWnd::SetRowInfo](../mfc/reference/csplitterwnd-class.md#setrowinfo) et [CSplitterWnd::SetColumnInfo](../mfc/reference/csplitterwnd-class.md#setcolumninfo) fonctions.  
  
## <a name="actual-vs-ideal-sizes"></a>Réel vs. Tailles idéal  
 La disposition des volets dans la fenêtre de séparateur dépend de la taille de la trame qui les contient. Lorsqu’un utilisateur redimensionne le frame qui le contient, le `CSplitterWnd` repositionne et redimensionne les volets afin qu’ils occupent aussi bien que possible.  
  
 L’utilisateur peut définir manuellement la ligne de tailles de la largeur des colonnes et la hauteur, ou le programme peut définir la taille idéale en utilisant la `CSplitterWnd` classe. La taille réelle peut être inférieure ou supérieure à la solution idéale. Windows s’ajuste la taille réelle si n’est pas assez de place pour afficher la taille idéale ou s’il existe trop d’espace vide sur la droite ou le bas de la fenêtre de séparateur.  
  
## <a name="custom-controls"></a>Contrôles personnalisés  
 Vous pouvez remplacer de nombreuses fonctions pour fournir un comportement personnalisé et une interface personnalisée. Vous pouvez remplacer ce premier ensemble pour fournir d’autres images pour les différents composants de graphiques d’une fenêtre fractionnée.  
  
- `virtual void OnDrawSpltter(CDC* pDC, ESplitType nType, const CRect& rect);`  
  
- `virtual void OnInvertTracker(const CRect& rect);`  
  
Vous appelez cette fonction pour créer un contrôle de barre de défilement partagé. Vous pouvez la remplacer pour créer des contrôles supplémentaires en regard de la barre de défilement.  
  
- `virtual BOOL CreateScrollBarCtrl(DWORD dwStyle, UINT nID);`  
  
Ces fonctions implémentent la logique de la fenêtre fractionnée dynamique. Vous pouvez remplacer ces pour fournir une logique plus avancée du séparateur.  
  
- `virtual void DeleteView(int row, int col);`  
  
- `virtual BOOL SplitRow(int cyBefore);`  
  
- `virtual BOOL SplitColumn(int cxBefore);`  
  
- `virtual void DeleteRow(int rowDelete);`  
  
- `virtual void DeleteColumn(int colDelete);`  
  
## <a name="cview-functionality"></a>Fonctionnalités de CView  
 Le `CView` classe utilise les commandes de haut niveau suivantes pour déléguer à la `CSplitterWnd` implémentation. Étant donné que ces commandes sont virtuels, la norme `CView` implémentation ne nécessite pas l’intégralité de `CSplitterWnd` implémentation liée dans. Pour les applications qui utilisent `CView` mais pas `CSplitterWnd`, le `CSplitterWnd` implémentation ne sera pas liée à l’application.  
  
- `virtual BOOL CanActivateNext(BOOL bPrev = FALSE);`  

   Vérifie si ID_NEXT_PANE ou ID_PREV_PANE est actuellement possible.  
  
- `virtual void ActivateNext(BOOL bPrev = FALSE);`  

   Exécute la commande « Volet suivant » ou « Volet précédent ».  
  
- `virtual BOOL DoKeyboardSplit();`  

   Exécute le fractionnement de commande, généralement « fractionner la fenêtre » via le clavier.  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

